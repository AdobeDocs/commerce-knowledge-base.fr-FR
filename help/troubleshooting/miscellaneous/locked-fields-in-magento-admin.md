---
title: Champs verrouillés (grisés) dans l’administrateur Commerce
description: Cet article fournit une solution lorsque vous ne pouvez pas modifier les champs dans l’administrateur Commerce.
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Champs verrouillés (grisés) dans l’administrateur Commerce

Cet article fournit une solution lorsque vous ne pouvez pas modifier les champs verrouillés (grisés) dans l’administrateur Commerce.

## Produits et versions concernés

* Adobe Commerce on-premise 2.3.x, 2.4.x
* Adobe Commerce sur l’infrastructure cloud 2.3.x, 2.4.x

## Problème

Une fois que vous avez enregistré une modification de votre configuration sur `app/etc/env.php` ou `app/etc/config.php`, vous ne pouvez pas modifier le paramètre dans l’administrateur.

<u>Étapes à reproduire</u> :

Remarque : Il s’agit d’un exemple. Le problème peut affecter toutes les configurations qui ont été enregistrées.

1. Le commerçant enregistre ses informations d’identification de méthodes de diffusion à l’aide de la commande suivante dans le terminal : `./vendor/bin/ece-tools config:dump`. Cela permet d’enregistrer les informations d’identification dans le fichier `app/etc/env.php`.
1. Le commerçant tente ensuite de modifier les informations d’identification.

<u>Résultats attendus</u> :

Le marchand peut définir les valeurs dans les paramètres du champ Admin et les enregistrer.

<u>Résultats réels</u> :

Les champs de l’administrateur sont verrouillés ou les valeurs peuvent être modifiées, mais ne seront pas enregistrées dans l’administrateur.

## Cause

Lorsque la configuration est enregistrée sur `env.php` ou `config.php`, vous ne pourrez pas modifier le paramètre dans l’administrateur. Pour permettre la modification du paramètre, vous devez supprimer la configuration de `env.php` ou `config.php`.

## Solution

Assurez-vous que la configuration n&#39;a pas été enregistrée sur `app/etc/env.php` ou `app/etc/config.php`. S’il a été enregistré, essayez les étapes suivantes :

* `config.php` - Supprimez le paramètre, puis redéployez.
* `env.php` - Modifiez directement sur le serveur et supprimez le paramètre, puis exécutez `bin/magento app:config:import`.

## Lecture connexe

* [Exportez la configuration](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/export-configuration) dans notre documentation destinée aux développeurs.
* [Définissez les valeurs de configuration](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values) dans notre documentation destinée aux développeurs.
* [Adobe Commerce sur l’infrastructure cloud : réduisez le temps d’arrêt du déploiement avec Configuration Management](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) dans notre base de connaissances de support.
