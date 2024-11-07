---
title: Échec du téléchargement en raison des modifications dans le compositeur
description: Cet article fournit un correctif pour une erreur de téléchargement et d’exception Adobe Commerce ayant échoué.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Échec du téléchargement en raison des modifications dans le compositeur

Cet article fournit un correctif pour une erreur de téléchargement et d’exception Adobe Commerce ayant échoué.

## Problème

Lors du téléchargement, l’erreur suivante s’affiche :

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Cause

Cela se produit en raison des modifications apportées à certaines versions du compositeur. La méthode de contournement consiste à rétrograder le compositeur vers une version antérieure et à effectuer à nouveau le téléchargement Adobe Commerce.

## Solution

Toute version du compositeur datée du 21 novembre au 26 novembre 2015 présente ce problème. Pour confirmer que ce problème est lié à la version du compositeur, saisissez la commande suivante :

```php
composer -v
```

La version s’affiche comme suit :

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Notez que la date est 2015-11-25, ce qui indique que le compositeur a ce problème.

Pour contourner ce problème :

1. Modifiez votre version du compositeur afin de vous permettre de télécharger le logiciel Adobe Commerce en effectuant l’une des opérations suivantes :

   * Rétrogradation du compositeur à l’aide de la commande suivante : `composer self-update 1.0.0-alpha11`.
   * Mise à niveau du compositeur vers une version ultérieure au 26 novembre 2015 : `composer self-update`.

1. Supprimez votre répertoire Adobe Commerce et vos sous-répertoires.
1. Essayez à nouveau le téléchargement en utilisant `[composer create-project](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer)` ou `[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)`.
1. Après avoir téléchargé le logiciel Adobe Commerce, mettez à jour le compositeur : `composer self-update`.
