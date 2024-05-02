---
title: Correctif d’erreur fatale PHP de la mise à niveau Adobe Commerce 2.4.3, 2.3.7-p1
description: "Cet article fournit un correctif pour le moment où les commerçants tentent de mettre à niveau vers Adobe Commerce (toutes les méthodes de déploiement) ou Magento Open Source 2.4.3 ou 2.3.7-p1, l’erreur suivante s’affiche :"
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Correctif d’erreur fatale PHP de la mise à niveau Adobe Commerce 2.4.3, 2.3.7-p1

Cet article fournit un correctif lorsque les commerçants tentent de mettre à niveau vers Adobe Commerce (toutes les méthodes de déploiement) ou Magento Open Source 2.4.3 ou 2.3.7-p1, ils voient l’erreur suivante :

*Erreur fatale PHP : erreur non interceptée : appel à une fonction non définie Magento\Framework\Filesystem\Directory\str_contains() dans &lt;...>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

Le problème sera corrigé dans le cadre des versions 2.4.4, 2.4.3-p1 et 2.3.7-p2.

## Versions et produits concernés

* Adobe Commerce (toutes les méthodes de déploiement) lors de la mise à niveau vers la version 2.3.7-p1 ou 2.4.3.
* Magento Open Source lors de la mise à niveau vers 2.3.7-p1 ou 2.4.3.

## Problème

Le problème est dû aux nouvelles versions d’Adobe Commerce 2.4.3 et 2.3.7-p1 utilisant uniquement la fonction PHP 8. `str_contains`. Adobe Commerce 2.4.3 et 2.3.7-p1 sont uniquement compatibles avec PHP 7.4. Cette fonction ne peut donc pas être utilisée.

<u>Étapes à reproduire</u> :

Tentative de mise à niveau vers Adobe Commerce 2.4.3 ou 2.3.7-p1.

<u>Résultat attendu :</u>

Mise à niveau réussie.

<u>Résultat réel :</u>

erreur fatale PHP.

## Solution

Pour pallier ce problème, exécutez la commande suivante dans l’interface de ligne de commande/le terminal : `composer require symfony/polyfill-php80` à partir du dossier racine du Magento ou installez un correctif de compositeur.

Pour résoudre le problème de la version 2.4.3, Adobe Commerce (toutes les méthodes de déploiement) et les marchands Magento Open Sources doivent appliquer un correctif :

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Pour résoudre le problème pour 2.3.7-p1, Adobe Commerce (toutes les méthodes de déploiement) et les marchands Magento Open Sources doivent appliquer un correctif :

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Magento](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Lecture connexe

GitHub [Commande PHP 8 non prise en charge dans Magento 2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)
