---
title: Impossible d’enregistrer *contact* comme clé URL
description: Cet article fournit une solution au problème lorsque vous ne pouvez pas enregistrer *contact* en tant que clé URL (par exemple, « /contact ») pour les produits ou les pages CMS. Lorsque vous essayez d’enregistrer la clé URL, vous recevez une erreur indiquant que la clé URL est une URL en double.
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%
---
# Impossible d’enregistrer *contact* comme clé URL

Cet article fournit une solution au problème lorsque vous ne pouvez pas enregistrer *contact* en tant que clé URL (par exemple, « /contact ») pour les produits ou les pages CMS.

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.4.x

## Problème

Vous ne pouvez pas enregistrer un produit ou une page CMS en utilisant le terme *contact* comme clé URL. Lorsque vous essayez d’enregistrer la clé URL, vous recevez une erreur indiquant que la clé URL est une URL en double.

<u>Procédure à suivre </u> :

Créez une page CMS avec *contact* comme clé URL.

<u>Résultat attendu </u> :

La page est enregistrée avec *contact* comme clé URL.

<u>Résultat réel</u> :

Vous ne pouvez pas enregistrer la page. Vous obtenez l’erreur : *La valeur spécifiée dans le champ Clé d’URL générerait une URL qui existe déjà.*

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

Vous ne pouvez pas utiliser le terme *contact* comme clé URL. Vous pouvez toutefois utiliser le terme *contact* associé à une autre lettre ou à un autre numéro (par exemple, *contact1* et *contact2*). Bien que le terme ne doive pas nécessairement être *contact+\&lt;autre nombre ou lettre\>*, il peut s’agir de n’importe quelle chaîne tant que sa longueur ne dépasse pas 255 caractères.

Effectuez les étapes suivantes :

1. Connectez-vous à Commerce Admin.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. Cliquez sur **[!UICONTROL Add URL Rewrite]**.
1. Sélectionnez *[!UICONTROL Custom]* dans la liste déroulante [!UICONTROL Create URL Rewrite] .
   1. Dans la [!UICONTROL Request Path], tapez « contact ». Notez que le [!UICONTROL Request Path] correspond à ce qu’un utilisateur ou une utilisatrice saisit dans le navigateur et que le [!UICONTROL Target Path] correspond à l’emplacement vers lequel il ou elle doit rediriger.
   1. Dans la [!UICONTROL Target Path], saisissez la nouvelle clé URL (par exemple, « contact1 »).
   1. Sélectionnez *[!UICONTROL No]* dans la liste déroulante [!UICONTROL Redirect] .

## Lecture connexe

* [Réécritures d’URL](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite) dans notre guide d’utilisation.
* [Bonnes pratiques SEO](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/seo-overview) dans notre guide de l’utilisateur.
