---
title: 'MDVA-30599 : customer_is_guest n’est pas défini correctement'
description: Le correctif MDVA-30599 corrige le problème en raison duquel les guillemets d’invité créés à l’aide de l’API sont incorrectement marqués comme guillemets pour les clients connectés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé. Le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599 : customer_is_guest est mal défini

Le correctif MDVA-30599 corrige le problème en raison duquel les guillemets d’invité créés à l’aide de l’API sont incorrectement marqués comme guillemets pour les clients connectés. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé. Le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.0

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les guillemets d’invité créés à l’aide de l’API sont incorrectement marqués comme guillemets pour les clients connectés.

<u>Étapes à reproduire</u> :

1. Sur le storefront Adobe Commerce, ajoutez un produit au panier en tant qu’utilisateur invité.
1. Dans votre base de données Adobe Commerce, recherchez le `quote_id_mask` correspondant.
1. Envoyez une demande d’API à l’interface du référentiel de panier `quoteGuestCartRepositoryV1` pour les paniers d’invités. Vous pouvez le faire via une requête Swagger ou cURL.

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>Résultats attendus</u> :

En réponse, vous obtenez `"customer_is_guest": true`

<u>Résultats réels</u> :

En réponse, vous obtenez `"customer_is_guest": false`

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Autres étapes requises après l’installation du correctif

Le correctif sera efficace pour tous les nouveaux paniers d’invités. Si vous devez corriger les paniers d’invités existants, définissez `quote.customer_is_guest = 1` pour les enregistrements dont `quote.customer_id` est NULL. Vous pouvez exécuter une requête semblable à ce qui suit :

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>Nous vous recommandons vivement de tester la requête dans l’environnement d’évaluation/d’intégration avant de l’exécuter dans Production. Nous vous recommandons également d’effectuer une sauvegarde récente avant toute manipulation avec DB.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
