---
title: "ACSD-55238 : enregistrement de la méta-description du produit vide"
description: Appliquez le correctif ACSD-55238 pour résoudre le problème Adobe Commerce en raison duquel une description de produit contenant le code de HTML généré par [!DNL Page Builder] ou un autre éditeur de HTML est toujours affiché dans la méta-description, et il n’est pas possible de le définir sur vide.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238 : enregistrement de la méta-description du produit vide

Le correctif ACSD-55238 corrige le problème en raison duquel une description de produit contenant le code de HTML généré par un éditeur de HTML s’affichait toujours dans la méta-description. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.42 est installée. L’ID de correctif est ACSD-55238. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Description du produit qui contient du code de HTML généré par [!DNL Page Builder] ou un autre éditeur de HTML est toujours affiché dans la méta-description, et il n’est pas possible de le définir sur vide.

<u>Étapes à reproduire</u>:

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** et créer un nouveau bloc avec n&#39;importe quel contenu.
1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** et créez un produit. Définissez la méta-description sur vide.
1. Ajoutez le bloc créé ci-dessus en utilisant *[!DNL Page Builder]* dans le *[!UICONTROL Content]* et enregistrez le produit.
1. Ouvrez le produit sur le storefront et vérifiez son élément de document . `meta name = "description"`.

<u>Résultats attendus</u>:

La méta-description est vide.

<u>Résultats réels</u>:

Lorsqu’une description d’un produit contient un bloc, il est utilisé pour la méta-description du produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
