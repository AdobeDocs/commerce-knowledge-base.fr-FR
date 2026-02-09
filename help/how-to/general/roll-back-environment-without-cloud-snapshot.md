---
title: Restauration de l’environnement sans instantané du cloud
description: Cet article présente deux solutions pour restaurer un environnement sans avoir d’instantané de votre environnement sur Adobe Commerce sur l’infrastructure cloud.
exl-id: 834d13a7-3b1a-460c-9ed0-9d560105f436
feature: Build, Cloud, Console
source-git-commit: d7c714cf5b2f9db139440d814af26c12001bb4d9
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 0%

---

# Restauration de l’environnement sans instantané du cloud

Cet article présente deux solutions pour restaurer un environnement sans avoir d’instantané de votre environnement sur Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

Choisissez la solution la plus adaptée à votre cas :

* Si vous avez une version stable, mais pas d’instantané valide - [Scénario 1 : pas d’instantané, build stable (connexion SSH disponible)](#scen2).
* Si la version est rompue et que vous ne disposez pas d’un instantané valide - [Scénario 2 : aucun instantané ; version rompue (aucune connexion SSH)](#scen3).

## Scénario 1 : aucun instantané, build stable (connexion SSH disponible) {#scen2}

Cette section explique comment restaurer un environnement lorsque vous n’avez pas créé d’instantané, mais que vous pouvez accéder à l’environnement via SSH.

Les étapes sont les suivantes :

1. Désactivez la gestion de la configuration.
1. Désinstallez le logiciel Adobe Commerce.
1. Réinitialisez la branche Git.

Après avoir effectué les étapes suivantes :

* votre installation Adobe Commerce revient à son état Vanilla (base de données restaurée ; configuration de déploiement supprimée ; répertoires sous `var` effacés)
* votre branche git est réinitialisée à l’état souhaité dans le passé

Lisez les étapes détaillées ci-dessous :

### Étape 0 (Prérequis) : Supprimer config.php pour désactiver Configuration Management {#disable_config_management}

Nous devons désactiver la gestion de la configuration afin qu’elle n’applique pas automatiquement les paramètres de configuration précédents lors du déploiement.

Pour désactiver la gestion de la configuration, assurez-vous que votre répertoire `/app/etc/` ne contient pas les fichiers `config.php` (pour Adobe Commerce 2.4.x) ou `config.local.php` (pour Adobe Commerce 2.1.x).

Pour supprimer le fichier de configuration, procédez comme suit :

1. [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Supprimez le fichier de configuration :
   * Pour Adobe Commerce 2.4 :

   ```php
    rm app/etc/config.php
   ```

   * Pour Adobe Commerce 2.1 :

   ```php
     rm app/etc/config.local.php
   ```

Pour en savoir plus sur la gestion de la configuration, consultez [Gestion de la configuration pour les paramètres du magasin](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) dans notre documentation destinée aux développeurs.

### Étape 1 : désinstaller le logiciel Adobe Commerce avec la commande setup:uninstall {#setup-uninstall}


La désinstallation du logiciel Adobe Commerce interrompt et restaure la base de données, supprime la configuration de déploiement et efface les répertoires situés sous `var`.

Consultez [Désinstaller le logiciel Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) dans notre documentation destinée aux développeurs.

Pour désinstaller le logiciel Adobe Commerce, procédez comme suit :

1. [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Exécuter `setup:uninstall` :

   ```php
     php bin/magento setup:uninstall
   ```

1. Confirmez la désinstallation.

Le message suivant s’affiche pour confirmer la réussite de la désinstallation :

```php
[SUCCESS]: Magento uninstallation complete.
```

Cela signifie que nous avons rétabli notre installation d’Adobe Commerce (y compris DB) à son état authentique (Vanilla).

### Étape 2 : réinitialiser la branche Git {#reset-git-branch}

Avec la réinitialisation Git, nous rétablissons l’état souhaité du code dans le passé.

1. Clonez l’environnement vers votre environnement de développement local. Vous pouvez copier la commande dans la console Cloud :    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Accéder à l’historique des validations. Utilisez `--reverse` pour afficher l’historique dans l’ordre inverse pour plus de commodité :

   ```git
     git log --reverse
   ```

1. Sélectionnez le hachage de validation pour lequel vous êtes satisfait. Pour réinitialiser le code à son état d’authenticité (Vanilla), recherchez la toute première validation qui a créé votre branche (environnement).    ![Sélection d’un hachage de validation dans la console Git](assets/select_commit_hash.png)
1. Appliquer la réinitialisation Hard Git :

   ```git
     git reset --h <commit_hash>
   ```

1. Envoyez les modifications au serveur :

   ```git
     git push --force <origin> <branch>
   ```

Après avoir effectué ces étapes, notre branche Git est réinitialisée et l’ensemble du journal des modifications Git est effacé. La dernière notification push Git déclenche le redéploiement pour appliquer toutes les modifications et réinstaller Adobe Commerce.

## Scénario 2 : aucun instantané ; version rompue (aucune connexion SSH) {#scen3}

Cette section explique comment restaurer un environnement lorsqu’il est dans un état critique : la procédure de déploiement ne peut pas réussir à créer une application en cours d’exécution, ce qui rend la connexion SSH indisponible.

Dans ce scénario, vous devez d’abord restaurer l’état de fonctionnement de votre application Adobe Commerce à l’aide de la réinitialisation Git, puis désinstaller le logiciel Adobe Commerce (pour supprimer et restaurer la base de données, supprimer la configuration de déploiement, etc.). Le scénario implique les mêmes étapes que dans le scénario 1, mais l’ordre des étapes est différent et il existe une étape supplémentaire : forcer le redéploiement. Les étapes sont les suivantes :

[&#x200B;1. Réinitialisez la branche Git.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)

[2. Désactivez la gestion de la configuration.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)

[&#x200B;3. Désinstallez le logiciel Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)

4&amp;période; Forcer le redéploiement.

Après avoir effectué ces étapes, vous obtiendrez les mêmes résultats que dans le scénario 1.

### Étape 4 : forcer le redéploiement

Effectuez une validation (il peut s’agir d’une validation vide, bien que nous ne la recommandions pas) et envoyez-la au serveur pour déclencher le redéploiement :

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## Si la configuration échoue:uninstall réinitialisez manuellement la base de données

Si l&#39;exécution de la commande `setup:uninstall` échoue avec une erreur et ne peut pas être exécutée, nous pouvons effacer manuellement la base de données en procédant comme suit :

1. [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Connectez-vous à la base de données MySQL :

   ```sql
   mysql -h database.internal
   ```

1. Déposez la base de données `main` :

   ```sql
   drop database main;
   ```

1. Créez une base de données `main` vide :

   ```sql
   create database main;
   ```

1. Supprimez les fichiers de configuration suivants : `config.php`, `config.php` `.bak`, `env.php` et `env.php.bak`.

Après la réinitialisation de la base de données, [effectuez une notification push Git vers l’environnement pour déclencher le redéploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#git-commands) et installez Adobe Commerce sur une base de données nouvellement créée. Ou [exécutez la commande redeploy](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [Restaurer un instantané sur le cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup)
* [Créer un instantané](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-a-manual-backup)
* [Snapshots et gestion des sauvegardes](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* [Gérer les branches avec la console cloud - Afficher les journaux](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html?lang=en#view-logs)
* [Échec du déploiement des composants](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/recover-failed-deployment.html)
* [Gérer le projet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project)
