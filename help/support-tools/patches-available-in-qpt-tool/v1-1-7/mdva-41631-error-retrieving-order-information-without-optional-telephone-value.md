---
title: '''MDVA-41631 : erreur lors de la récupération des informations de commande sans valeur "téléphonique" facultative'
description: Le correctif MDVA-41631 corrige le problème en raison duquel les utilisateurs obtenaient une erreur lors de la récupération des informations de commande sans valeur "téléphonique" facultative via GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631 : erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative

Le correctif MDVA-41631 corrige le problème en raison duquel les utilisateurs obtenaient une erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative via GraphQL. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.7 est installée. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs obtiennent une erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative via GraphQL.

<u>Étapes à reproduire</u>:

1. Accédez à **Magasin** > **Configuration** > **Clients** > **Configuration client** > **Options de nom et d’adresse** > **Afficher le téléphone** et définissez le numéro de téléphone sur facultatif.
1. Passez une commande à l’aide de l’API GraphQL en tant que client connecté.
   * Ne définissez pas le numéro de téléphone lors de la définition des adresses de facturation et de livraison. Suivez les instructions de la section [Tutoriel sur le passage en caisse GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html) dans notre documentation destinée aux développeurs.
1. Récupération de la commande à l’aide de GraphQL [Requête customerOrder](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Résultats attendus</u>:

Les utilisateurs obtiennent des informations sur la commande.

<u>Résultats réels</u>:

Les utilisateurs reçoivent l’erreur suivante : *&quot;message&quot;: &quot;Erreur interne du serveur&quot;,*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
