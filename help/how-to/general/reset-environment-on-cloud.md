---
title: Réinitialisation de l’environnement sur Adobe Commerce sur l’infrastructure cloud
description: Cet article présente différents scénarios de restauration d’un environnement sur Adobe Commerce sur l’infrastructure cloud.
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: f2aeb0262ddcb3d7e78028d08b9323db243fc96b
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 0%

---

# Réinitialisation de l’environnement sur Adobe Commerce sur l’infrastructure cloud

Cet article présente différents scénarios de restauration d’un environnement sur Adobe Commerce sur l’infrastructure cloud.

Choisissez la méthode la plus adaptée à votre cas :

* Si vous avez prévu une activité (déploiement ou mise à niveau prévu) - [Scénario 1 : activité planifiée)](#scen1).
* Si vous disposez d’un instantané valide - [Scénario 2 : restauration d’un instantané](#scen2).
* Si vous disposez d’une version stable, mais pas d’instantané valide - [Scénario 3 : aucun instantané, version stable (connexion SSH disponible)](#scen3).
* Si la version est endommagée et que vous n’avez pas d’instantané valide - [Scénario 4 : aucun instantané ; version rompue (aucune connexion SSH)](#scen4).

## Scénario 1 : activité planifiée

Avec un déploiement ou une mise à niveau planifié, le plus simple et recommandé [!UICONTROL Rollback] serait que le marchand, dans le cadre de vos préparatifs, effectue les opérations suivantes :

>[!NOTE]
>
>Toujours tester ces étapes dans votre **[!UICONTROL Staging Environment]** tout d&#39;abord !

<u>Cinq jours avant les activités de mise à niveau/déploiement</u>:

1. Vérifiez la taille de la base de données active.
1. Vérifiez que vous disposez de suffisamment d’espace disque sur `/data/exports` pour contenir un [!UICONTROL Database Dump]. Si vous ne disposez pas de suffisamment d’espace disque, supprimez les données indésirables ou créez un cas de support et demandez au disque d’être développé.

<u>Le jour des modifications</u>:

1. Placez le site web dans [!UICONTROL Maintenance Mode].<br>
En savoir plus sur [Activer ou désactiver [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) dans notre guide d’utilisation, et [[!UICONTROL Maintenance Mode] options de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) dans notre guide de mise à niveau.
1. Prenez un local [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u>Si une [!UICONTROL Rollback] est requis</u>:

1. Si des applications telles que [!DNL MariaDB] a été mis à niveau dans le cadre de cette activité planifiée, demandez d’abord que l’application soit réinstallée vers une version précédente.
1. [!UICONTROL Rollback] la base de données à l&#39;aide de l&#39;attribut local [!UICONTROL Database Dump], puis réimportez-les dans [!DNL MariaDB].
1. [!UICONTROL Rollback] le code via [!DNL Git] à une version de travail précédente.

Utilisation [!UICONTROL Snapshots] n’est pas la méthode recommandée pour l’activité de mise à niveau/planifiée [!UICONTROL rollbacks/restores], car la récupération des données par rapport à un [!UICONTROL Database Dump], comme indiqué à l’étape 2 de la **Si une [!UICONTROL Rollback] est requis** .

[!UICONTROL Snapshots] ne sont pas conservés sur le noeud/serveur, ils sont conservés sur un bloc de stockage distinct, et comme ces données doivent être transmises du stockage de bloc sur le réseau à un nouveau disque, le processus prend du temps. Ce nouveau disque est ensuite monté sur le noeud prêt à être récupéré/importé sur le disque d’origine connecté au noeud/serveur.

Lorsque vous comparez cela à l’importation d’un fichier local [!UICONTROL Database Dump], les données sont déjà récupérables sur le noeud/serveur, de sorte que beaucoup de temps est enregistré en tant que [!UICONTROL Database Import] est obligatoire.

## Scénario 2 : restauration d’un instantané

Lecture : [Restauration d’un instantané sur Adobe Commerce sur l’infrastructure cloud](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) dans notre documentation destinée aux développeurs.

>[!NOTE]
>
>La création d’un instantané doit être notre toute première étape après l’accès à Adobe Commerce sur le compte d’infrastructure cloud et avant l’application de modifications majeures. Il s’agit d’une bonne pratique et vivement recommandée.

Lecture : [Création d’un instantané](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) dans notre documentation destinée aux développeurs.

## Scénario 3 : aucun instantané, version stable (connexion SSH disponible)

Cette section explique comment réinitialiser un environnement lorsque vous n’avez pas créé d’instantané, mais que vous pouvez accéder à l’environnement via SSH.

Les étapes sont les suivantes :

1. Désactivez la gestion de la configuration.
1. Désinstallez le logiciel Adobe Commerce.
1. Réinitialisez la variable [!DNL git] branche.

Après avoir effectué les étapes suivantes :

* Votre installation Adobe Commerce retourne à son état Vanilla (base de données restaurée, configuration de déploiement supprimée, répertoires situés sous `var` effacé).
* Votre [!DNL git] est réinitialisée à l’état souhaité dans le passé.

Lisez les étapes détaillées ci-dessous.

### Étape 0 (condition préalable requise) : supprimez config.php pour désactiver Configuration Management

Nous devons désactiver Configuration Management afin qu’elle n’applique pas automatiquement les paramètres de configuration précédents lors du déploiement.

Pour désactiver Configuration Management, assurez-vous que la variable `/app/etc/` ne contient pas le répertoire `config.php` fichier .

Pour supprimer le fichier de configuration, procédez comme suit :

1. [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Supprimez le fichier de configuration : `rm app/etc/config.php`

En savoir plus sur Configuration Management :

* [Réduction du temps d’arrêt du déploiement sur Adobe Commerce sur l’infrastructure cloud](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) dans notre base de connaissances de soutien.
* [Gestion des configurations pour les paramètres du magasin](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) dans notre documentation destinée aux développeurs.

### Étape 1 : désinstallation du logiciel Adobe Commerce avec la commande setup:uninstall


La désinstallation du logiciel Adobe Commerce supprime et restaure la base de données, supprime la configuration de déploiement et efface les répertoires sous `var`.

Lecture : [Désinstallation du logiciel Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) dans notre documentation destinée aux développeurs.

Pour désinstaller le logiciel Adobe Commerce, procédez comme suit :

1. [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Exécuter `setup:uninstall` : `bin/magento setup:uninstall`
1. Confirmez la désinstallation.

Le message suivant s’affiche pour confirmer la désinstallation :

```php
[SUCCESS]: Magento uninstallation complete.
```

Cela signifie que nous avons rétabli notre installation Adobe Commerce (y compris DB) sur son état authentique (Vanilla).

### Étape 2 : réinitialiser la variable [!DNL git] branche

Avec [!DNL git] réinitialiser, nous avons rétabli le code à l’état souhaité dans le passé.

1. Cloner l’environnement vers votre environnement de développement local. Vous pouvez copier la commande dans la console cloud :    ![copy_git_clone.png](assets/copy_git_clone.png)
1. Accédez à l’historique des validations. Utilisation `--reverse` pour afficher l’historique dans l’ordre inverse, afin de faciliter les opérations : `git log --reverse`
1. Sélectionnez le hachage de validation sur lequel vous avez été bon. Pour réinitialiser le code à son état authentique (Vanilla), recherchez la toute première validation qui a créé votre branche (environnement).
   ![Sélection d’un hachage de validation dans la console Git](assets/select_commit_hash.png)
1. Appliquer les conditions difficiles [!DNL git] reset : `git reset --h <commit_hash>`
1. Push changes to server : `git push --force <origin> <branch>`

Après avoir effectué ces étapes, nos [!DNL git] la branche est réinitialisée et l’intégralité de la [!DNL git] changelog est clair. Le dernier [!DNL git] push déclenche le redéploiement pour appliquer toutes les modifications et réinstaller Adobe Commerce.

## Scénario 4 : aucun instantané ; version rompue (pas [!DNL SSH] connection)

Cette section explique comment réinitialiser un environnement lorsqu’il se trouve dans un état critique : la procédure de déploiement ne peut pas réussir à créer une application de travail, ce qui a pour effet de [!DNL SSH] connexion indisponible.

Dans ce scénario, vous devez d’abord restaurer l’état de fonctionnement de votre application Adobe Commerce à l’aide de [!DNL git] réinitialisez, puis désinstallez le logiciel Adobe Commerce (pour déposer et restaurer la base de données, supprimer la configuration de déploiement, etc.). Le scénario comprend les mêmes étapes que dans le scénario 3, mais l’ordre des étapes est différent et il existe une autre étape : forcer le redéploiement. Les étapes sont les suivantes :

1. [Réinitialisez la variable [!DNL git] branche.](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [Désactivez la gestion de la configuration.](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [Désinstallez le logiciel Adobe Commerce.](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. Forcer le redéploiement.

Une fois ces étapes effectuées, les résultats seront les mêmes que dans le scénario 3.

### Étape 4 : forcer le redéploiement

Effectuez une validation (il peut s’agir d’une validation vide, bien que nous ne la recommandions pas) et envoyez-la au serveur pour déclencher le redéploiement :

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## En cas d’échec de l’installation:désinstallation, réinitialisez manuellement la base de données

Si l’exécution de la variable `setup:uninstall` échoue avec une erreur et ne peut pas être effectuée, la base de données peut être effacée manuellement en procédant comme suit :

1. [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Connectez-vous à la base de données MySQL : `mysql -h database.internal` (Pour les environnements Pro, voir : [Configuration du service MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)).
1. Déposez le `main` DB : `drop database main;`
1. Créer un champ vide `main` DB : `create database main;`
1. Supprimez les fichiers de configuration suivants : `config.php` , `config.php` , `.bak,` , `env.php`, `env.php.bak`

Après avoir réinitialisé la base de données, [make a [!DNL git] Push vers l’environnement pour déclencher le redéploiement](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) et installez Adobe Commerce sur une base de données nouvellement créée. Ou [exécuter la commande redeploy](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).
