---
title: robots.txt non mis à jour ou affichage des paramètres par défaut
description: L’article fournit une solution lorsque vous avez configuré correctement `robots.txt`, par exemple par [Bonnes pratiques pour Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), mais que le `robots.txt` n’est pas mis à jour ou affiche les paramètres par défaut.
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt non mis à jour ou affichage des paramètres par défaut

L’article fournit une solution pour lorsque vous avez configuré `robots.txt` correctement, par exemple par [Bonnes pratiques pour Adobe Commerce robots.txt](https://support.magento.com/hc/en-us/articles/360048754931), mais que le `robots.txt` n’est pas mis à jour ou affiche les paramètres par défaut.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.x, 2.4.x

## Problème

Impossible de modifier le paramètre par défaut `robots.txt`.

<u>Étapes à reproduire :</u>

1. Accédez au panneau Admin.
1. Ajoutez du contenu à **Contenu** > Conception > **Configuration** > **Modifier l’instruction personnalisée du fichier`robots.txt`** comme le texte &quot;hello&quot; et enregistrez les modifications.
1. Visitez l’URL `robots.txt`.

<u>Résultat attendu :</u>
`robots.txt` contient le texte enregistré.

<u>Résultat réel :</u>

Le fichier `robots.txt` ne change pas.

## Cause

L’indexation par les moteurs de recherche est désactivée.

## Solution

Activez l’indexation par moteur de recherche. Voir [Configuration de l’indexation par moteur de recherche](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine) dans notre documentation destinée aux développeurs.

## Lecture connexe

* [Ajoutez des robots de moteur de recherche et de carte de site](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) dans notre documentation destinée aux développeurs.
