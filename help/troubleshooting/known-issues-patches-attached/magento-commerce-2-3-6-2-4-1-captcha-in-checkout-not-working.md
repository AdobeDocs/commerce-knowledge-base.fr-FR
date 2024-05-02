---
title: Adobe Commerce 2.3.6, 2.4.1 CAPTCHA dans le passage en caisse ne fonctionne pas
description: Cet article fournit un correctif pour le problème où la fonctionnalité CAPTCHA pour le passage en caisse ne fonctionne pas comme prévu sur la page Passer une commande lors de l’utilisation de fournisseurs de paiement tiers tels que Paypal Express, Payflow Pro ou CyberSource dans Adobe Commerce.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.1 CAPTCHA dans le passage en caisse ne fonctionne pas

Cet article fournit un correctif pour le problème où la fonctionnalité CAPTCHA pour le passage en caisse ne fonctionne pas comme prévu sur la page Passer une commande lors de l’utilisation de fournisseurs de paiement tiers tels que Paypal Express, Payflow Pro ou CyberSource dans Adobe Commerce.

Ce problème connu est mentionné dans notre documentation destinée aux développeurs :

<u>Pour Adobe Commerce 2.3.6</u>:

* [Notes de mise à jour d’Adobe Commerce 2.3.6 : problèmes connus](https://devdocs.magento.com/guides/v2.3/release-notes/commerce-2-3-6.html#known-issues)
* [Notes de mise à jour de Magento Open Source 2.3.6 : problèmes connus](https://devdocs.magento.com/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>Pour Adobe Commerce 2.4.1</u>:

* [Notes de mise à jour d’Adobe Commerce 2.4.1 : problèmes connus](https://devdocs.magento.com/guides/v2.4/release-notes/commerce-2-4-1.html#known-issues)
* [Notes de mise à jour de Magento Open Source 2.4.1 : problèmes connus](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-1.html#known-issues)

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 et 2.4.1
* Magento Open Source 2.3.6 et 2.4.1

## Problème

<u>Étapes à reproduire</u>

1. Configurez au moins l’un de ces modes de paiement dans Commerce : Paypal Express, Payflow Pro ou CyberSource.
1. Accédez à **Admin > Magasins > Configuration > Clients > Configuration client > CAPTCHA** .
   * Définir **Activation de CAPTCHA sur le storefront** = *Oui* .
   * Sélectionner dans **Forms** : *Passage en caisse/Ordre de placement* , *Connexion* , et *Mot de passe oublié* .
   * Définir **Mode d’affichage** = *Après le nombre de tentatives de connexion* (pour que la variable **Nombre de tentatives infructueuses de connexion** s’affiche).
   * Définir **Nombre de tentatives infructueuses de connexion** = *0* (pour que le captcha fonctionne tout le temps).
1. Sur le front-end, ajoutez un produit au panier et essayez d’effectuer un passage en caisse.
1. Sur la page Informations de paiement, saisissez captcha et essayez d’extraire avec Paypal Express, Payflow Pro ou CyberSource.

<u>Résultat attendu :</u>

La fonction CAPTCHA fonctionne comme prévu.

<u>Résultat réel :</u>

Le message d’erreur s’affiche : *Veuillez fournir le code CAPTCHA et réessayer.*

## Solution

Appliquez l’un des correctifs ci-dessous selon que vous utilisez Adobe Commerce sur site/Adobe Commerce sur l’infrastructure cloud/Magento Open Source 2.3.6 ou 2.4.1.

## Correctifs

Les correctifs sont joints à cet article, disponibles en téléchargement dans les deux `.composer` et `.git` formats.

Pour télécharger un correctif, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur l’un des liens suivants :

<u>Pour Adobe Commerce sur site/Adobe Commerce sur l’infrastructure cloud/Magento Open Source 2.3.6</u> :

* [Correctif du compositeur MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Correctif Git MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>Pour Adobe Commerce sur site/Adobe Commerce sur l’infrastructure cloud/Magento Open Source 2.4.1</u> :

* [Correctif du compositeur MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Correctif Git MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

Ces correctifs ne sont compatibles avec aucune autre version ou édition d’Adobe Commerce ou de Magento Open Source.

## Comment appliquer le correctif

<u>Compositeur</u>

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support pour les instructions de correctif du compositeur.

<u>Correctif Git</u>

Voir la documentation destinée aux développeurs [Application de correctifs : correctifs personnalisés](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) pour obtenir des instructions sur le correctif git pour Adobe Commerce/Magento Open Source.
