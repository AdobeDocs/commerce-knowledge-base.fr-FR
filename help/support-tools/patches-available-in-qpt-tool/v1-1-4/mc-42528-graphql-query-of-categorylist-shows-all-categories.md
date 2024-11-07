---
title: "MC-42528 : la requête GraphQL de categoryList affiche toutes les catégories"
description: Le correctif MC-42528 résout le problème en raison duquel la requête GraphQL de `categoryList` renvoie les catégories affectées et non affectées lorsque la catégorie de navigation d’une catégorie spécifique est définie sur "Refuser". Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 est installé. L’ID de correctif est MC-42528. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528 : la requête GraphQL de categoryList affiche toutes les catégories

Le correctif MC-42528 résout le problème en raison duquel la requête GraphQL de `categoryList` renvoie les catégories affectées et non affectées lorsque la catégorie de navigation d’une catégorie spécifique est définie sur &quot;Refuser&quot;. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4 est installé. L’ID de correctif est MC-42528. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La requête GraphQL de `categoryList` renvoie les catégories affectées et non affectées.

<u>Étapes à reproduire</u> :

1. Créez deux catégories, CAT1 et CAT2, et affectez quelques produits à chaque catégorie.
1. Créez un catalogue partagé privé.
1. Créez un utilisateur de société et affectez-le au catalogue partagé créé.
1. Attribuez CAT1 au catalogue personnalisé et définissez l’autorisation de catégorie sur &quot;Autoriser&quot; la catégorie de navigation pour le groupe de clients du catalogue privé.
1. Définissez l’autorisation de catégorie pour CAT2 sur &quot;Refuser&quot; Catégorie de navigation pour le groupe de clients du catalogue privé.
1. Exécutez la requête GraphQL `categoryList` ou `categories` en tant qu’utilisateur de l’entreprise.

<u>Résultats attendus</u> :

Seul le CAT1 apparaît dans la réponse.

<u>Résultats réels</u> :

Toutes les catégories s’affichent dans la réponse, quelles que soient les autorisations de navigation de la catégorie.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
