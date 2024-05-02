---
title: Le fichier .csv des produits exportés n’apparaît pas
description: Cet article fournit un correctif pour le problème qui se produit lorsque vous essayez d’exporter des produits vers un fichier .csv dans l’administrateur Commerce, mais que le fichier n’apparaît pas.
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: 465eb89cf5c5169b0b459ab7e6bdcbd418781093
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Le fichier .csv des produits exportés n’apparaît pas

Cet article fournit un correctif pour le problème qui se produit lorsque vous essayez d’exporter des produits vers un fichier .csv dans l’administrateur Commerce, mais que le fichier n’apparaît pas.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, tous [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problème

<u>Étapes à reproduire</u>

Conditions préalables : la **Ajout d’une clé secrète aux URL** est définie sur *Oui*. L’option est configurée dans l’administrateur Commerce sous **Magasins** > **Configuration** > **Avancé** > **Administration** > **Sécurité**.

1. Dans l’administrateur, accédez à **Système** > **Transfert de données** > **Exporter**.

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. Sélectionner
   * **Type d’entité**: *Produits*
   * **Exporter le format de fichier**: *CSV*
   * **Fermeture du champ**: ne cochez pas la case.
1. Cliquez sur **Continuer**.
1. Le message suivant s&#39;affiche : *&quot;Un message est ajouté à la file d’attente, attendez pour obtenir votre fichier bientôt&quot;*.

<u>Résultat attendu</u>

Le fichier .csv contenant les produits exportés s’affiche dans la grille en quelques minutes.

<u>Résultat réel</u>

Le fichier .csv contenant les produits exportés ne s’affiche pas dans la grille dans 10 minutes ou plus.

## Cause

Problème connu avec la fonctionnalité d’exportation dans la partie application Adobe Commerce version 2.3.2.

## Solution

Il existe deux solutions possibles :

* Désactivez l’option Ajouter une clé secrète à l’URL .
* Exécutez la variable `bin/magento queue:consumers:start exportProcessor` manuellement et éventuellement configurer l’exécution par cron.

Voir les détails des deux options dans les paragraphes suivants.

### Désactiver l’option Ajouter une clé secrète à l’URL

1. Dans l’administrateur, accédez à **Magasins** > **Configuration** > **Avancé** > **Administration** > **Sécurité**.
1. Définissez la variable **Ajout d’une clé secrète aux URL** option à *Non.*
1. Cliquez sur **Enregistrer la configuration**.
1. Nettoyer le cache sous **Système** > **Outils** > **Gestion du cache** ou en exécutant    ```bash    bin/magento cache:clean``` ou dans l’administrateur.

### Exécutez la commande d’exportation manuellement et ajoutez-la éventuellement en tant que tâche cron

Pour obtenir le fichier d’exportation, exécutez le `bin/magento queue:consumers:start exportProcessor` . Après l’exécution de cette opération, le fichier doit s’afficher dans la grille.


Pour ajouter le processus en tant que tâche cron, vous devez éventuellement ajouter la fonction `CRON_CONSUMERS` à la variable `.magento.env.yaml` fichier .

#### Ajout d’un processus en tant que tâche cron (facultatif)

1. Assurez-vous que votre cron est configuré. Voir [Configuration de tâches cron](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) pour plus d’informations.
1. Exécutez la commande suivante pour renvoyer une liste des consommateurs de la file de messages :     `./bin/magento queue:consumers:list`
1. Ajoutez ce qui suit à votre `.magento.env.yaml` dans le répertoire racine de l’application et incluez les consommateurs que vous souhaitez ajouter. Par exemple, voici le consommateur requis pour le traitement de l’exportation :

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   Poussez ensuite ce fichier mis à jour et redéployez votre environnement. Référence également [Ajout de tâches cron personnalisées à votre projet](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project) dans notre documentation destinée aux développeurs.

>[!NOTE]
>
>Si vous ne trouvez pas la variable `.magento.env.yaml` pour votre environnement, et si vous pensez qu’il a été supprimé, vous devez créer un `.magento.env.yaml`. Il peut être initialement vide. Vous pouvez y ajouter des informations selon vos besoins. Reportez-vous aux articles suivants : [Configuration des variables d’environnement pour le déploiement](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) et [Variables d’environnement](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) dans notre documentation destinée aux développeurs.

>[!NOTE]
>
>Sur les projets Adobe Commerce sur l’infrastructure cloud Pro, la variable [fonction auto-crons](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab) doit être activé sur votre infrastructure cloud Adobe Commerce avant de pouvoir ajouter des tâches cron personnalisées aux environnements d’évaluation et de production à l’aide de `.magento.app.yaml`. Si cette fonction n’est pas activée, [créer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)pour que la tâche soit ajoutée.
