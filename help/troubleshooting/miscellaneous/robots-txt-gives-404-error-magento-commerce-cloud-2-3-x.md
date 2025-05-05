---
title: robots.txt donne une erreur 404 à Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit un correctif pour le moment où le fichier &grave;robots.txt&grave; renvoie une erreur 404 dans Adobe Commerce sur l’infrastructure cloud.
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt donne une erreur 404 à Adobe Commerce sur l’infrastructure cloud

Cet article fournit un correctif pour le moment où le fichier `robots.txt` renvoie une erreur 404 dans Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

Le fichier `robots.txt` ne fonctionne pas et renvoie une exception Nginx. Le fichier `robots.txt` est généré dynamiquement &quot;à la volée&quot;. Le fichier `robots.txt` n’est pas accessible par l’URL `/robots.txt` car Nginx possède une règle de réécriture qui redirige de force toutes les requêtes `/robots.txt` vers le fichier `/media/robots.txt` qui n’existe pas.

## Cause

Cela se produit généralement lorsque Nginx n’est pas configuré correctement.

## Solution

La solution consiste à désactiver la règle Nginx qui redirige les requêtes `/robots.txt` vers le fichier `/media/robots.txt`. Les commerçants avec libre-service activé peuvent le faire par eux-mêmes, et les marchands sans libre-service activé doivent créer un ticket d’assistance.

Si le libre-service n’est pas activé (ou si vous ne savez pas s’il est activé), [envoyez un ticket d’assistance Magento](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant la suppression de la règle de redirection Nginx des demandes `/robots.txt` vers `/media/robots.txt`.

Si vous avez activé le libre-service, mettez à niveau les outils de la fonction ECID vers au moins la version 2002.0.12 et supprimez la règle de redirection Nginx dans votre fichier `.magento.app.yaml`. Pour plus d’informations, reportez-vous à la section [Ajout de robots de moteur de recherche et de carte de site](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html?lang=fr) dans la documentation destinée aux développeurs.

## Lecture connexe

* [Comment bloquer le trafic malveillant pour les Magento Commerce Cloud à un niveau Fastly](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) dans notre base de connaissances de support.
* [Ajoutez des robots de moteur de recherche et de carte de site](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) dans notre documentation destinée aux développeurs.
* [Robots de moteur de recherche](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html?lang=fr#search-engine-robots) dans notre guide d’utilisation.
