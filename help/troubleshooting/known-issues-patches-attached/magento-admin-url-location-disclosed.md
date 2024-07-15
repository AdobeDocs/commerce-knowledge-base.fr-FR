---
title: Emplacement de l’URL d’administration Adobe Commerce divulgué
description: Cet article fournit un correctif pour le problème de sécurité Adobe Commerce en raison duquel l’emplacement URL du panneau d’administration peut être divulgué. Connaître l’emplacement de l’URL peut faciliter l’automatisation des attaques.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Emplacement de l’URL d’administration Adobe Commerce divulgué

Cet article fournit un correctif pour le problème de sécurité Adobe Commerce en raison duquel l’emplacement URL du panneau d’administration peut être divulgué. Connaître l’emplacement de l’URL peut faciliter l’automatisation des attaques.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.X.X
* Adobe Commerce On-Premise 2.X.X
* Magento Open Source 2.X.X

## Problème

Un problème a été découvert dans Magento Open Source et Adobe Commerce qui peut être utilisé pour révéler l’emplacement de l’URL du panneau d’administration. Bien qu’il n’y ait actuellement aucune raison de croire que ce problème conduirait directement à un compromis, sachant que l’emplacement de l’URL pourrait faciliter l’automatisation des attaques.

## Solution

Pour résoudre le problème, appliquez le correctif joint à cet article. Pour le télécharger, cliquez sur le lien suivant :

* Téléchargez [PRODSECBUG-2432\_EE\_2.1.17\_compositeur.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) - pour les versions 2.1.13-2.1.17, Adobe Commerce, Magento Open Source
* Téléchargez [PRODSECBUG-2432\_EE\_2.2.8\_compositeur.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) - pour les versions 2.2.0-2.2.8, toutes les éditions
* Téléchargez [PRODSECBUG-2432\_EE\_2.3.1\_compositeur.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) - pour les versions 2.3.0-2.3.1, toutes les éditions

Si vous ne voyez pas de correctif pour votre produit/version, mettez à niveau vers la dernière version de sécurité, puis appliquez le correctif.

Adobe recommande vivement d&#39;appliquer le correctif dès que possible, même si vous n&#39;avez rencontré aucun symptôme d&#39;une attaque.

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Autres recommandations de sécurité

Adobe recommande également vivement aux commerçants de déployer des outils pour sécuriser leur panneau d’administration, notamment l’authentification à deux facteurs, le VPN, l’Place sur la liste autorisée IP, etc. Pour plus d’informations, consultez les blogs et la documentation suivants :

* [5 Actions immédiates vers Protect contre les attaques brutales de la force](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect Your Magento Installation Password Guider New Update](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [ Bonnes pratiques de sécurité ](https://magento.com/security/best-practices/security-best-practices)
* Ajout et configuration de l’authentification à deux facteurs dans Adobe Commerce pour [2.3.x](https://docs.magento.com/user-guide/v2.3/stores/security-two-factor-authentication.html) et [2.4.x](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html)
