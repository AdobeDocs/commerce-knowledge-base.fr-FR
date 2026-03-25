---
title: Mise à niveau d’Adobe Commerce 2.4.3, 2.3.7-p1 PHP Erreur fatale Correctif
description: 'Cet article fournit un correctif pour le moment où les commerçants tentent d’effectuer une mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement) ou Magento Open Source 2.4.3 ou 2.3.7-p1, ils voient l’erreur suivante :'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Mise à niveau d’Adobe Commerce 2.4.3, 2.3.7-p1 PHP Erreur fatale Correctif

Cet article fournit un correctif pour le moment où les commerçants tentent d’effectuer une mise à niveau vers Adobe Commerce (toutes les méthodes de déploiement) ou Magento Open Source 2.4.3 ou 2.3.7-p1, ils voient l’erreur suivante :

*Erreur fatale PHP : erreur non trouvée : appel de la fonction non définie Magento\Framework\Filesystem\Directory\str_contains() dans &lt;...>/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php:74*

Le problème sera corrigé dans la portée des versions 2.4.4, 2.4.3-p1 et 2.3.7-p2.

## Versions et produits concernés

* Adobe Commerce (toutes les méthodes de déploiement) lors de la mise à niveau vers 2.3.7-p1 ou 2.4.3.
* Magento Open Source lors de la mise à niveau vers 2.3.7-p1 ou 2.4.3.

## Problème

Le problème est causé par les nouvelles versions Adobe Commerce 2.4.3 et 2.3.7-p1 utilisant PHP 8 uniquement la fonction `str_contains`. Adobe Commerce 2.4.3 et 2.3.7-p1 sont uniquement compatibles avec PHP 7.4, cette fonction ne peut donc pas être utilisée.

<u>Procédure à suivre </u> :

Tentative de mise à niveau vers Adobe Commerce 2.4.3 ou 2.3.7-p1.

<u>Résultat attendu : </u>

Mise à niveau réussie.

<u>Résultat réel :</u>

Erreur fatale PHP.

## Solution

Pour pallier ce problème, exécutez la commande suivante dans l’interface de ligne de commande/Terminal : `composer require symfony/polyfill-php80` à partir du dossier racine Magento ou installez un correctif compositeur.

Pour résoudre le problème dans la version 2.4.3, Adobe Commerce (toutes les méthodes de déploiement) et les commerçants Magento Open Source doivent appliquer le correctif suivant :

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

Pour résoudre le problème de la version 2.3.7-p1, Adobe Commerce (toutes les méthodes de déploiement) et les commerçants Magento Open Source doivent appliquer le correctif suivant :

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## Application du correctif

Pour obtenir des instructions, consultez [Application d’un correctif de compositeur fourni par Magento](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) .

## Lectures connexes

GitHub [commande PHP 8 non prise en charge dans le #33680 EE de Magento 2.4.3](https://github.com/magento/magento2/issues/33680)
