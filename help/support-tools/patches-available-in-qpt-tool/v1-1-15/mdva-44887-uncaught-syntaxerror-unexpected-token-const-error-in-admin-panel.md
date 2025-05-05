---
title: "MDVA-44887: 'Uncaught SyntaxError: Uncaught token const (erreur de syntaxe non interceptée : const de jetons inattendus) dans le panneau d’administration"
description: "Le correctif MDVA-44887 corrige le problème où l’utilisateur administrateur ne peut cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unpending token const* s’affiche dans le panneau d’administration. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 est installé. L’ID de correctif est MDVA-44887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5."
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887 : Erreur de syntaxe non interceptée : erreur &quot;Conteneur de jetons inattendu&quot; dans le panneau d’administration

Le correctif MDVA-44887 corrige le problème en raison duquel l’utilisateur administrateur ne pouvait cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unpending token const* s’affiche dans le panneau d’administration. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 est installé. L’ID de correctif est MDVA-44887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur administrateur ne peut cliquer sur aucune option de menu. L’erreur *Uncaught SyntaxError: Unpending token const* s’affiche dans le panneau d’administration.

<u>Étapes à reproduire</u> :

1. Activez le regroupement JS.
1. Minifiez les fichiers JS.
1. Connectez-vous au panneau d’administration de Commerce.

<u>Résultats attendus</u> :

L’utilisateur administrateur ne peut cliquer sur aucune option de menu. Une erreur s’est produite dans la console du navigateur : *Uncaught SyntaxError: Unpending token const*.

<u>Résultats réels</u> :

Un utilisateur administrateur peut accéder au panneau d’administration.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
