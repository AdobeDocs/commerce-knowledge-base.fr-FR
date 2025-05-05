---
title: "ACSD-51853 : les styles de texte copiés ne sont pas appliqués à l’aide du créateur de pages"
description: Appliquez le correctif ACSD-51853 pour résoudre le problème Adobe Commerce en raison duquel les styles de texte copiés ne sont pas appliqués lorsque le créateur de pages est utilisé.
feature: Page Builder
role: Admin
exl-id: 1efd3147-1ae0-468b-af04-1632fbaaefda
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51853 : les styles de texte copiés ne sont pas appliqués à l’aide du créateur de pages.

Le correctif ACSD-51853 corrige le problème en raison duquel les styles de texte copiés ne sont pas appliqués lorsque le créateur de pages est utilisé. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.34 est installé. L’ID de correctif est ACSD-51853. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les styles de texte copiés ne sont pas appliqués lors de l’utilisation du créateur de pages.

<u>Étapes à reproduire</u> :

1. Connectez-vous à l’administrateur.
1. Accédez à > **content** > **pages** > **Ouvrir une page** > **Modifier avec le générateur de page**.
1. Faites glisser Rangée et *Texte* depuis **[!UICONTROL Elements]**.
1. Copiez **contenu enrichi**, collez ce texte dans un **[!UICONTROL Page Builder]**.

<u>Résultats attendus</u>

Le texte copié est collé avec tous les styles.

<u>Résultats réels</u>

Le texte copié est collé en tant que texte brut et tous les styles sont perdus.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
