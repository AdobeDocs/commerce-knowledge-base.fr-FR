---
title: Impossible d’enregistrer "shipping" comme clé d’URL
description: Cet article fournit une solution au problème lorsque vous ne pouvez pas enregistrer "expédition" comme clé d’URL (par exemple, "/shipping") pour les produits ou les pages CMS. Lorsque vous essayez d’enregistrer la clé URL, vous recevez une erreur indiquant que la clé URL est une URL en double.
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Impossible d’enregistrer &quot;shipping&quot; comme clé d’URL

Cet article fournit une solution au problème lorsque vous ne pouvez pas enregistrer &quot;expédition&quot; comme clé d’URL (par exemple, &quot;/shipping&quot;) pour les produits ou les pages CMS. Lorsque vous essayez d’enregistrer la clé URL, vous recevez une erreur indiquant que la clé URL est une URL en double.

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.4.x

## Problème

Vous ne pouvez pas enregistrer une page CMS avec le terme &quot;livraison&quot; dans la clé URL.

<u>Étapes à reproduire</u>:

Créez une page CMS avec la clé URL comme &quot;livraison&quot;.

<u>Résultat attendu</u>:

La page est enregistrée avec &quot;livraison&quot; dans la clé URL.

<u>Résultat réel</u>:

Vous ne pouvez pas enregistrer et une erreur s’affiche : *La valeur spécifiée dans le champ Clé URL génère une URL qui existe déjà.*

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

Vous ne pouvez pas utiliser le terme &quot;expédition&quot; dans votre clé URL, mais vous pouvez utiliser le terme &quot;expédition&quot; combiné à une autre lettre ou un autre numéro (par exemple, &quot;expédition1&quot; et &quot;expédition2&quot;). Bien que le terme ne doive pas nécessairement être &quot;expédition&quot;+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;> - le terme peut être n’importe quelle chaîne tant que la longueur ne dépasse pas 255 caractères.

Effectuez les étapes suivantes :

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Marketing** > SEO &amp; Search > **URL Rewrites**.
1. Cliquez sur **Ajouter une réécriture d’URL**.
1. Sélectionner *Personnalisé* dans la liste déroulante Créer une réécriture d’URL .
   1. Saisissez dans le Chemin de la demande &quot;expédition&quot;. Remarque : le chemin d’accès à la requête est ce que l’utilisateur saisit dans le navigateur et le chemin d’accès cible est l’endroit vers lequel il doit rediriger.
   1. Saisissez dans le chemin cible la nouvelle clé d’URL (par exemple, &quot;shipping1&quot;).
   1. Sélectionner **Non** dans la liste déroulante Redirection .

## Lecture connexe

* [URL Rewrites](https://docs.magento.com/user-guide/marketing/url-rewrite.html) dans notre guide d’utilisation.
* [Bonnes pratiques relatives au référencement](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) dans notre guide d’utilisation.
