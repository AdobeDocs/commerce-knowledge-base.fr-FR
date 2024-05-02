---
title: robots.txt donne une erreur 404 à Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit un correctif pour le moment où le fichier `robots.txt` renvoie une erreur 404 dans Adobe Commerce sur l’infrastructure cloud.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt donne une erreur 404 à Adobe Commerce sur l’infrastructure cloud

Cet article fournit un correctif pour le `robots.txt` renvoie une erreur 404 dans Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

La variable `robots.txt` ne fonctionne pas et renvoie une exception Nginx. La variable `robots.txt` est généré dynamiquement &quot;à la volée&quot;. La variable `robots.txt` n’est pas accessible par la fonction `/robots.txt` URL car Nginx possède une règle de réécriture qui redirige de force tous les `/robots.txt` à la fonction `/media/robots.txt` qui n’existe pas.

## Cause

Cela se produit généralement lorsque Nginx n’est pas configuré correctement.

## Solution

La solution consiste à désactiver la règle Nginx qui redirige `/robots.txt` à la fonction `/media/robots.txt` fichier . Les commerçants avec libre-service activé peuvent le faire par eux-mêmes, et les marchands sans libre-service activé doivent créer un ticket d’assistance.

Si le libre-service n’est pas activé (ou si vous ne savez pas s’il est activé), [envoi d’un ticket d’assistance Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demande de suppression de la règle de redirection Nginx `/robots.txt` requêtes à `/media/robots.txt`.

Si le libre-service est activé, mettez à niveau les outils ECID vers au moins la version 2002.0.12 et supprimez la règle de redirection Nginx dans votre `.magento.app.yaml` fichier . Vous pouvez consulter [Ajout de robots de carte de site et de moteur de recherche](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) pour plus d’informations, voir la documentation destinée aux développeurs .

## Lecture connexe

* [Comment bloquer le trafic malveillant pour Magento Commerce Cloud à un niveau Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) dans notre base de connaissances de soutien.
* [Ajout de robots de carte de site et de moteur de recherche](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) dans notre documentation destinée aux développeurs.
* [Robots des moteurs de recherche](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) dans notre guide d’utilisation.
