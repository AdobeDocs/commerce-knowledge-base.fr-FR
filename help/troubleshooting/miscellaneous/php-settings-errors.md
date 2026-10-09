---
title: Erreurs de paramètres PHP
description: Cet article fournit des solutions pour les erreurs de paramètres PHP.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
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
source-wordcount: '348'
ht-degree: 0%
---
# Erreurs de paramètres PHP

Cet article fournit des solutions pour les erreurs de paramètres PHP.

## Erreur de limite de mémoire PHP

Les contrôles de préparation vous permettent de vous assurer que vous disposez d&#39;au moins 1 Go de mémoire réservée aux processus PHP. Ce paramètre doit être suffisant pour la plupart des installations, y compris l’installation de données d’exemple facultatives. Cependant, nous recommandons au moins 2 Go pour le débogage.

Pour augmenter votre limite de mémoire PHP :

1. Connectez-vous à votre serveur Adobe Commerce.
1. Localisez votre fichier `php.ini` à l’aide de la commande suivante :

   ```
   bash    $ php --ini
   ```

1. En tant qu’utilisateur disposant de droits d’`root`, utilisez un éditeur de texte pour ouvrir le `php.ini` spécifié par `Loaded Configuration File`.
1. Localisez `memory_limit`.
1. Remplacez-la par une valeur `2GB` pour une utilisation normale et le débogage.
1. Enregistrez vos modifications dans `php.ini` et quittez l’éditeur de texte.
1. Redémarrez votre serveur web. Voici quelques exemples :

   * CentOS : `service httpd restart`
   * Ubuntu : `service apache2 restart`
   * nginx (CentOS et Ubuntu) : `service nginx restart`

1. Recommencez l&#39;installation.

## erreur max-input-vars en raison de formulaires volumineux

Les configurations comportant un grand nombre de vues de magasins, de produits, d’attributs ou d’options peuvent générer des formulaires qui dépassent la limite PHP prédéfinie. Si le nombre de valeurs envoyées dépasse la limite de `max-input-vars` définie dans `php.ini` (la valeur par défaut est 1 000), les données restantes ne sont pas transférées et ces valeurs de base de données ne sont pas mises à jour. Dans ce cas, un message d&#39;avertissement apparaît dans le log PHP :

```bash
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Il n’existe aucune valeur « appropriée » pour `max-input-vars` ; elle dépend de la taille et de la complexité de votre configuration. Modifiez la valeur dans le fichier `php.ini` selon vos besoins. Voir [Paramètres PHP requis](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/php-settings).

## erreur de niveau d’imbrication de la fonction maximale xdebug

Voir [Lors de l’installation, erreur de niveau d’imbrication de fonction maximale xdebug](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Les erreurs s’affichent lorsque vous accédez à un modèle HTML

Le texte de l’erreur est généralement :

```bash
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Solution : `asp_tags = off` en php.ini

Plusieurs modèles comportent une syntaxe pour la prise en charge du niveau abstrait sur les modèles (utilisez différents moteurs de modèles tels que Twig) enveloppés dans des balises `<% %>`, comme ce [modèle](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) pour afficher une image de produit :

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Informations supplémentaires sur [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Modifiez des `php.ini` et définissez des `asp_tags = off`. Pour plus d&#39;informations, voir [Paramètres PHP requis](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/php-settings).
