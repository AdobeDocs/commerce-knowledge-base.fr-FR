---
title: erreurs de paramètres PHP
description: Cet article fournit des solutions pour les erreurs de paramètres PHP.
exl-id: 51fb3c95-2e25-4d86-a6cf-e08e90d097ca
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# erreurs de paramètres PHP

Cet article fournit des solutions pour les erreurs de paramètres PHP.

## Erreur de limite de mémoire PHP

Les contrôles de préparation permettent de s’assurer qu’au moins 1 Go de mémoire est réservé aux processus PHP. Ce paramètre doit être suffisant pour la plupart des installations, y compris l’installation de données d’exemple facultatives. Toutefois, nous recommandons d’utiliser au moins 2 Go pour le débogage.

Pour augmenter votre limite de mémoire PHP :

1. Connectez-vous à votre serveur Adobe Commerce.
1. Recherchez votre `php.ini` à l’aide de la commande suivante :

   ```
   bash    $ php --ini
   ```

1. En tant qu’utilisateur avec `root` autorisations, utilisez un éditeur de texte pour ouvrir la `php.ini` spécifié par `Loaded Configuration File`.
1. Localiser `memory_limit`.
1. Remplacez-la par une valeur de `2GB` pour une utilisation normale et un débogage.
1. Enregistrez vos modifications dans `php.ini` et quittez l’éditeur de texte.
1. Redémarrez votre serveur web. Voici des exemples :

   * CentOS : `service httpd restart`
   * Ubuntu : `service apache2 restart`
   * nginx (CentOS et Ubuntu) : `service nginx restart`

1. Réessayez l’installation.

## erreur max-input-vars due à des formulaires volumineux

Les configurations comportant un grand nombre de storeviews, de produits, d’attributs ou d’options peuvent générer des formulaires qui dépassent la limite prédéfinie PHP. Si le nombre de valeurs envoyées dépasse la valeur `max-input-vars` limite définie dans `php.ini` (la valeur par défaut est 1 000), les données restantes ne sont pas transférées et ces valeurs de base de données ne sont pas mises à jour. Dans ce cas, un avertissement s’affiche dans le journal PHP :

```terminal
PHP message: PHP Warning: Unknown: Input variables exceeded 1000. To increase the limit change max_input_vars in php.ini.
```

Il n’existe pas de valeur &quot;correcte&quot; pour `max-input-vars`; cela dépend de la taille et de la complexité de votre configuration. Modifiez la valeur de la variable `php.ini` le cas échéant. Voir [Paramètres PHP requis](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).

## erreur de niveau d&#39;imbrication de fonction maximal xdebug

Voir [Lors de l’installation, erreur de niveau d’imbrication de fonction maximum xdebug](/help/troubleshooting/miscellaneous/installation-xdebug-maximum-function-nesting-level-error.md).

## Des erreurs s’affichent lorsque vous accédez à un modèle HTML.

Le texte d’erreur est généralement :

```terminal
Parse error: syntax error, unexpected 'data' (T_STRING)
```

### Solution : Définissez `asp_tags = off` dans php.ini

Plusieurs modèles ont une syntaxe pour la prise en charge du niveau abstrait sur les modèles (utilisez différents moteurs de modèle tels que Twig) encapsulés dans `<% %>` balises, comme ceci [modèle](https://github.com/magento/magento2/blob/2.0/app/code/Magento/Catalog/view/adminhtml/templates/product/edit/base_image.phtml) pour afficher une image de produit :

```php
<img
    class="product-image"
    src="<%- data.url %>"
    data-position="<%- data.position %>"
    alt="<%- data.label %>" />
```

Plus d’informations sur [asp\_tags](http://php.net/manual/en/ini.core.php#ini.asp-tags).

Modifier `php.ini` et défini `asp_tags = off`. Pour plus d’informations, voir [Paramètres PHP requis](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html).
