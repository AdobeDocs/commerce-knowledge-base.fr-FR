---
title: '[!DNL USPS] La méthode de livraison Ground Advantage prend en charge le correctif pour AC-9182'
promoted: true
description: Appliquez un correctif pour traiter la variable [!DNL USPS] La méthode d’expédition Ground Advantage émet AC-9182 pour Adobe Commerce 2.4.4 - 2.4.6-p2.
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] La méthode de livraison Ground Advantage prend en charge le correctif pour AC-9182.

Cet article fournit un correctif pour résoudre le problème AC-9182 pour le nouveau **[!DNL USPS]Avantages au sol** méthode d’expédition dans Adobe Commerce 2.4.4 - 2.4.6-p2.

Le 9 juillet 2023, The United States Postal Service ([!DNL USPS]) a publié une nouvelle méthode d’expédition, [[!DNL USPS] Avantages au sol](https://www.usps.com/ship/ground-advantage.htm).

Cette nouvelle méthode d’expédition remplace les trois principales méthodes d’expédition actuelles :

* [!DNL USPS] Vente au détail au sol
* [!DNL USPS] Service de package de première classe
* [!DNL USPS] Parcel Select Ground

[[!DNL USPS] annonce](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works) à compter du 30 septembre 2023, ces trois méthodes d’expédition seront abandonnées et tous les clients devront utiliser la nouvelle **[!DNL USPS]Avantages au sol** à la place.

Ainsi, après le 30 septembre 2023, tous les marchands Adobe Commerce qui utilisent la méthode de livraison USPS ne pourront pas obtenir de tarifs de livraison à partir de [!DNL USPS] en utilisant ces trois méthodes d’expédition héritées.

Ce problème sera corrigé dans le cadre des prochaines versions des correctifs uniquement de sécurité d’octobre 2023, dans les versions 2.4.6-p3, 2.4.5-p5 et 2.4.4-p6.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud et sur site, et Magento Open Source :

* 2.4.4
* 2.4.4-p1
* 2.4.4-p2
* 2.4.4-p3
* 2.4.4-p4
* 2.4.4-p5
* 2.4.5
* 2.4.5-p1
* 2.4.5-p2
* 2.4.5-p3
* 2.4.5-p4
* 2.4.6
* 2.4.6-p1
* 2.4.6-p2

## Cause

La variable [!DNL USPS] made an [!DNL API] mettre à jour.

## Solution

Pour résoudre le problème dans les versions 2.4.4, 2.4.5 et 2.4.6, vous devez appliquer le correctif AC-9182 ci-dessous.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, cliquez sur le lien suivant :

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## Comment appliquer le correctif

Décompressez le fichier et reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) pour obtenir des instructions.

## Comment déterminer si les correctifs ont été appliqués

Étant donné qu’il n’est pas possible de vérifier facilement si le problème a été résolu, vous pouvez vérifier si le correctif AC-9182 a bien été appliqué.

<u>Pour ce faire, procédez comme suit :</u>:

1. [Installez le [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Exécutez la commande :

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. Vous devriez voir une sortie similaire à celle-ci, où AC-9182 renvoie la valeur *Appliqué* status :

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
