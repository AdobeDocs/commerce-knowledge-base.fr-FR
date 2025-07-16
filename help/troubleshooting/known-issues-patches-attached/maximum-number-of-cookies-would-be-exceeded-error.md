---
title: Erreur de dépassement du nombre maximal de cookies dans Adobe Commerce
description: Découvrez comment résoudre le problème d’Adobe Commerce en raison duquel une erreur se produit indiquant que le nombre maximal de cookies serait dépassé.
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
exl-id: 5c42ea7a-f023-4d34-8417-bb470efc3b84
source-git-commit: 87e98607ee5e1cc41e4266836fd09531a290725e
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# *Le nombre maximal de cookies serait dépassé* erreur dans Adobe Commerce

Cet article fournit des correctifs pour résoudre l’erreur indiquant *Le nombre maximal de cookies serait dépassé* dans Adobe Commerce.

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 à 2.4.7, avec l’un des correctifs suivants appliqués :

* Correctif MDVA-12304 appliqué à l’aide du [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes)
* [Mise à jour de sécurité disponible pour Adobe Commerce - APSB25-08](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27149)
* [Correctifs cloud pour [!DNL Commerce] 1.1.4](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)

## Problème

Les problèmes liés aux cookies dans Adobe Commerce entraînent l’apparition de l’erreur suivante dans les journaux d’erreurs :

*report.WARNING : impossible d&#39;envoyer le cookie. Le nombre maximal de cookies serait dépassé.*

### Cause

Le problème se produit, car le nombre maximal de cookies autorisés est défini sur *50*.

## Solution

1. Supprimez le correctif MDVA-12304 si vous l’avez appliqué à l’aide de l’[!DNL Quality Patches Tool (QPT)] .

   * Pour Adobe Commerce sur les infrastructures cloud, supprimez le correctif de `.magento.env.yaml`.
   * Pour les installations sur site d’Adobe Commerce, exécutez la commande suivante pour rétablir le correctif :

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. Appliquez les correctifs ci-joints en fonction de votre version d’Adobe Commerce :

   * Pour les versions 2.4.4-p12, 2.4.5-p11, 2.4.6-p9 et 2.4.7-p4, appliquez le correctif [ACSD-64710](assets/acsd-64710_2.4.5-p11.patch.zip).

   * Pour les versions 2.4.4-p13, 2.4.5-p12, 2.4.6-p10, 2.4.7-p5 et 2.4.8, appliquez le correctif [ACSD-65562](assets/acsd-65562_2.4.5-p12.patch.zip).

### Lecture connexe

* [ Application de correctifs ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/apply) dans le guide de mise à niveau d’Adobe Commerce
* [Bonnes pratiques pour distribuer les correctifs Adobe Commerce à grande échelle](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) dans le guide d’implémentation d’Adobe Commerce
* [Notes de mise à jour de la suite d’outils Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) dans le guide Commerce sur le cloud .
