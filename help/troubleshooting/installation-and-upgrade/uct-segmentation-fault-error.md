---
title: Dépannage des erreurs de l’outil de compatibilité de mise à niveau
description: Cet article explique les erreurs que vous pouvez rencontrer lors de l’utilisation de l’outil de compatibilité de mise à niveau et fournit des solutions pour corriger ces erreurs afin que vous puissiez exécuter l’outil avec succès.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Dépannage des erreurs de l’outil de compatibilité de mise à niveau

Cet article explique les erreurs que vous pouvez rencontrer lors de l’utilisation de l’outil de compatibilité de mise à niveau et fournit des solutions pour corriger ces erreurs afin que vous puissiez exécuter l’outil avec succès.

## Produits et versions concernés

* [Outil de compatibilité de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) est compatible avec les versions Adobe Commerce à partir de la version 2.3.0.

## Erreur de segmentation

<u>Cause</u>:

Lorsque deux modules portent le même nom, l’outil de compatibilité de mise à niveau affiche une erreur de segmentation.

<u>Solution</u>:

Pour éviter cette erreur, il est recommandé de spécifier le chemin d’accès au module en tant qu’argument :

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> L’outil de compatibilité de mise à niveau peut ne pas être en mesure d’analyser le code base s’il contient une dépendance circulaire entre les méthodes.

## Sortie vide

<u>Étapes à reproduire</u>:

1. Si après avoir exécuté cette commande :

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. La seule sortie est `Upgrade compatibility tool`:

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>Cause</u>:

La cause probable est une limitation de la mémoire PHP.

Deux solutions sont possibles pour éviter cette limitation de mémoire PHP.

<u>Solution 1</u>:

Remplacez la limitation de mémoire en définissant `memory_limit` to `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> La variable `M2_VERSION` est la version Adobe Commerce cible que vous souhaitez comparer à votre instance Adobe Commerce.

<u>Solution 2</u>:

Ajouter le `-m` L’option permet à l’outil de compatibilité de mise à niveau d’analyser indépendamment chaque module spécifique afin d’éviter de rencontrer deux modules portant le même nom dans votre instance Adobe Commerce.

Cette option de commande permet également à l’outil de compatibilité de mise à niveau d’analyser un dossier contenant plusieurs modules :

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Voir [Exécution de l’outil dans une interface de ligne de commande](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html) pour plus d’informations sur les options de l’interface de ligne de commande.
