---
title: '''[!DNL FedEx] Migration de l’intégration de la méthode d’expédition de SOAP vers l’API RESTful'
promoted: true
description: Appliquez un correctif pour traiter la variable [!DNL FedEx] migration de l’intégration des méthodes de livraison de l’API SOAP vers l’API RESTful pour Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] Migration de l’intégration des méthodes d’expédition de SOAP vers l’API RESTful

Cet article fournit un correctif pour résoudre les problèmes liés à la fonction [!DNL FedEx] migration de l’intégration des méthodes de livraison de l’API SOAP vers l’API RESTful pour Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

[!DNL FedEx Web Services] Le suivi, la validation des adresses et la validation des codes postaux des services web de définition des langues (WSDLS) seront retirés le 15 mai 2024. SOAP [!DNL FedEx Web Services] est dans un conteneur de développement et a été remplacé par [!DNL FedEx] API RESTFUL. Pour en savoir plus, voir [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Ce changement a une incidence sur notre [!DNL FedEx] l’implémentation de l’intégration des méthodes d’expédition dans Adobe Commerce. Nous devons corriger notre implémentation actuelle et migrer des API SOAP obsolètes vers les dernières [!DNL FedEx] API RESTFUL.

À compter du 15 mai 2024, les clients Adobe Commerce ne pourront plus utiliser notre [!DNL FedEx] intégration de la méthode d’expédition. Adobe publie donc ce correctif qui permet aux clients Adobe Commerce 2.4.4+ d’utiliser la dernière version [!DNL FedEx] API RESTFUL au lieu des API SOAP obsolètes.


## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud et sur site, et Magento Open Source :

* 2.4.4-p4
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## Cause

La variable [!DNL FedEx] leurs API SOAP ont été abandonnées et remplacées par les API RESTful à la place. Voir [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

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

Décompressez le fichier et reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) pour obtenir des instructions.

## Comment déterminer si les correctifs ont été appliqués

Étant donné qu’il n’est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif a bien été appliqué. Utilise (exemple : *AC-9363*) comme correctif à vérifier.

<u>Pour ce faire, procédez comme suit :</u>:

1. [Installez le [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Exécutez la commande :

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Vous devriez voir une sortie similaire à celle-ci, où AC-9363 renvoie la valeur *Appliqué* status :

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
