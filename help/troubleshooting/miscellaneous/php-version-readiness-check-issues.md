---
title: Problèmes de vérification de l’état de préparation des versions PHP
description: Cet article décrit les solutions aux problèmes de version PHP que vous pouvez rencontrer lors de l’installation/de la mise à niveau d’Adobe Commerce sur site à l’aide de l’assistant de configuration web.
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Problèmes de vérification de l’état de préparation des versions PHP

Cet article décrit les solutions aux problèmes de version PHP que vous pouvez rencontrer lors de l’installation/de la mise à niveau d’Adobe Commerce sur site à l’aide de l’assistant de configuration web.

>[!WARNING]
>
>Sur Adobe Commerce sur l’infrastructure cloud, notez que les mises à niveau de service ne peuvent pas être transférées vers l’environnement de production sans préavis de 48 heures ouvrables à notre équipe d’infrastructure. Cela est nécessaire, car nous devons nous assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais voulus, avec un temps d’arrêt minimal pour votre environnement de production. 48 heures avant que vos modifications ne soient en production [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle le processus de mise à niveau doit commencer.

## Produits et versions concernés

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Version PHP non prise en charge

### Problème

La vérification échoue car vous utilisez une version PHP non prise en charge.

### Solution

Pour résoudre ce problème, utilisez l’une des versions prises en charge répertoriées dans notre documentation destinée aux développeurs. [Configuration requise 2.3.x](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html) et [Configuration requise 2.2.x](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html).

## La vérification de la préparation PHP ne s’affiche pas

### Problème

La vérification de l’état de préparation PHP n’affiche pas la version PHP comme le montre la figure suivante.
![upgr-tshot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### Solution

Ceci est le symptôme d’une configuration de tâche cron incorrecte. Pour plus d’informations, voir [Configuration de tâches cron](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) dans notre documentation destinée aux développeurs.

## Version PHP incorrecte

### Problème

La vérification indique une version PHP incorrecte. En règle générale, cela se produit uniquement pour les utilisateurs avancés qui ont installé plusieurs versions de PHP. Dans certains cas, la vérification de l’état de préparation échoue ; dans d’autres cas, elle peut réussir.

Si la version PHP signalée par la vérification de l’état de préparation est incorrecte, cela résulte d’une incohérence des versions PHP entre l’interface de ligne de commande de PHP et le module externe de serveur web. Adobe Commerce requiert que vous utilisiez *une version* de PHP pour l’interface de ligne de commande (qui exécute cron) et le serveur web (qui exécute l’administrateur Commerce, le gestionnaire de composants et la mise à niveau du système).

### Solution

Nous supposons que si vous rencontrez ce problème, vous êtes un utilisateur avancé qui a probablement installé plusieurs versions de PHP sur votre système.

Pour résoudre ce problème, essayez les méthodes suivantes :

* Redémarrez votre serveur web ou php-fm.
* Vérifiez les `$PATH` Variable d’environnement pour plusieurs chemins d’accès à PHP.
* Utilisez la variable `which php` pour localiser le premier fichier exécutable PHP dans votre chemin d’accès ; s’il n’est pas correct, supprimez-le ou créez un lien symbolique vers la version PHP correcte.
* Utilisez une [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) pour collecter plus d’informations.
* Assurez-vous d’exécuter une version PHP prise en charge en fonction de la configuration requise, dans la documentation destinée aux développeurs :
   * [Configuration requise pour Adobe Commerce 2.3.x](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html)
   * [Configuration requise pour Adobe Commerce 2.2.x](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html)
* Définissez les mêmes paramètres PHP pour la ligne de commande PHP et le plug-in du serveur Web PHP comme décrit dans la section [options de configuration PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-centos-ubuntu.html) dans notre documentation destinée aux développeurs.
