---
title: Migration de l’intégration de la méthode d’expédition [!DNL FedEx] de SOAP vers l’API RESTful
promoted: true
description: Appliquez un correctif pour gérer la migration  [!DNL FedEx]  l’intégration de la méthode d’expédition de SOAP vers l’API RESTful pour Adobe Commerce 2.4.4-p4 - 2.4.6-pX.
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7a54e992e365238ec7c764225a31cd3b6b8ad019
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# Migration de l’intégration de la méthode d’expédition [!DNL FedEx] de SOAP vers l’API RESTful

>[!WARNING]
>
>Utilisez le correctif ACSD-61622 de la version 1.1.57 de [!DNL Quality Patches Tool] (QPT) au lieu du correctif fourni précédemment. Le nouveau correctif est compatible avec les versions Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p1 à 2.4.6-p8. Il peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool].
>
>Pour plus d’informations, reportez-vous à l’article [correctif ACSD-61622](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-61622-fedex-account-specific-rates-missing-from-response) dans notre guide des outils Adobe Commerce.

>[!WARNING]
>
>Avant d’installer le nouveau correctif, vous devez désinstaller le correctif précédent fourni dans cet article. Pour obtenir des instructions sur la désinstallation des correctifs, reportez-vous à la section [Rétablir un correctif personnalisé](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches#revert-a-custom-patch) de notre guide d’utilisation.


Cet article fournit un correctif pour résoudre les problèmes de migration de l’intégration de la méthode d’expédition [!DNL FedEx] de SOAP vers l’API RESTful pour Adobe Commerce 2.4.4-p4 - 2.4.6-pX.

Le suivi [!DNL FedEx Web Services], la validation des adresses et la validation des codes postaux Web Services Definition Languages (WSDLS) ont été retirés le 15 mai 2024. Le [!DNL FedEx Web Services] basé sur SOAP est en cours de développement et a été remplacé par [!DNL FedEx] API RESTFUL. Pour en savoir plus, voir [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

Cette modification a un impact sur notre implémentation actuelle de l’intégration de la méthode d’expédition [!DNL FedEx] dans Adobe Commerce et nécessite que nous corrigions notre implémentation actuelle et que nous migrions des API SOAP obsolètes vers les dernières API RESTFUL [!DNL FedEx].

À compter du 15 mai 2024, les clients Adobe Commerce ne pourront plus utiliser notre intégration de méthode d’expédition [!DNL FedEx] actuelle. Par conséquent, Adobe publie ce correctif qui permet aux clients Adobe Commerce 2.4.4+ d’utiliser les dernières API RESTFUL [!DNL FedEx] au lieu des API SOAP obsolètes.


## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud et sur site, et Magento Open Source :

* 2.4.4-p4
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6-pX

## Cause

Les [!DNL FedEx] ont abandonné leurs API basées sur SOAP et les ont remplacées par des API RESTful. Pour plus d&#39;informations, consultez la section [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## Solution

Utilisez les correctifs ci-joints, en fonction de la version d’Adobe Commerce ou du Magento Open Source :

Pour résoudre ce problème dans les versions 2.4.4+, 2.4.5+ et 2.4.6+, vous devez appliquer le correctif correspondant à votre version d’Adobe Commerce/Magento Open Source ci-dessous.

## Patch

Utilisez les correctifs ci-joints, en fonction de la version d’Adobe Commerce ou du Magento Open Source :

### Pour les versions 2.4.4 à p4 :

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### Pour les versions 2.4.5, 2.4.5-pX :

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### Pour les versions 2.4.6 et 2.4.6-pX :


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## Application du correctif

Décompressez le fichier et consultez [Comment appliquer un correctif de compositeur fourni par Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) dans notre base de connaissances du support pour obtenir des instructions.

## Comment déterminer si les patchs ont été appliqués

Comme il n’est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif a bien été appliqué. Cette méthode utilise (exemple : *AC-9363*) comme correctif à vérifier.

<u>Pour ce faire, procédez comme suit </u> :

1. [Installez le  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Exécutez la commande :

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. Vous devriez voir une sortie similaire à celle-ci, où AC-9363 renvoie le statut *Appliqué* :

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
