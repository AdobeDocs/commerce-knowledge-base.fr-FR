---
title: laminas/laminas-escaper 2.7.1 provoque une erreur dans les pages frontales Adobe Commerce et d’administration
description: Cet article fournit une solution au problème où la sortie de plasas/laminas-escaper:2.7.1 rompt les fonctionnalités d’Adobe Commerce dans la gestion de produits, les catégories et les pages de produits. Ce problème sera corrigé dans Adobe Commerce 2.4.3.
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escaper 2.7.1 provoque une erreur dans les pages frontales Adobe Commerce et d’administration


## Produits et versions concernés

* Adobe Commerce sur notre architecture cloud 2.3.5+
* Adobe Commerce 2.3.5+

## Problème

Après la mise à jour vers laminas/laminas-escaper:2.7.1, un message d’erreur s’affiche sur la page.

<u>Étapes à reproduire</u>:

Remplacez plasas/laminas-escaper par 2.7.1.

<u>Résultat attendu</u>:

Aucune erreur.

<u>Résultat réel</u>:

Après la mise à jour vers laminas/laminas-escaper:2.7.1, un message d’erreur s’affiche sur une page d’édition de produit (ou de gestion de produit) : *TypeError : rawurlencode() s’attend à ce que le paramètre 1 soit une chaîne, int donné dans /var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php:246*
Cette erreur se produit sur les pages front-end et d’administration, provoquant une distorsion du contenu de la page.

## Cause

plasas/laminas-escaper 2.7.1 a commencé à utiliser une validation de type stricte pour la classe Escaper.

## Solution

Exécuter `composer require laminas/laminas-escaper:2.7.0` dans le répertoire racine de chaque projet.

## Lecture connexe

laminas Documentation : [plasas-escaper](https://docs.laminas.dev/laminas-escaper/)
