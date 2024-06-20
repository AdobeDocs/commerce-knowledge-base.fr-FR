---
title: "ACSD-52041 : le rendu du générateur de pages ne libère pas les verrous"
description: Appliquez le correctif ACSD-52041 pour résoudre le problème Adobe Commerce en raison duquel le générateur de pages s’affiche pendant cinq secondes sans déclencher de verrous.
feature: Page Builder
role: Admin, Developer
exl-id: f2a1fd36-2098-46a7-aa42-3a5a0014adc9
source-git-commit: fc5dc9fcf610cae6f8c0a334b4ef15029c462c66
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-52041 : Le rendu du générateur de pages ne libère pas les verrous

Le correctif ACSD-52041 corrige le problème de rendu de Page Builder pendant cinq secondes sans relâcher de verrous. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.48 est installée. L’ID de correctif est ACSD-52041-v2. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.4-p8, 2.4.5 - 2.4.5-p7, 2.4.6 - 2.4.6-p6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le Créateur de pages effectue un rendu pendant cinq secondes sans déclencher de verrous.

<u>Étapes à reproduire</u>:

1. Modifiez une page CMS, une page de produit ou tout autre page comportant le Créateur de pages.
1. Enregistrez les modifications.
1. Remarquez le temps d’économie de la page.

<u>Résultats attendus</u>

Le contenu est enregistré. Aucune erreur n’a été trouvée dans le journal du navigateur.

<u>Résultats réels</u>

L’enregistrement prend plus de temps que la durée habituelle.
Erreur dans la console : ``Page Builder was rendering for 5 seconds without releasing locks``

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) dans le [!DNL Quality Patches Tool] guide.
