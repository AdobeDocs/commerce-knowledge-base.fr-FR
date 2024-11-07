---
title: Mise à niveau vers le schéma DHL v10 pour continuer à proposer l’expédition DHL
description: Cet article fournit une solution permettant aux commerçants de continuer à proposer l’expédition DHL après la mise à niveau du schéma DHL 6.2 en décembre 2022, en effectuant une mise à niveau vers le schéma 10.0 ou en appliquant le correctif AC-3023.
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Mise à niveau vers la version 10.0 du schéma DHL pour continuer à proposer l’expédition DHL

Cet article fournit une solution permettant aux commerçants de continuer à proposer l’expédition DHL après la mise hors service du schéma DHL version 6.2 à la fin de décembre 2022.

## Produits et versions concernés

* Adobe Commerce 2.4.5 et versions antérieures, toutes les méthodes de déploiement.

## Problème

En août 2022, nous avons publié la [mise à niveau du schéma DHL version 6.2. avec un correctif](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) pour que les commerçants continuent à proposer la livraison DHL. DHL introduit à nouveau un nouveau schéma - version 10.0 - en octobre 2022, et la version précédente (schéma 6.2) sera abandonnée fin décembre 2022. L’intégration DHL d’Adobe Commerce 2.4.5 et versions antérieures ne prend en charge que la version 6.2.

## Solution

Adobe Commerce 2.4.5-p1 et 2.4.4-p2, publiés en octobre 2022, contient la nouvelle version 10.0 du schéma DHL. Ainsi, les commerçants qui effectuent une mise à niveau vers 2.4.5-p1 et 2.4.4-p2 n’ont rien à faire pour continuer à offrir les envois DHL. Nous encourageons tous les commerçants à effectuer une mise à niveau vers les versions 2.4.5-p1 et 2.4.4-p2 avant la mise hors service du schéma DHL 6.2. fin décembre 2022.

Les commerçants qui ne souhaitent pas effectuer la mise à niveau vers les versions 2.4.5-p1 et 2.4.4-p2 devront appliquer un correctif s’ils souhaitent continuer à proposer l’expédition DHL après décembre 2022.

## Correctif

L’ID de correctif est AC-3023 et il est disponible dans la version 1.1.2 de [!DNL Quality Patches Tool].

Reportez-vous aux liens suivants sur l’utilisation de [!DNL Quality Patches Tool] et installez les correctifs en fonction de vos méthodes de déploiement :

* Adobe Commerce sur site et Magento Open Source : [Outils de correctifs de qualité > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans Adobe Experience League.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

**Le correctif s’applique aux versions Adobe Commerce suivantes (toutes les méthodes de déploiement) :**

* 2.3.7, 2.4.0, 2.4.1, 2.4.2, 2.4.3, 2.4.3, 2.4.3-p2, 2.4.3-p3, 2.4.4

## Liens utiles

* [[!DNL Quality Patches Tool] > Notes de mise à jour](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) dans Adobe Experience League.

* [[!DNL Quality Patches Tool] : recherchez des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans Adobe Experience League.

## Lecture connexe

* [Appliquez un correctif pour continuer à proposer DHL comme transporteur ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) dans notre base de connaissances de support.

* [Carrières de livraison > DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html) dans notre guide d’utilisation.
* [Référence de configuration > Ventes > Méthodes de diffusion](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html) dans notre guide d’utilisation.
