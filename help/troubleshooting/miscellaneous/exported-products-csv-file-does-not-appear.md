---
title: Le fichier .csv des produits exportés n’apparaît pas
description: Cet article fournit un correctif pour le problème qui se produit lorsque vous essayez d’exporter le type d’entité souhaité vers un fichier .csv dans l’administrateur Commerce, mais que le fichier n’apparaît pas.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: b6f1222918b027eaecda42b767e6f83b2cf0f5d0
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Le fichier .csv des produits exportés n’apparaît pas

Cet article fournit une solution au problème d’affichage du fichier lors de l’exportation du type d’entité souhaité vers un fichier .csv dans Commerce Admin.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

<u>Étapes à reproduire</u>

Conditions préalables : l’option **Ajouter une clé secrète aux URL** est définie sur *Oui*. L’option est configurée dans l’administrateur Commerce sous **Magasins** > **Configuration** > **Avancé** > **Admin** > **Sécurité**.

1. Dans l’administrateur, accédez à **Système** > **Transfert de données** > **Exporter**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Sélectionner
   * **Type d’entité** : l’entité que vous souhaitez exporter
   * **Format du fichier d’exportation** : *CSV*
   * **Field Enclose** : laissez la case décochée.
1. Cliquez sur **Continuer**.
1. Le message suivant s&#39;affiche : *&quot;Message ajouté à la file d&#39;attente, attendez d&#39;obtenir votre fichier bientôt&quot;*.

<u>Résultat attendu</u>

Le fichier .csv contenant le type d’entité souhaité exporté s’affiche dans la grille en quelques minutes.

<u>Résultat réel</u>

Le fichier .csv contenant le type d’entité souhaité exporté ne s’affiche pas dans la grille dans 10 minutes ou plus.

## Cause

Problème connu avec la fonctionnalité d’exportation dans la partie application Adobe Commerce version 2.3.2.

## Solution

Il existe deux solutions possibles :

* Désactivez l’option Ajouter une clé secrète à l’URL .
* Exécutez la commande `bin/magento queue:consumers:start exportProcessor` manuellement et éventuellement configurez-la pour qu’elle soit exécutée par cron.

Voir les détails des deux options dans les paragraphes suivants.

### Désactiver l’option Ajouter une clé secrète à l’URL

1. Dans l’administrateur, accédez à **Magasins** > **Configuration** > **Avancé** > **Admin** > **Sécurité**.
1. Définissez l’option **Ajouter la clé secrète aux URL** sur *Non*
1. Cliquez sur **Enregistrer la configuration**.
1. Nettoyer le cache sous **System** > **Tools** > **Cache Management** ou en exécutant    ```bash    bin/magento cache:clean``` ou dans l’administrateur.

### Exécutez la commande d’exportation manuellement et ajoutez-la éventuellement en tant que tâche cron

Pour obtenir le fichier d&#39;export, exécutez la commande `bin/magento queue:consumers:start exportProcessor`. Après l’exécution de cette opération, le fichier doit s’afficher dans la grille.


Pour ajouter le processus en tant que tâche cron, vous devez éventuellement ajouter la variable `CRON_CONSUMERS` au fichier `.magento.env.yaml`.

#### Ajout d’un processus en tant que tâche cron (facultatif)

1. Assurez-vous que votre cron est configuré. Pour plus d’informations, voir [Configuration des tâches cron](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) .
1. Exécutez la commande suivante pour renvoyer une liste des consommateurs de la file de messages :     `./bin/magento queue:consumers:list`
1. Ajoutez le code suivant à votre fichier `.magento.env.yaml` dans le répertoire racine de l’application et incluez les consommateurs que vous souhaitez ajouter. Par exemple, voici le consommateur requis pour le traitement de l’exportation :

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Poussez ensuite ce fichier mis à jour et redéployez votre environnement. Référencez également [Ajouter des tâches cron personnalisées à votre projet](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) dans notre documentation destinée aux développeurs.

>[!NOTE]
>
>Si vous ne trouvez pas le fichier `.magento.env.yaml` pour votre environnement et que vous pensez qu’il a été supprimé, vous devez créer un `.magento.env.yaml`. Il peut être initialement vide. Vous pouvez y ajouter des informations selon vos besoins. Référencez les articles suivants : [Configuration de variables d’environnement pour le déploiement](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) et [Variables d’environnement](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) dans notre documentation destinée aux développeurs.

>[!TIP]
>
>[Les fichiers YAML](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) sont sensibles à la casse et n’autorisent pas les onglets. Veillez à utiliser une mise en retrait cohérente dans l’ensemble du fichier .magento.env.yaml , sinon votre configuration risque de ne pas fonctionner comme prévu. Les exemples de la documentation et du fichier d’exemple utilisent une mise en retrait à deux espaces. Utilisez la commande de validation de l’outil ece pour vérifier votre configuration.

>[!NOTE]
>
>Sur Adobe Commerce sur les projets d’infrastructure cloud Pro, la [fonction auto-crons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) doit être activée sur votre infrastructure cloud Adobe Commerce avant de pouvoir ajouter des tâches cron personnalisées aux environnements d’évaluation et de production à l’aide de `.magento.app.yaml`. Si cette fonction n&#39;est pas activée, [créez un ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour que la tâche soit ajoutée pour vous.
