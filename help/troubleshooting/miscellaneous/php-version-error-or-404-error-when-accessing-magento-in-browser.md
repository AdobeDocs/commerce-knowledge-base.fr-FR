---
title: Erreur de version PHP ou erreur 404 lors de l’accès à Adobe Commerce dans le navigateur
description: Cet article fournit des solutions aux problèmes où vous ne pouvez pas accéder à votre instance Adobe Commerce dans un navigateur web et obtenir l’erreur 404 ou "version PHP non prise en charge".
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Erreur de version PHP ou erreur 404 lors de l’accès à Adobe Commerce dans le navigateur

Cet article fournit des solutions aux problèmes où vous ne pouvez pas accéder à votre instance Adobe Commerce dans un navigateur web et obtenir l’erreur 404 ou &quot;version PHP non prise en charge&quot;.

## Produits et versions concernés :

* Adobe Commerce 2.3.x

## Problème : version de PHP non prise en charge

Le message suivant s’affiche lorsque vous essayez d’accéder au storefront d’Adobe Commerce ou à l’administrateur Commerce :

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### Solution

Procédez comme suit :

* Mettez à niveau PHP vers la version 7.3. Pour plus d’informations, voir [Exigences en matière de pile de technologie Adobe Commerce 2.3](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html#php) dans notre documentation destinée aux développeurs.
* Redémarrez Apache, car il se peut qu’il n’utilise pas la même version PHP que sur le système de fichiers. Pour redémarrer Apache, utilisez les commandes suivantes :
   * Ubuntu : `service apache2 restart`
   * CentOS : `service httpd restart`

## Problème : erreur 404

Une erreur 404 (Introuvable) s’affiche lorsque vous essayez d’accéder au storefront Adobe Commerce ou à l’administrateur Commerce.

### Solution

Procédez comme suit :

* Assurez-vous de [Réécritures du serveur Apache](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html) sont activées. Si les réécritures du serveur Apache sont incorrectement définies, les fichiers statiques ne sont pas diffusés à partir du bon emplacement.
* Il peut y avoir un problème avec l’URL de base que vous avez saisie lors de l’installation. Vous spécifiez l’URL de base comme valeur de `--base-url=` lors de l’installation d’Adobe Commerce à partir de la ligne de commande ou en tant que valeur de la variable **Adresse de la boutique** sur la page Configuration Web du programme d’installation Web. URL de base *must* commencer par le schéma (par exemple `http://` ) et se terminent par une barre oblique (/). Exécutez à nouveau le programme d’installation avec une valeur valide et essayez ensuite d’accéder à Adobe Commerce.
