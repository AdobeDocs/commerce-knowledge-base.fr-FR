---
title: Résoudre une erreur de décalage non autorisée
description: Cet article fournit une solution pour le cas où, dans Adobe Commerce version 2.1 ou ultérieure, vous recevriez une erreur de résolution d’un décalage illégal lors de la création d’un nouveau produit dans l’administration Commerce.
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
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
source-wordcount: '324'
ht-degree: 0%
---
# Résoudre une erreur de décalage non autorisée

Cet article fournit une solution pour le cas où, dans Adobe Commerce version 2.1 ou ultérieure, vous recevriez une erreur de résolution d’un décalage illégal lors de la création d’un nouveau produit dans l’administration Commerce.

Dans Adobe Commerce 2.1 ou une version ultérieure, lors de la création d’un nouveau produit dans l’Administration de Commerce, l’erreur suivante peut s’afficher :

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## Détail

Adobe Commerce 2.1 et versions ultérieures utilisent les commentaires de code PHP dans l&#39;appel de validation `getDocComment` dans la méthode [`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73) de `Magento\Framework\Api\ExtensionAttributesFactory.php`.

Si vous avez activé PHP OPcache (ce que nous recommandons), cette erreur s&#39;affiche car par défaut, le paramètre OPcache [`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments) est désactivé.

## Solution

Pour résoudre le problème, recherchez les paramètres de configuration OPcache et activez `opcache.save_comments` comme suit :

### Étape 1 : Rechercher la configuration de votre cache OP

#### Pour trouver les paramètres de configuration OPcache :

Les paramètres PHP OPcache sont généralement situés dans `php.ini` ou `opcache.ini`. L&#39;emplacement peut dépendre de votre système d&#39;exploitation et de la version PHP. Le fichier de configuration OPcache peut avoir une section `[opcache]` ou des paramètres comme `opcache.enable`.

Suivez les instructions suivantes pour le trouver :

* Serveur web Apache :<br>

Pour Ubuntu avec Apache, les paramètres OPcache sont généralement situés dans `php.ini`.<br>
Pour CentOS avec Apache ou nginx, les paramètres OPcache sont généralement situés dans `/etc/php.d/opcache.ini`.<br>
Dans le cas contraire, la commande suivante permet de le localiser :

```bash
    $ sudo find / -name 'opcache.ini'
```

* Serveur web nginx avec PHP-FPM : `/etc/php5/fpm/php.ini`.

Si vous disposez de plusieurs `opcache.ini`, modifiez-les toutes.


### Étape 2 : activer le `opcache.save_comments`

1. Ouvrez votre fichier de configuration OPcache dans un éditeur de texte.
1. Recherchez `opcache.save_comments` et supprimez les commentaires si nécessaire.
1. Assurez-vous que sa valeur est définie sur `1`.
1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Redémarrez votre serveur web :

   * Apache, Ubuntu : `service apache2 restart`
   * Apache, CentOS : `service httpd restart`
   * nginx, Ubuntu et CentOS : `service nginx restart`

1. Régénérez la configuration d’ID et toutes les classes manquantes qui peuvent être générées automatiquement :

```bash
    $ bin/magento setup:di:compile`
```
