---
title: Liste de contrôle pour la configuration d’un nouveau [!DNL domain]
description: Il s’agit d’une liste de contrôle indiquant comment configurer un nouveau  [!DNL domain] dans Adobe Commerce sur l’infrastructure cloud.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Liste de contrôle pour la configuration d&#39;un nouveau [!DNL domain]

Il s’agit d’une liste de contrôle indiquant comment configurer un nouveau [!DNL domain] dans Adobe Commerce sur l’infrastructure cloud. Il s’applique, que vous souhaitiez simplement ajouter un nouveau domaine ou remplacer le domaine actuel par un nouveau.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Configuration d’un nouveau domaine

### Étape 1 - Est-ce pour le [!DNL Integration, Staging] ou [!DNL Production environment] ?

* **[!DNL Integration]** : [!DNL Custom domains] ne sont pas pris en charge. Vous devez plutôt utiliser cette méthode : [Configuration de plusieurs sites Web ou magasins : Configuration de l’installation locale](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) dans notre guide d’utilisation.
* **[!DNL Staging]** : accédez à **Étape 2**.
* **[!DNL Production]** : accédez à **Étape 3**.

### Étape 2 - [!DNL Staging environment] : êtes-vous sur [!DNL Pro] ou [!DNL Starter] ?

* **[!DNL Pro]** : **Envoyez une requête** pour ajouter le domaine à [!DNL Fastly, Nginx] et configurez le [!DNL SSL certificate] (ainsi que le [!DNL Sendgrid domain], si nécessaire). Une fois qu’il a été configuré, [mettez à jour la configuration [!DNL DNS] avec [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Vous pouvez ajouter vous-même le nouveau [!DNL domain] à [!DNL Fastly] en mettant à jour la configuration dans [!DNL Admin] dans **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** comme dans [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) de notre guide d’utilisation.
>
>Si vous ne parvenez pas à ajouter le domaine, cela peut être dû à l’une des raisons suivantes :
>
>1. Vous migrez le domaine vers l’environnement cloud, qui a été configuré dans votre propre service [!DNL Fastly]. Dans ce cas, envoyez une demande et une délégation de demande du domaine.
>1. Vous migrez le domaine de Starter vers Pro. Dans ce cas, soumettez une demande d’assistance supplémentaire.

* **[!DNL Starter]** : [!DNL Custom domains] ne sont pas pris en charge dans l’environnement d’évaluation.

### Étape 3 - [!DNL Production environment] : êtes-vous sur [!DNL Pro] ou [!DNL Starter] ?

* **[!DNL Pro]** : **Envoyez une requête** pour ajouter le domaine à [!DNL Fastly, Nginx] et configurez le [!DNL SSL certificate] (en tant que [!DNL Sendgrid domain], si nécessaire). Une fois qu’il a été configuré, passez à l’ **étape 4**.

>[!NOTE]
>
>Vous pouvez ajouter vous-même le nouveau [!DNL domain] à [!DNL Fastly] en mettant à jour la configuration dans [!DNL Admin] dans **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) dans notre guide d’utilisation.
>
>
>Si vous ne parvenez pas à ajouter le domaine, cela peut être dû à l’une des raisons suivantes :
>
>1. Vous migrez le domaine de l’environnement sur site vers l’environnement cloud, qui a été configuré dans votre propre service [!DNL Fastly]. Dans ce cas, envoyez une demande et une délégation de demande du domaine.
>1. Vous migrez le domaine de Starter vers Pro. Dans ce cas, soumettez une demande d’assistance supplémentaire.

* **[!DNL Starter]** : Ajoutez le [!DNL domain] à votre projet dans l’onglet **[!DNL Domains]** , puis **envoyez une requête** pour fournir le **[!DNL ACME Challenge Key]** pour le [!DNL SSL certificate].

### Étape 4 - L’ [!DNL domain] est-il actif ?

* **OUI** : [Mettez à jour la configuration  [!DNL DNS]  avec [!UICONTROL production] paramètres](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NO** : [Mettez à jour la configuration  [!DNL DNS]  avec [!UICONTROL development] settings](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Lecture connexe

* [Configuration de plusieurs sites Web ou magasins : ajoutez New [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) dans notre guide d’utilisation.
