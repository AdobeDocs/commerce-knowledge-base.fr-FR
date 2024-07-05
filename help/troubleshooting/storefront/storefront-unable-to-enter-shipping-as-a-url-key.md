---
title: Impossible d’enregistrer la livraison en tant que clé d’URL
description: Cet article fournit une solution au problème lorsque vous ne pouvez pas enregistrer l’expédition en tant que clé d’URL (_ par exemple, /shipping_) pour les produits ou les pages CMS. Lorsque vous essayez d’enregistrer la clé URL, vous recevez une erreur indiquant que la clé URL est un doublon d’une URL.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 1ce963142a261a17e2b42f79dd567c8484ec5b3e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Enregistrement impossible _shipping_ comme clé d’URL

Cet article fournit une solution au problème lorsque vous ne pouvez pas enregistrer l’expédition comme clé d’URL (_par exemple, /shipping_) pour les produits ou les pages CMS. Lorsque vous essayez d’enregistrer la clé URL, vous recevez une erreur indiquant que la clé URL est une URL en double.

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.4.x

## Problème

Vous ne pouvez pas enregistrer une page CMS avec le terme . _shipping_ dans la clé URL.

<u>Étapes à reproduire</u>:

Créez un **[!UICONTROL CMS page]** avec la clé URL comme _shipping_.

<u>Résultat attendu</u>:

La page enregistre avec _shipping_ comme clé d’URL.

<u>Résultat réel</u>:

Vous ne pouvez pas enregistrer lorsque cette erreur se produit :
*La valeur spécifiée dans le champ Clé URL génère une URL qui existe déjà.*

## Cause

L’expédition est un mot réservé défini dans `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## Solution

Vous ne pouvez pas utiliser le terme _shipping_ dans votre clé d’URL ; toutefois, vous pouvez utiliser le terme _shipping_ combiné avec une autre lettre ou un autre nombre (_Par exemple, shipping1 et shipping2_).

Bien que le terme n’ait pas à être _shipping_+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - le terme peut être n’importe quelle chaîne tant que la longueur ne dépasse pas *255* caractères.

## Effectuez les étapes suivantes :

1. Connectez-vous à l’administrateur Adobe Commerce.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Cliquez sur **[!UICONTROL Add URL Rewrite]**.
1. Sélectionner **[!UICONTROL Custom]** dans le **[!UICONTROL Create URL Rewrite]** menu déroulant.
   1. Saisissez le [!UICONTROL Request Path] as **_shipping_**.
   1. Dans le **[!UICONTROL Target Path]**, saisissez la nouvelle clé d’URL (_Par exemple, &quot;shipping1&quot;_).
   1. Sélectionner **[!UICONTROL No]** dans le **[!UICONTROL Redirect]** menu déroulant.


      (**Remarque**: le chemin d’accès à la requête est ce que l’utilisateur saisit dans le navigateur et le chemin d’accès cible est l’endroit où il doit rediriger.)

En outre, évitez d’utiliser ces mots-clés étiquetés comme *réservé* mots-clés qui font apparaître la même exception. L’utilisation de l’un de ces mots-clés répertoriés ci-dessous comme valeur de clé d’URL entraîne l’affichage de la même erreur.


```
"admin"
"adminAnalytics"
"analytics"
"api"
"backup"
"bulk"
"captcha"
"catalog"
"catalogsearch"
"checkout"
"cms"
"contact"
"cookie"
"customer"
"directory"
"downloadable"
"giftmessage"
"groupedProduct"
"indexer"
"instantpurchase"
"loginascustomer"
"marketplace"
"mui"
"multishipping"
"newsletter"
"oauth"
"paypal"
"persistent"
"productalert"
"releaseNotification"
"reports"
"review"
"robots"
"rss"
"sales"
"search"
"security"
"sendfriend"
"shipping"
"stores"
"swagger"
"swatches"
"tax"
"theme"
"translation"
"vault"
"wishlist"
```

## Lecture connexe

* [URL Rewrites](https://docs.magento.com/user-guide/marketing/url-rewrite.html) dans notre Guide de l’utilisateur Marchandisage et promotions .
* [Bonnes pratiques relatives au référencement](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) dans notre Guide de l’utilisateur Marchandisage et promotions .
