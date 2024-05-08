---
title: Liste de contrôle pour la configuration d’une nouvelle [!DNL domain]
description: Il s’agit d’une liste de contrôle indiquant comment configurer une nouvelle [!DNL domain] dans Adobe Commerce sur l’infrastructure cloud.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Liste de contrôle pour la configuration d’une nouvelle [!DNL domain]

Il s’agit d’une liste de contrôle indiquant comment configurer une nouvelle [!DNL domain] dans Adobe Commerce sur l’infrastructure cloud. Il s’applique, que vous souhaitiez simplement ajouter un nouveau domaine ou remplacer le domaine actuel par un nouveau.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Configuration d’un nouveau domaine

### Étape 1 - Est-ce pour la variable [!DNL Integration, Staging], ou [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] ne sont pas prises en charge. Utilisez plutôt cette méthode : [Configuration de plusieurs sites web ou magasins : configuration d’une installation locale](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) dans notre guide d’utilisation.
* **[!DNL Staging]**: accédez à **Étape 2**.
* **[!DNL Production]**: accédez à **Étape 3**.

### Etape 2 - [!DNL Staging environment]: êtes-vous activé [!DNL Pro] ou [!DNL Starter]?

* **[!DNL Pro]**: **Envoyer une requête** pour ajouter le domaine à [!DNL Fastly, Nginx]et configurez la variable [!DNL SSL certificate] (ainsi que la variable [!DNL Sendgrid domain], si nécessaire). Une fois configuré, [mettre à jour la variable [!DNL DNS] configuration avec [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Vous pouvez ajouter la nouvelle [!DNL domain] to [!DNL Fastly] vous-même en mettant à jour la configuration dans la variable [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** as in [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) dans notre guide d’utilisation.
>
>Si vous ne parvenez pas à ajouter le domaine, cela peut être dû à l’une des raisons suivantes :
>
>1. Vous migrez le domaine vers l’environnement cloud qui a été configuré dans votre propre [!DNL Fastly] service. Dans ce cas, envoyez une demande et une délégation de demande du domaine.
>1. Vous migrez le domaine de Starter vers Pro. Dans ce cas, soumettez une demande d’assistance supplémentaire.

* **[!DNL Starter]**: [!DNL Custom domains] ne sont pas pris en charge dans l’environnement d’évaluation.

### Etape 3 - [!DNL Production environment]: êtes-vous activé [!DNL Pro] ou [!DNL Starter]?

* **[!DNL Pro]**: **Envoyer une requête** pour ajouter le domaine à [!DNL Fastly, Nginx]et configurez la variable [!DNL SSL certificate] (comme la variable [!DNL Sendgrid domain], si nécessaire). Une fois que a été configuré, continuez à **Étape 4**.

>[!NOTE]
>
>Vous pouvez ajouter la nouvelle [!DNL domain] to [!DNL Fastly] vous-même en mettant à jour la configuration dans la variable [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) dans notre guide d’utilisation.
>
>
>Si vous ne parvenez pas à ajouter le domaine, cela peut être dû à l’une des raisons suivantes :
>
>1. Vous migrez le domaine de l’environnement local vers l’environnement cloud, qui a été configuré dans votre propre [!DNL Fastly] service. Dans ce cas, envoyez une demande et une délégation de demande du domaine.
>1. Vous migrez le domaine de Starter vers Pro. Dans ce cas, soumettez une demande d’assistance supplémentaire.

* **[!DNL Starter]**: ajoutez le [!DNL domain] à votre projet dans le **[!DNL Domains]** , puis **envoyer une requête ;** pour fournir la variable **[!DNL ACME Challenge Key]** pour le [!DNL SSL certificate].

### Étape 4 - Est la variable [!DNL domain] live ?

* **OUI**: [Mettez à jour le [!DNL DNS] configuration avec [!UICONTROL production] paramètres](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NON**: [Mettez à jour le [!DNL DNS] configuration avec [!UICONTROL development] paramètres](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Lecture connexe

* [Configurer plusieurs sites Web ou magasins : Ajouter nouveau [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) dans notre guide d’utilisation.
