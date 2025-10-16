---
title: Liste de contrôle pour la configuration d’un nouveau  [!DNL domain]
description: Il s’agit d’une liste de contrôle décrivant comment configurer un nouveau  [!DNL domain]  dans Adobe Commerce sur l’infrastructure cloud.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 552a290b50f9e0c5fa740f26092c57bac447fe68
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Liste de contrôle pour la configuration d’un nouveau [!DNL domain]

Cette liste de contrôle explique comment configurer un nouveau [!DNL domain] dans Adobe Commerce sur l’infrastructure cloud. Elle s’applique que vous ajoutiez un nouveau domaine ou que vous remplaciez le domaine actuel. Elle s’applique également après l’obtention d’un nouvel environnement d’évaluation (voir Étape 4).

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Configuration d’un nouveau domaine

>[!NOTE]
>
>Avant de poursuivre la configuration du domaine, assurez-vous des points suivants :
>
>Toutes les URL de base sont configurées pour utiliser HTTPS sous **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**, avec la portée de la vue correcte du site web ou de la boutique.
>&#x200B;> [Forcer TLS](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/how-to/redirect-http-to-https-for-all-pages-on-cloud-force-tls#token_type=bearer&expires_in=10799996) est activé pour rediriger tout le trafic HTTP vers HTTPS sur votre site Adobe Commerce sur l’infrastructure cloud.

### Étape 1 : s’agit-il de l’[!DNL Integration, Staging] ou de l’[!DNL Production environment] ?

* **[!DNL Integration]** : les [!DNL Custom domains] ne sont pas pris en charge. Vous devez utiliser la méthode suivante à la place : [Configurer plusieurs sites web ou magasins : Configurer l’installation locale](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=fr#add-new-domains) dans notre guide d’utilisation.
* **[!DNL Staging]** : accédez à **Étape 2**.
* **[!DNL Production]** : passez à **étape 3**.

### Étape 2 - [!DNL Staging environment] : êtes-vous sur [!DNL Pro] ou [!DNL Starter] ?

* **[!DNL Pro]** : **Envoyez une demande** pour ajouter le domaine à [!DNL Fastly, Nginx] et configurer le [!DNL SSL certificate] (ainsi que le [!DNL Sendgrid domain], si nécessaire). Une fois cette configuration terminée, [mettez à jour la configuration avec [!DNL DNS]  [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Pour l’architecture PRO, l’ajout d’un nouveau domaine nécessite l’envoi d’une demande d’assistance à Adobe Commerce. Bien que certains clients puissent configurer manuellement Fastly via Admin Console, cela ne s’applique que dans certains cas, par exemple lorsque le domaine n’est pas lié à un autre service ou projet Fastly. Cependant, la configuration de Nginx est toujours requise et cette étape doit être gérée par Adobe. Pour cette raison, l’approche recommandée et la plus fiable est d’envoyer un [ticket d’assistance](https://experienceleague.adobe.com/home?lang=fr&support-tab=home#support) et de laisser Adobe gérer l’ensemble du processus de configuration du domaine.


* **[!DNL Starter]** : les [!DNL Custom domains] ne sont pas prises en charge dans l’environnement d’évaluation.

### Étape 3 - [!DNL Production environment] : êtes-vous sur [!DNL Pro] ou [!DNL Starter] ?

* **[!DNL Pro]** : **Envoyez une demande** pour ajouter le domaine à [!DNL Fastly, Nginx] et configurer le [!DNL SSL certificate] (comme [!DNL Sendgrid domain], si nécessaire). Une fois que cela a été configuré, passez à **Étape 4**.

>[!NOTE]
>
>Vous pouvez ajouter le nouveau [!DNL domain] pour vous [!DNL Fastly] en mettant à jour la configuration dans le [!DNL Admin] dans **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=fr#manage-domains) dans notre guide de l’utilisateur.
>
>
>Si vous ne parvenez pas à ajouter le domaine, cela peut être dû à l’une des raisons suivantes :
>
>1. Vous effectuez une migration du domaine de l’environnement local vers l’environnement cloud, qui a été configuré dans votre propre service [!DNL Fastly]. Dans ce cas, envoyez une requête et demandez la délégation du domaine.
>1. Vous migrez le domaine de Starter vers Pro. Dans ce cas, envoyez une demande d’assistance supplémentaire.

* **[!DNL Starter]** : ajoutez les [!DNL domain] à votre projet dans l’onglet **[!DNL Domains]** , puis **soumettez une demande** pour fournir les **[!DNL ACME Challenge Key]** de la [!DNL SSL certificate].

### Étape 4 - Le [!DNL domain] est-il en ligne ?

* **OUI** : [Mettez à jour la configuration [!DNL DNS] avec [!UICONTROL production] paramètres](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=fr#update-dns-configuration-with-production-settings).
* **NON** : [mettez à jour la configuration  [!DNL DNS]  avec [!UICONTROL development] paramètres](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr#update-dns-configuration-with-development-settings).

### Étape 5 : les redirections de domaine sont-elles configurées dans `magento-vars.php` ?

Une fois le domaine configuré, vous devez [modifier les variables](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites#modify-variables) dans le fichier `magento-vars.php` pour diriger le domaine vers l’URL de site web/magasin appropriée.

### Étape 6 : la configuration [!DNL domain] est-elle vérifiée ?

Si vous avez ajouté de nouveaux magasins, groupes de magasins et sites web dans **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** pour le ou les nouveaux domaines, vérifiez si les sections suivantes apparaissent dans votre fichier `app/etc/config.php`, par exemple :

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

Cela signifie que vous avez configuré [SCD sur le build](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build) en exécutant la commande `config:dump` dans le package `ece-tools` par le passé.

Si vous constatez que le nouveau magasin/site web que vous avez créé ne s’affiche pas dans le fichier `app/etc/config.php`, veillez à exécuter à nouveau la commande pour synchroniser le fichier `config.php` avec les modifications apportées à votre base de données, puis validez le fichier `config.php` et redéployez. Cela permet de faciliter le déploiement de contenu statique pour le ou les nouveaux magasins/sites web vers les chemins d’accès aux fichiers appropriés.

## Lecture connexe

* [Configurer plusieurs sites web ou magasins : Ajouter nouveau [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=fr#add-new-domains) dans notre guide de l&#39;utilisateur.
* [Site non accessible en raison du cloaking de l&#39;origine](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26856)
