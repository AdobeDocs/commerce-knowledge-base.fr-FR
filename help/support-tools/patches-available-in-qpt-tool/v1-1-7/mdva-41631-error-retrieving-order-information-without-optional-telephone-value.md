---
title: 'MDVA-41631 : erreur lors de la récupération des informations de commande sans valeur "téléphonique" facultative'
description: Le correctif MDVA-41631 corrige le problème en raison duquel les utilisateurs obtenaient une erreur lors de la récupération des informations de commande sans valeur "téléphonique" facultative via GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631 : erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative

Le correctif MDVA-41631 corrige le problème en raison duquel les utilisateurs obtenaient une erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative via GraphQL. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs obtiennent une erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative via GraphQL.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasin** > **Configuration** > **Clients** > **Configuration client** > **Options de nom et d’adresse** > **Afficher le numéro de téléphone** et définissez le numéro de téléphone comme facultatif.
1. Passez une commande à l’aide de l’API GraphQL en tant que client connecté.
   * Ne définissez pas le numéro de téléphone lors de la définition des adresses de facturation et de livraison. Suivez les instructions du [tutoriel sur le passage en caisse de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) dans notre documentation destinée aux développeurs.
1. Récupérez la commande à l’aide de la requête GraphQL [customerCommandes](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/).

<pre>
<code class="language-graphql">
&lbrace;
  customer &lbrace;
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}})&lbrace;
        items&lbrace;
          billing_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
shipping_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
        &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Résultats attendus</u> :

Les utilisateurs obtiennent des informations sur la commande.

<u>Résultats réels</u> :

Les utilisateurs reçoivent l’erreur suivante : *&quot;message&quot;: &quot;Erreur interne du serveur&quot;,*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
