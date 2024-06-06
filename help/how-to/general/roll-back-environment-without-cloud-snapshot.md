---
title: Restauration de l’environnement sans instantané du cloud
description: Cet article présente deux solutions pour restaurer un environnement sans avoir un instantané de votre environnement sur Adobe Commerce sur l’infrastructure cloud.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: 5347e8714ef1374440f5d246100a0221e4b189fc
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Restauration de l’environnement sans instantané du cloud

Cet article présente deux solutions pour restaurer un environnement sans avoir un instantané de votre environnement sur Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Choisissez la méthode la plus adaptée à votre cas :

* Si vous disposez d’une version stable, mais pas d’instantané valide - [Scénario 1 : aucun instantané, version stable (connexion SSH disponible)](#scen2).
* Si la version est endommagée et que vous n’avez pas d’instantané valide - [Scénario 2 : aucun instantané ; version rompue (aucune connexion SSH)](#scen3).

## Scénario 1 : aucun instantané, version stable (connexion SSH disponible) {#scen2}

Cette section explique comment restaurer un environnement lorsque vous n’avez pas créé d’instantané, mais que vous pouvez accéder à l’environnement via SSH.

Les étapes sont les suivantes :

1. Désactivez la gestion de la configuration.
1. Désinstallez le logiciel Adobe Commerce.
1. Réinitialisez la branche git.

Après avoir effectué les étapes suivantes :

* votre installation Adobe Commerce retourne à son état Vanilla (base de données restaurée ; configuration de déploiement supprimée ; répertoires situés sous `var` effacé)
* votre branche git est réinitialisée à l’état souhaité dans le passé.

Lisez les étapes détaillées ci-dessous :

### Étape 0 (condition préalable requise) : supprimez config.php pour désactiver Configuration Management {#disable_config_management}

Nous devons désactiver Configuration Management afin qu’elle n’applique pas automatiquement les paramètres de configuration précédents lors du déploiement.

Pour désactiver Configuration Management, assurez-vous que la variable `/app/etc/` ne contient pas le répertoire `config.php` (pour Adobe Commerce 2.4.x) ou `config.local.php` (pour Adobe Commerce 2.1.x).

Pour supprimer le fichier de configuration, procédez comme suit :

1. [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Supprimez le fichier de configuration :
   * Pour Adobe Commerce 2.4 :

   ```php
    rm app/etc/config.php
   ```

   * Pour Adobe Commerce 2.1 :

   ```php
     rm app/etc/config.local.php
   ```

Pour en savoir plus sur Configuration Management, consultez les sections suivantes :

* [Réduction du temps d’arrêt du déploiement sur Adobe Commerce sur l’infrastructure cloud](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) dans notre base de connaissances de soutien.
* [Gestion des configurations pour les paramètres du magasin](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) dans notre documentation destinée aux développeurs.

### Étape 1 : désinstallation du logiciel Adobe Commerce avec la commande setup:uninstall {#setup-uninstall}


La désinstallation du logiciel Adobe Commerce supprime et restaure la base de données, supprime la configuration de déploiement et efface les répertoires sous `var`.

Réviser [Désinstallation du logiciel Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) dans notre documentation destinée aux développeurs.

Pour désinstaller le logiciel Adobe Commerce, procédez comme suit :

1. [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Exécuter `setup:uninstall`:

   ```php
     php bin/magento setup:uninstall
   ```

1. Confirmez la désinstallation.

Le message suivant s’affiche pour confirmer la désinstallation :

```php
[SUCCESS]: Magento uninstallation complete.
```

Cela signifie que nous avons rétabli notre installation Adobe Commerce (y compris DB) sur son état authentique (Vanilla).

### Étape 2 : réinitialisation de la branche git {#reset-git-branch}

Avec la réinitialisation de git, nous avons rétabli le code à l’état souhaité dans le passé.

1. Cloner l’environnement vers votre environnement de développement local. Vous pouvez copier la commande dans la console cloud :    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Accédez à l’historique des validations. Utilisation `--reverse` pour afficher l’historique dans l’ordre inverse, afin de faciliter les opérations :

   ```git
     git log --reverse
   ```

1. Sélectionnez le hachage de validation sur lequel vous avez été bon. Pour réinitialiser le code à son état authentique (Vanilla), recherchez la toute première validation qui a créé votre branche (environnement).    ![Sélection d’un hachage de validation dans la console Git](assets/select_commit_hash.png)
1. Appliquez la réinitialisation git stricte :

   ```git
     git reset --h <commit_hash>
   ```

1. Push changes to server :

   ```git
     git push --force <origin> <branch>
   ```

Une fois ces étapes effectuées, notre branche git est réinitialisée et l’ensemble du changement git est clair. La dernière notification push git déclenche le redéploiement pour appliquer toutes les modifications et réinstaller Adobe Commerce.

## Scénario 2 : aucun instantané ; version rompue (aucune connexion SSH) {#scen3}

Cette section explique comment restaurer un environnement lorsqu&#39;il se trouve dans un état critique : la procédure de déploiement ne peut pas réussir à créer une application opérationnelle, rendant ainsi la connexion SSH indisponible.

Dans ce scénario, vous devez d’abord restaurer l’état de fonctionnement de votre application Adobe Commerce à l’aide de la réinitialisation de git, puis désinstaller le logiciel Adobe Commerce (pour déposer et restaurer la base de données, supprimer la configuration de déploiement, etc.). Le scénario comprend les mêmes étapes que dans le scénario 1, mais l’ordre des étapes est différent et il existe une autre étape : forcer le redéploiement. Les étapes sont les suivantes :

[1. Réinitialisez la branche git.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Désactivez la gestion de la configuration.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[3. Désinstallez le logiciel Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&amp;period ; redéploiement des forces.

Une fois ces étapes effectuées, vous obtiendrez les mêmes résultats que dans le scénario 1.

### Étape 4 : forcer le redéploiement

Effectuez une validation (il peut s’agir d’une validation vide, bien que nous ne la recommandions pas) et envoyez-la au serveur pour déclencher le redéploiement :

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## En cas d’échec de l’installation:désinstallation, réinitialisez manuellement la base de données

Si l’exécution de la variable `setup:uninstall` échoue avec une erreur et ne peut pas être effectuée, la base de données peut être effacée manuellement en procédant comme suit :

1. [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Connectez-vous à la base de données MySQL :

   ```sql
   mysql -h database.internal
   ```

1. Déposez le `main` DB :

   ```sql
   drop database main;
   ```

1. Créer un champ vide `main` DB :

   ```sql
   create database main;
   ```

1. Supprimez les fichiers de configuration suivants : `config.php`, `config.php` `.bak`, `env.php`, et `env.php.bak`.

Après avoir réinitialisé la base de données, [effectuer une notification push git vers l’environnement pour déclencher le redéploiement ;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) et installez Adobe Commerce sur une base de données nouvellement créée. Ou [exécuter la commande redeploy](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Restauration d’un instantané sur le cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Création d’un instantané](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Instantanés et gestion des sauvegardes](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Gestion des branches à l’aide de la console Cloud - Afficher les journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Échec du déploiement des composants](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Gérer le projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
