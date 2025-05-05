---
title: 'MDVA-44147 : la demande GraphQL ne renvoie pas de listes de demandes'
description: Le correctif MDVA-44147 corrige le problème en raison duquel la demande GraphQL ne renvoie pas de listes de demandes. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID du correctif est MDVA-44147. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
exl-id: c7a526f2-638c-4172-8750-aa076724851a
feature: B2B, GraphQL
role: Admin
source-git-commit: aedf869e96ce6bcbf538805dd6d14d31db8c2e02
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-44147 : la demande GraphQL ne renvoie pas de listes de demandes

Le correctif MDVA-44147 corrige le problème en raison duquel la demande GraphQL ne renvoie pas de listes de demandes. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID du correctif est MDVA-44147. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La demande GraphQL ne renvoie pas de listes de demandes d&#39;approvisionnement.

<u>Procédure à suivre </u> :

1. Accédez à **Magasin** > **Paramètres** > **Configuration** > **Général** > **Fonctionnalités B2B** et activez la liste des demandes d’approvisionnement.
1. Connectez-vous en tant que client et ajoutez un produit à la [Liste des demandes internes](https://experienceleague.adobe.com/fr/docs/commerce-admin/b2b/requisition-lists/requisition-lists).
1. Créez un [jeton client](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/).

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) &lbrace;
          token
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. Utilisez la requête suivante pour récupérer toutes les listes de demandes du client. Utilisez l’en-tête **Authorization** avec la valeur `Bearer <customer_token>`. Pour plus d’informations, reportez-vous à l’article [Requête client](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/customer/) dans la documentation destinée aux développeurs.

   Requête :

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   Réponse :

   <pre>
    <code class="language-graphql">
    &lbrace;
      "data": &lbrace;
        "customer": &lbrace;
          "requisition_lists": &lbrace;
            "items": &lbrack;
            &lbrace;
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": &lbrace;
                "items": &lbrack;
                &lbrace;
                  "uid": "MQ==",
                  "product": &lbrace;
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    &rbrace;,
                    "quantity": 1
                  &rbrace;
                  &rbrack;,
                  "total_pages": 1
                &rbrace;
              &rbrace;
              &rbrack;,
              "total_count": 1
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

1. Copiez l’UID de n’importe quel élément de la liste renvoyée (MQ==) et utilisez la requête suivante pour obtenir la liste filtrée par UID.

   <pre>
    <code class="language-graphql">
    query &lbrace;
      customer &lbrace;
        requisition_lists(
          pageSize: 20,
          filter: &lbrace;
            uids: &lbrace;
              eq: "MQ=="
            &rbrace;
          &rbrace;
          ) &lbrace;
            items &lbrace;
              uid
              name
              description
              items(pageSize: 20) &lbrace;
                items &lbrace;
                  uid
                  product &lbrace;
                    uid
                    name
                    sku
                    __typename
                  &rbrace;
                  quantity
                &rbrace;
                total_pages
              &rbrace;
            &rbrace;
            total_count
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

<u>Résultats attendus</u> :

Un résultat est renvoyé.

<u>Résultats réels</u> :

Aucun résultat n’est renvoyé.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-Premise : [Guide de mise à jour logicielle > Application de correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs et développeuses.

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans notre base de connaissances d’assistance.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances du support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans notre documentation destinée aux développeurs et développeuses.
