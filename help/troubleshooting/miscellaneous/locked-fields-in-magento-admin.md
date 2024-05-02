---
title: Champs verrouillés dans l’administrateur Commerce
description: Cet article fournit une solution lorsque vous ne pouvez pas modifier les champs dans l’administrateur Commerce.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Champs verrouillés dans l’administrateur Commerce

Cet article fournit une solution lorsque vous ne pouvez pas modifier les champs dans l’administrateur Commerce.

## Produits et versions concernés

* Adobe Commerce on-premise 2.3.x, 2.4.x
* Adobe Commerce sur l’infrastructure cloud 2.3.x, 2.4.x

## Problème

Une fois que vous avez enregistré la modification de votre configuration sur `app/etc/env.php` ou `app/etc/config.php`, vous ne pouvez pas modifier le paramètre dans Admin.

<u>Étapes à reproduire</u>:

Remarque : Il s’agit d’un exemple. Le problème peut affecter toutes les configurations qui ont été enregistrées.

1. Le marchand enregistre les informations d’identification de ses méthodes de diffusion à l’aide de la commande suivante dans le terminal : `./vendor/bin/ece-tools config:dump`. Les informations d’identification sont ainsi enregistrées dans la variable `app/etc/env.php` fichier .
1. Le commerçant tente ensuite de modifier les informations d’identification.

<u>Résultats attendus</u>:

Le marchand peut définir les valeurs dans les paramètres du champ Admin et les enregistrer.

<u>Résultats réels</u>:

Les champs de l’administrateur sont verrouillés ou les valeurs peuvent être modifiées, mais ne seront pas enregistrées dans l’administrateur.

## Cause

Lorsque la configuration est enregistrée dans `env.php` ou `config.php`, vous ne pourrez pas modifier le paramètre dans l’Admin. Pour permettre la modification du paramètre, vous devez supprimer la configuration de `env.php` ou `config.php`.

## Solution

Assurez-vous que la configuration n’a pas été enregistrée dans `app/etc/env.php` ou `app/etc/config.php`. S’il a été enregistré, essayez les étapes suivantes :

* `config.php` - Supprimez le paramètre, puis redéployez.
* `env.php` - Modifiez ce paramètre directement sur le serveur et supprimez-le, puis exécutez `bin/magento app:config:import`.

## Lecture connexe

* [Exportation de la configuration](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings) dans notre documentation destinée aux développeurs.
* [Définition des valeurs de configuration](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set) dans notre documentation destinée aux développeurs.
* [Adobe Commerce sur l’infrastructure cloud : réduisez les temps d’arrêt du déploiement avec Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) dans notre base de connaissances de soutien.
