---
title: "ACSD-51574 : Image non mise à jour sur l’interface frontale lorsqu’elle est remplacée par une autre image"
description: Appliquez le correctif ACSD-51574 pour résoudre le problème Adobe Commerce en raison duquel l’image n’est pas mise à jour sur le front-end après son remplacement par une autre image.
feature: Configuration
role: Admin
exl-id: a6f26126-71c3-43c2-bba4-60a914d7ec11
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-51574 : Image non mise à jour sur l’interface frontale lorsqu’elle est remplacée par une autre image

Le correctif ACSD-51574 corrige le problème en raison duquel l’image n’est pas mise à jour sur le front-end après son remplacement par une autre image. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.37 est installée. L’ID de correctif est ACSD-51574. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.7

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’image n’est pas mise à jour sur le front-end après son remplacement par une autre image.

<u>Étapes à reproduire</u>:

1. Créez un produit avec quelques images.
1. Modifiez le produit et téléchargez une image portant un nom connu (par exemple : *image.jpg*).
1. Enregistrez le produit.
1. Modifiez à nouveau le produit, supprimez l’ancienne version de l’image, puis chargez la nouvelle version de l’image portant le même nom. **Vérifiez que la nouvelle version est visiblement différente pour voir le problème.**
1. Enregistrez le produit. L’administrateur et le front-end affichent les images.
1. Modifiez à nouveau le produit et rechargez la même nouvelle image (en utilisant le même nom).
1. Enregistrez le produit et consultez la page du produit sur le front-end.

<u>Résultats attendus</u>:

L’image téléchargée la deuxième fois doit correspondre à la nouvelle image, ainsi qu’au nom de l’image renommé.

<u>Résultats réels</u>:

L’image téléchargée la seconde fois est l’ancienne version de l’image précédemment supprimée, au lieu de la même nouvelle image.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
