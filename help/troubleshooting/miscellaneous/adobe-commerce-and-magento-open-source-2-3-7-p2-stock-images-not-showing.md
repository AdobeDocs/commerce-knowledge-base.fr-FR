---
title: Images Stock non affichées, Adobe Commerce et Magento Open Source 2.3.7-p2
description: Cet article fournit une solution au problème où les images de stock d’Adobe téléchargées dans les répertoires du système de fichiers "pub/media" ou "pub/media/catalog" ne s’affichent pas dans l’interface utilisateur de la galerie de médias. Cela est dû au fait que les images se trouvent en dehors des répertoires de galeries de médias autorisés. Pour que ces images s’affichent, les marchands doivent supprimer les images du système de fichiers et les transférer à nouveau dans un répertoire de galerie de médias autorisé.
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Images Stock non affichées, Adobe Commerce et Magento Open Source 2.3.7-p2

Cet article fournit une solution pour le problème où les images de stock d’Adobe téléchargées dans les répertoires du système de fichiers `pub/media` ou `pub/media/catalog` ne s’affichent pas dans l’interface utilisateur de la galerie de médias. Cela est dû au fait que les images se trouvent en dehors des répertoires de galeries de médias autorisés. Pour que ces images s’affichent, les marchands doivent supprimer les images du système de fichiers et les transférer à nouveau dans un répertoire de galerie de médias autorisé.

## Produits et versions concernés

* Adobe Commerce et Magento Open Source 2.3.7-p2


## Problème

Les marchands peuvent télécharger des images Adobe Stock sur la racine de stockage dans la galerie de médias, mais ces images n’apparaissent pas dans l’interface utilisateur et apparaîtront comme si elles n’avaient pas été téléchargées. Cela est dû au fait que le système remarque que l’image est déjà téléchargée vers le système de fichiers bien qu’elle ne soit pas disponible dans l’interface utilisateur de la galerie de médias. Cela signifie qu’une fois qu’un commerçant charge une image sur `pub/media` ou `pub/media/catalog`, il ne peut pas l’utiliser tant qu’elle n’a pas été supprimée directement dans le système de fichiers.

<u>Étapes à reproduire</u>

1. Activez Adobe Stock avec des clés d’API valides.
1. Ouvrez la galerie multimédia (**Catalogue** > **Catégories** > **section Contenu** > cliquez sur **Sélectionner dans la galerie**).
1. Cliquez sur **Rechercher dans Adobe Stock**.
1. Sélectionnez une image. Cliquez sur **Enregistrer l’aperçu**. Notez que vous devrez peut-être réinitialiser la grille Adobe Stock pour que les images apparaissent.

<u>Résultat attendu</u> :

L’image s’affiche.

<u>Résultat réel</u> :

Un message d&#39;erreur s&#39;affiche : *L&#39;image est introuvable. Nous ne pouvons pas trouver cette image dans la galerie de médias.*

## Cause

Les images peuvent être chargées sur la racine de stockage de la galerie de médias via Adobe Stock.

## Solution

Sélectionnez un sous-répertoire de la racine de stockage de la galerie de médias (à l’exception de **Racine de stockage** > **Catalogue**) avant de charger une image Adobe Stock.
Supprimez les images Adobe Stock téléchargées des dossiers `pub/media` et `pub/media/catalog` sur le système de fichiers Adobe Commerce et téléchargez les images dans tous les sous-répertoires racine de stockage de la galerie de médias autorisés à la place (à l’exception de **Racine de stockage** > **Catalogue**).

## Lecture connexe

* [Stockage multimédia](https://experienceleague.adobe.com/fr/docs/commerce-admin/content-design/wysiwyg/storage/media-storage) dans notre guide d’utilisation.
