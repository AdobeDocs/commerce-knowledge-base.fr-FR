---
title: "MDVA-43178 : le jeton client de la boutique personnalisée ne peut pas être récupéré dans GraphQL"
description: Le correctif MDVA-43178 corrige le problème en raison duquel le jeton client d’un magasin personnalisé ne peut pas être récupéré dans GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-43178. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: b2a8bf96-7534-41d2-b83b-58d8e0b6d076
feature: GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-43178 : le jeton client de la boutique personnalisée ne peut pas être récupéré dans GraphQL

Le correctif MDVA-43178 corrige le problème en raison duquel le jeton client d’un magasin personnalisé ne peut pas être récupéré dans GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-43178. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le jeton client d’un magasin personnalisé ne peut pas être récupéré dans GraphQL.

<u>Étapes à reproduire</u> :

1. Créez deux vues de magasin pour le magasin par défaut.
1. Créez un site Web, un magasin et un magasin. Nommez cette vue de magasin &quot;test3&quot;.
1. Créez un client pour le nouveau site web.
1. Générer un jeton d’administration API :

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    {
      "username": "login",
      "password": "password"
    }
    </code>
    </pre>

1. Envoyez GraphQL pour récupérer le jeton client en tant qu’administrateur, utilisez le jeton d’administration pour l’autorisation, avec &quot;store&quot; = &quot;test3&quot; dans l’en-tête :

   <pre>
    <customer_email>
      </pre>

<u>Résultats attendus</u> :

Le jeton client est généré.

<u>Résultats réels</u> :

Le jeton client n’est pas généré. Les commerçants obtiennent *l’e-mail du client fourni n’existe pas* en réponse.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
