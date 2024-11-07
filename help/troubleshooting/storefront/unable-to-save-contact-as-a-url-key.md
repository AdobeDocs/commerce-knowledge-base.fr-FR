---
title: Impossible d’enregistrer *contact* comme clé URL
description: Cet article fournit une solution au problème lorsque vous ne pouvez pas enregistrer *contact* comme clé d’URL (par exemple, "/contact") pour les produits ou les pages CMS. Lorsque vous essayez d’enregistrer la clé URL, vous recevez une erreur indiquant que la clé URL est une URL en double.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Impossible d&#39;enregistrer *contact* comme clé d&#39;URL

Cet article fournit une solution au problème lorsque vous ne pouvez pas enregistrer *contact* en tant que clé d’URL (par exemple, &quot;/contact&quot;) pour des produits ou des pages CMS.

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.4.x

## Problème

Vous ne pouvez pas enregistrer un produit ou une page CMS à l’aide du terme *contact* comme clé d’URL. Lorsque vous essayez d’enregistrer la clé URL, vous recevez une erreur indiquant que la clé URL est une URL en double.

<u>Étapes à reproduire</u> :

Créez une page CMS avec *contact* comme clé d’URL.

<u>Résultat attendu</u> :

La page est enregistrée avec *contact* comme clé d’URL.

<u>Résultat réel</u> :

Vous ne pouvez pas enregistrer la page. Vous obtenez l’erreur : *La valeur spécifiée dans le champ Clé URL génère une URL qui existe déjà.*

## Cause

*Contact* est un mot réservé défini dans `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## Solution

Vous ne pouvez pas utiliser le terme *contact* comme clé d&#39;URL, mais vous pouvez utiliser le terme *contact* combiné à une autre lettre ou un autre numéro (par exemple, *contact1* et *contact2*). Bien que le terme n’ait pas à être *contact+\&lt;autre nombre ou lettre\>*, le terme peut être n’importe quelle chaîne tant que la longueur ne dépasse pas 255 caractères.

Effectuez les étapes suivantes :

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Cliquez sur **[!UICONTROL Add URL Rewrite]**.
1. Sélectionnez *[!UICONTROL Custom]* dans la liste déroulante [!UICONTROL Create URL Rewrite].
   1. Dans le [!UICONTROL Request Path], saisissez &quot;contact&quot;. Notez que [!UICONTROL Request Path] est ce que l’utilisateur entre dans le navigateur et que [!UICONTROL Target Path] est l’endroit vers lequel il doit rediriger.
   1. Dans le [!UICONTROL Target Path], saisissez la nouvelle clé d’URL (par exemple, &quot;contact1&quot;).
   1. Sélectionnez *[!UICONTROL No]* dans la liste déroulante [!UICONTROL Redirect].

## Lecture connexe

* [URL réécrit](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) dans notre guide d’utilisation.
* [Bonnes pratiques d’optimisation pour les moteurs de recherche](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview) dans notre guide d’utilisation.
