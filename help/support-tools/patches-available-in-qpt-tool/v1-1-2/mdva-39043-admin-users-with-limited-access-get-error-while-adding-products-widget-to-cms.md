---
title: "MDVA-39043 : les utilisateurs administrateurs reçoivent une erreur lors de l’ajout d’un widget à la page CMS"
description: Le correctif MDVA-39043 corrige le problème en raison duquel les utilisateurs administrateurs disposant d’un accès limité obtiennent une erreur lors de l’ajout du widget "Produits" à la page CMS. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2 est installé. L’ID de correctif est MDVA-39043. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 63057351-e972-4575-9bf0-e818f590b40a
feature: Admin Workspace, CMS, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-39043 : les utilisateurs administrateurs reçoivent une erreur lors de l’ajout du widget à la page CMS.

Le correctif MDVA-39043 corrige le problème en raison duquel les utilisateurs administrateurs disposant d’un accès limité obtiennent une erreur lors de l’ajout du widget &quot;Produits&quot; à la page CMS. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.2 est installé. L’ID de correctif est MDVA-39043. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs administrateurs disposant d’un accès limité reçoivent une erreur lors de l’ajout du widget &quot;Produits&quot; à la page CMS.

<u>Étapes à reproduire</u> :

1. Connectez-vous au serveur principal à l’aide de l’administrateur avec accès uniquement pour modifier le contenu.
1. Accédez à **Contenu** > **Pages**.
1. Ouvrez une page à modifier.
1. Modifiez le contenu avec **Page Builder**.
1. Ajoutez le widget **Product** de la section **Ajouter du contenu** .
1. Cliquez sur **Configurer** sur le widget **Produit** .

<u>Résultats attendus</u> :

Aucune erreur ne s’affiche.

<u>Résultats réels</u> :

Le message d’erreur suivant est reçu :

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
