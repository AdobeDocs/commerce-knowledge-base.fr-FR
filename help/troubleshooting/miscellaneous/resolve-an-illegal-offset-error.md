---
title: Résoudre une erreur de décalage non autorisée
description: Cet article fournit une solution pour lorsque, dans Adobe Commerce 2.1 ou version ultérieure, vous recevez une erreur de décalage illégal lors de la création d’un produit dans Commerce Admin.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Résoudre une erreur de décalage non autorisée

Cet article fournit une solution pour lorsque, dans Adobe Commerce 2.1 ou version ultérieure, vous recevez une erreur de décalage illégal lors de la création d’un produit dans Commerce Admin.

Dans Adobe Commerce 2.1 ou version ultérieure, lors de la création d’un produit dans Commerce Admin, l’erreur suivante peut s’afficher :

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Détail

Adobe Commerce 2.1 et versions ultérieures utilisent les commentaires de code PHP dans les `getDocComment` appel de validation dans la fonction [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) dans `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Si vous avez activé le OPcache PHP (que nous recommandons), cette erreur s’affiche car, par défaut, le paramètre OPcache [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) est désactivée.

## Solution

Pour résoudre le problème, recherchez les paramètres de configuration OPcache et activez `opcache.save_comments` comme suit :

### Étape 1 : Localisation de la configuration OPcache

#### Pour rechercher les paramètres de configuration du cache d’OP :

Les paramètres du OPcache PHP sont généralement situés dans la variable `php.ini` ou `opcache.ini`. L’emplacement peut dépendre de votre système d’exploitation et de la version PHP. Le fichier de configuration OPcache peut comporter une `[opcache]` ou des paramètres tels que `opcache.enable`.

Suivez les instructions ci-dessous pour le trouver :

* Serveur web Apache :<br>

Pour Ubuntu avec Apache, les paramètres OPcache se trouvent généralement dans `php.ini`.<br>
Pour CentOS avec Apache ou nginx, les paramètres OPcache se trouvent généralement dans `/etc/php.d/opcache.ini`.<br>
Dans le cas contraire, utilisez la commande suivante pour la localiser :

```bash
    $ sudo find / -name 'opcache.ini'
```

* Serveur web nginx avec PHP-FPM : `/etc/php5/fpm/php.ini`.

Si vous en avez plusieurs `opcache.ini`, modifiez-les tous.


### Étape 2 : Activer `opcache.save_comments`

1. Ouvrez votre fichier de configuration OPcache dans un éditeur de texte.
1. Localiser `opcache.save_comments` et décommentez-le, si nécessaire.
1. Assurez-vous que sa valeur est définie sur `1`.
1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Redémarrez votre serveur web :

   * Apache, Ubuntu : `service apache2 restart`
   * Apache, CentOS : `service httpd restart`
   * nginx, Ubuntu et CentOS : `service nginx restart`

1. Régénérer la configuration de l’ID et toutes les classes manquantes qui peuvent être générées automatiquement :

```bash
    $ bin/magento setup:di:compile`
```
