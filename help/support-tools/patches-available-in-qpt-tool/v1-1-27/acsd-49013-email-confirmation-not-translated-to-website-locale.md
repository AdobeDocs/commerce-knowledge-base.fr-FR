---
title: '''ACSD-49013 : confirmation d''email non traduite en paramètre régional du site web'''
description: Appliquez le correctif ACSD-49013 pour résoudre le problème Adobe Commerce en raison duquel la confirmation par courrier électronique n’est pas traduite dans les paramètres régionaux du site web lors de la création de clients à l’aide de l’API en bloc.
exl-id: 68203bd4-021a-4736-a793-4b6663a9c66b
feature: Admin Workspace, Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-49013 : confirmation d&#39;email non traduite dans les paramètres régionaux du site web

Le correctif ACSD-49013 corrige le problème en raison duquel la confirmation par email n’est pas traduite dans les paramètres régionaux du site web lors de la création de clients à l’aide d’une API en bloc. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.27 est installée. L’ID de correctif est ACSD-49013. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La confirmation par e-mail n’est pas traduite dans les paramètres régionaux du site web lors de la création de clients à l’aide de l’API en bloc.

<u>Étapes à reproduire</u>:

1. Installez un autre paramètre régional comme `de_DE`.
1. Configurer *RabbitMQ*.
1. Exécuter `bin/magento setup:upgrade` pour installer les files d’attente dans RabbitMQ et configurer le module de langue.
1. Créez un site web supplémentaire dans [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Définir la langue de ce nouveau site web sur `de_DE` in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Exécutez un appel API pour créer un compte client à l’aide de l’API en bloc. Utilisez la variable `website_id`.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Exécuter `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. Vous pouvez constater que le compte client a été créé correctement sur le site web spécifié.
1. Vérifiez l’e-mail reçu pour l’enregistrement du client.

<u>Résultats attendus</u>:

Le client étant créé sur un site web spécifique, le courrier électronique d’enregistrement est envoyé en utilisant les paramètres régionaux de ce site web.

<u>Résultats réels</u>:

Le client est créé correctement sur le site web spécifié, mais l’email d’enregistrement est envoyé en utilisant le paramètre régional par défaut lors de l’utilisation de l’API en bloc.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
