---
title: '[!DNL FedEx] Migration de l’intégration de la méthode d’expédition de SOAP à l’API RESTful'
promoted: true
description: Appliquez un correctif pour gérer la migration de l’intégration de la méthode d’expédition de SOAP à l’API RESTful pour Adobe Commerce 2.4.4-p4 - 2.4.6-pX. [!DNL FedEx]
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Migration de l’intégration de la méthode d’expédition [!DNL FedEx] de SOAP vers l’API RESTful

Cet article fournit un correctif pour résoudre les problèmes liés à la migration de l’intégration de la méthode de livraison [!DNL FedEx] de SOAP à l’API RESTful pour Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

[!DNL FedEx Web Services] Le suivi, la validation des adresses et la validation des codes postaux des langues de définition des services web (WSDLS) seront abandonnés le 15 mai 2024. Le fichier [!DNL FedEx Web Services] basé sur SOAP est en conteneur de développement et a été remplacé par les API RESTFUL [!DNL FedEx]. Pour en savoir plus, voir [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Cette modification a un impact sur l’implémentation actuelle de l’intégration des méthodes d’expédition [!DNL FedEx] dans Adobe Commerce et nécessite que nous corrigions notre implémentation actuelle et que nous migrions des API SOAP obsolètes vers les dernières API RESTFUL [!DNL FedEx].

À compter du 15 mai 2024, les clients Adobe Commerce ne pourront plus utiliser l’intégration de notre méthode d’expédition [!DNL FedEx] actuelle. Par conséquent, Adobe publie ce correctif qui permet aux clients Adobe Commerce 2.4.4+ d’utiliser les dernières API RESTFUL [!DNL FedEx] au lieu des API SOAP obsolètes.


## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud et sur site, et Magento Open Source :

* 2.4.4-p4
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## Cause

Les [!DNL FedEx] ont abandonné leurs API SOAP et les ont remplacées par des API RESTful à la place. Voir [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## Solution

Utilisez les correctifs ci-joint suivants, en fonction de votre version d’Adobe Commerce/de Magento Open Source :

Pour résoudre le problème dans les versions 2.4.4+, 2.4.5+ et 2.4.6+, vous devez appliquer le correctif correspondant à votre version d’Adobe Commerce/Magento Open Source ci-dessous.

## Correctif

Utilisez les correctifs ci-joint suivants, en fonction de votre version d’Adobe Commerce/de Magento Open Source :

### Pour les versions 2.4.4-p4 :

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### Pour les versions 2.4.5, 2.4.5-pX :

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### Pour les versions 2.4.6, 2.4.6-pX :


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## Comment appliquer le correctif

Décompressez le fichier et reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) dans notre base de connaissances de support pour obtenir des instructions.

## Comment déterminer si les correctifs ont été appliqués

Étant donné qu’il n’est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif a bien été appliqué. Cela utilise (exemple : *AC-9363*) comme correctif à vérifier.

<u>Pour ce faire, procédez comme suit</u> :

1. [Installez le  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Exécutez la commande :

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Vous devriez voir une sortie similaire à celle-ci, où AC-9363 renvoie l’état *Appliqué* :

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
