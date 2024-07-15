---
title: Configuration de la connexion Adobe Commerce Intelligence pour les projets Cloud Starter existants
description: Cet article fournit une solution pour configurer la connexion Adobe Commerce Intelligence pour un projet Cloud Starter existant.
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Configuration de la connexion Adobe Commerce Intelligence pour les projets Cloud Starter existants

>[!NOTE]
>
>Adobe Commerce Intelligence était auparavant connu sous le nom de Magento Business Intelligence (MBI).

Cet article fournit une solution pour configurer la connexion Adobe Commerce Intelligence pour un projet Cloud Starter existant.

## Produits et versions concernés

Adobe Commerce au démarrage dans le cloud (toutes les versions)

## Problème

Vous souhaitez configurer la connexion Commerce Intelligence pour un projet Cloud Starter existant.

>[!NOTE]
>
>Adobe ne prend plus en charge les nouveaux abonnements à Cloud Starter, mais si vous disposez déjà d’un projet de démarrage, vous devez suivre les étapes ci-dessous pour configurer votre connexion.

## Solution

Pour activer Commerce Intelligence pour les projets Cloud Starter, créez un compte Commerce Intelligence, créez une clé SSH, puis connectez-vous enfin à votre base de données Adobe Commerce.

Procédez comme suit :

1. Créez votre compte Adobe Commerce Intelligence :

   * Accédez à [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * Accédez à **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * Cliquez sur le **[!UICONTROL Create Instance]**. Si vous ne voyez pas ce bouton, contactez votre responsable du succès client ou votre conseiller technique client.
   * Sélectionnez votre abonnement Cloud Starter. Si vous disposez uniquement d’un abonnement Cloud Starter, celui-ci est automatiquement sélectionné.
   * Cliquez sur **[!UICONTROL Continue]**.
   * Saisissez vos informations pour créer votre compte.

   ![Créer un compte MBI](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * Accédez à votre boîte de réception et vérifiez l’adresse électronique.

   ![Vérifier l’adresse électronique](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * Créez un mot de passe.

   ![Créer un mot de passe](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * Une fois votre compte créé, vous avez la possibilité d’ajouter des utilisateurs à votre nouveau compte. Vous pouvez désormais ajouter des administrateurs techniques pour réaliser les étapes suivantes.

   ![Ajouter des utilisateurs](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. Informations d’entrée sur votre magasin pour définir vos préférences.

   ![Ajouter des informations de magasin](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   Vous devrez rassembler certaines informations avant de pouvoir connecter votre base de données pour la troisième étape du flux d’intégration. Vous allez renseigner la page *[!UICONTROL Connect your database]* à l’étape 9.

1. Créez un utilisateur Commerce Intelligence dédié.

   * Créez un nouvel utilisateur sur [account.adobe.com](https://account.adobe.com/).
   * Accédez à [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) pour générer votre compte Adobe Commerce.
   * Pourquoi un nouvel utilisateur ? Adobe Commerce Intelligence a besoin d’un utilisateur ajouté au projet pour récupérer en permanence de nouvelles données à transférer à l’entrepôt de données Commerce Intelligence du compte. Cet utilisateur servira de connexion. L’ajout de cet utilisateur au projet se fera à l’étape 4.
   * La raison pour laquelle un utilisateur Commerce Intelligence dédié est d’empêcher l’utilisateur ajouté d’être désactivé ou supprimé par inadvertance et d’arrêter la connexion Commerce Intelligence.

1. Ajoutez l’utilisateur nouvellement créé à l’environnement principal du projet en tant que *contributeur*.

   ![Ajouter un utilisateur en tant que contributeur](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. Procurez-vous vos clés SSH Commerce Intelligence.

   * Accédez à la page **[!UICONTROL Connect your database]** de l’interface utilisateur de configuration de Commerce Intelligence et faites défiler l’écran jusqu’à **[!UICONTROL Encryption settings]**.
   * Pour le champ, **[!UICONTROL Encryption Type]**, choisissez **[!UICONTROL SSH Tunnel]**.
   * Dans la liste déroulante, vous pouvez copier et coller la clé publique Essentials BI Magento fournie.

   ![Paramètres de chiffrement](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. Ajoutez votre nouvelle clé publique Magento BI Essentials à l’utilisateur Commerce Intelligence créé à l’étape 5.

   * Accédez à [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). Connectez-vous avec les informations de connexion de votre compte pour le nouvel utilisateur Commerce Intelligence créé. Ensuite, accédez à l’onglet **[!UICONTROL Account Settings]** .
   * Faites défiler la page vers le bas et développez la liste déroulante pour les clés SSH. Cliquez ensuite sur **[!UICONTROL Add a public key]**.

   ![Ajouter une clé publique](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * Ajoutez la clé publique SSH Essentials SSH du Magento ci-dessus.

   ![Ajouter une clé publique SSH](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. Indiquez les informations d’identification MySQL de Business Intelligence Essentials.

   * Mettez à jour votre `.magento/services.yaml`.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * Mettez à jour votre `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. Obtenez des informations sur la connexion de votre base de données à Commerce Intelligence.

   Exécutez `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` pour obtenir des informations sur la connexion à votre base de données.

   Vous devriez recevoir des informations similaires à la sortie ci-dessous :

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. Connectez votre base de données Adobe Commerce.

   ![Connectez votre base de données Adobe Commerce](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *Entrées* :

   * Nom de l’intégration : [Choisissez un nom pour votre intégration.]
   * Hôte : `mbi.internal`
   * Port : 3306
   * Nom d’utilisateur : mbi
   * Mot de passe : [mot de passe d’entrée fourni dans la sortie de l’étape 8.]
   * Database Name : main
   * Préfixes de table : [laissez vide s’il n’existe aucun préfixe de table]

1. Définissez votre [!UICONTROL Timezone Settings].

   ![ Paramètres de fuseau horaire ](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *Entrées*

   * Base de données : Fuseau horaire : UTC
   * Fuseau horaire souhaité : [sélectionnez le fuseau horaire dans lequel vos données doivent s’afficher.]

1. Obtenez des informations sur vos paramètres de chiffrement.

   * L’interface utilisateur du projet fournit une chaîne d’accès SSH. Cette chaîne peut être utilisée pour collecter les informations nécessaires pour l’ adresse distante et le nom d’utilisateur lors de la configuration de votre **[!UICONTROL Encryption settings]**. Sélectionnez **[!UICONTROL SSH]** pour afficher votre nom d’utilisateur et votre adresse distante. La chaîne de texte précédant le *@* est votre nom d’utilisateur et la chaîne de texte suivant le *@* est votre adresse distante.

   ![Accéder au maître du site](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. Informations d’entrée pour votre [!UICONTROL Encryption Settings].

   ![Paramètres de chiffrement](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *Entrées*

   * Type de chiffrement : tunnel SSH
   * Adresse distante : ssh.us-3.magento.cloud
   * Nom d’utilisateur : vfbfui4vmfez6-master-7rqtwti—mymagento
   * Port : 22

1. Cliquez sur **[!UICONTROL Save Integration]**.
1. Vous êtes maintenant connecté à votre compte Commerce Intelligence Essentials.
1. Si vous êtes client Adobe Commerce Intelligence Pro, contactez votre responsable du succès client ou votre conseiller technique client pour coordonner les étapes suivantes.
