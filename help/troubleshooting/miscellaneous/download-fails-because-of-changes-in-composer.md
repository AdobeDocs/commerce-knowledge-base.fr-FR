---
title: Le téléchargement échoue en raison de modifications apportées au compositeur
description: Cet article fournit un correctif pour une erreur d’exception et de téléchargement Adobe Commerce ayant échoué.
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%
---
# Le téléchargement échoue en raison de modifications apportées au compositeur

Cet article fournit un correctif pour une erreur d’exception et de téléchargement Adobe Commerce ayant échoué.

## Problème

Lors du téléchargement, l’erreur suivante s’affiche :

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## Cause

Cela se produit en raison de modifications apportées à certaines versions du compositeur. La solution consiste à rétrograder le compositeur vers une version antérieure et à retenter votre téléchargement Adobe Commerce.

## Solution

Toute version de Composer datée du 21 au 26 novembre 2015 présente ce problème. Pour confirmer que ce problème est lié à la version du compositeur, saisissez la commande suivante :

```php
composer -v
```

La version s’affiche comme suit :

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

Notez que la date est le 25/11/2015, ce qui indique que le compositeur rencontre ce problème.

Pour contourner ce problème :

1. Modifiez votre version du compositeur afin de pouvoir télécharger le logiciel Adobe Commerce en effectuant l’une des opérations suivantes :

   * Rétrogradez le compositeur à l’aide de la commande suivante : `composer self-update 1.0.0-alpha11`.
   * Mettez à niveau le compositeur vers une version ultérieure au 26 novembre 2015 : `composer self-update`.

1. Supprimez votre répertoire Adobe Commerce et ses sous-répertoires.
1. Relancez le téléchargement à l’aide de `[composer create-project](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer)` ou `[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)`.
1. Une fois le logiciel Adobe Commerce téléchargé, mettez à jour le compositeur : `composer self-update`.
