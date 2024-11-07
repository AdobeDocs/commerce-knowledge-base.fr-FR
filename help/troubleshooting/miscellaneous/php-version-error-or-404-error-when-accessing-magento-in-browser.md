---
title: Erreur de version PHP ou erreur 404 lors de l’accès à Adobe Commerce dans le navigateur
description: Cet article fournit des solutions aux problèmes où vous ne pouvez pas accéder à votre instance Adobe Commerce dans un navigateur web et obtenir l’erreur 404 ou "version PHP non prise en charge".
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

* Mettez à niveau PHP vers la version 7.3. Pour plus d’informations, reportez-vous à la section [Exigences de pile de technologie Adobe Commerce 2.3](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements) de notre documentation destinée aux développeurs.
* Redémarrez Apache, car il se peut qu’il n’utilise pas la même version PHP que sur le système de fichiers. Pour redémarrer Apache, utilisez les commandes suivantes :
   * Ubuntu : `service apache2 restart`
   * CentOS : `service httpd restart`

## Problème : erreur 404

Une erreur 404 (Introuvable) s’affiche lorsque vous essayez d’accéder au storefront Adobe Commerce ou à l’administrateur Commerce.

### Solution

Procédez comme suit :

* Assurez-vous que les [réécritures du serveur Apache](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/web-server/apache) sont activées. Si les réécritures du serveur Apache sont incorrectement définies, les fichiers statiques ne sont pas diffusés à partir du bon emplacement.
* Il peut y avoir un problème avec l’URL de base que vous avez saisie lors de l’installation. Vous spécifiez l’URL de base comme valeur de `--base-url=` lors de l’installation d’Adobe Commerce à partir de la ligne de commande ou comme valeur du champ **Your Store Address** sur la page de configuration web du programme d’installation web. L’URL de base *must* commence par le schéma (tel que `http://` ) et se termine par une barre oblique (/). Exécutez à nouveau le programme d’installation avec une valeur valide et essayez ensuite d’accéder à Adobe Commerce.
