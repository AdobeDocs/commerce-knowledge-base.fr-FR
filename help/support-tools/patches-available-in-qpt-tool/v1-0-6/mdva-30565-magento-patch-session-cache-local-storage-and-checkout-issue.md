---
title: "MDVA-30565 : problème de stockage local et de passage en caisse du cache de session"
description: Le correctif MDVA-30565 résout le problème avec le stockage local et l’extraction du cache de session. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé.
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565 : problème de stockage local et de passage en caisse du cache de session

Le correctif MDVA-30565 résout le problème avec le stockage local et l’extraction du cache de session. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.6 est installée.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les articles de panier sont toujours visibles sur la page du panier lorsqu’une session client expire. Cela entraîne une erreur de méthode d’expédition d’estimation lorsqu’aucune méthode d’expédition n’est disponible pour le passage en caisse des invités.

<u>Étapes à reproduire</u>:

1. Activez le panier persistant dans l’administrateur Commerce. (**Activer la persistance** = &quot;*Oui*&quot;)
1. Connectez-vous en tant que client en front-end. Cela crée la variable `persistent_shopping_cart` et lance une session persistante.
1. Ajoutez un produit dans le panier.
1. Patientez jusqu’à ce que la session front-end soit expirée ou supprimez la variable `PHPSESSID` du cookie.
1. Vous êtes désormais un utilisateur invité, mais si vous accédez au panier, vous pouvez toujours voir le produit qui a été ajouté en tant que client connecté.
1. Supprimez le produit du panier et le panier est désormais vide. Vous pouvez voir qu’Adobe Commerce supprime la variable `persistent_shopping_cart` dans cet événement.
1. Ajoutez un nouveau produit dans le panier, puis accédez à la page du panier.
1. Désormais, dans la console du navigateur, elle s’affiche. `V1/guest-carts/4/estimate-shipping-methods` request renvoie désormais une réponse 404 avec un message `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>Résultats attendus</u>:

La requête de méthode d’expédition d’estimation renvoie les résultats corrects.

<u>Résultats réels</u>:

La demande de méthode d’expédition d’estimation échoue avec une erreur du type : &quot;*Désolé, aucun guillemet n&#39;est disponible pour cette commande pour le moment.*&quot;

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
