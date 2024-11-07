---
title: Site en mode de maintenance mais disponible pour les clients
description: Cet article fournit un correctif pour l’activation du mode de maintenance (problème d’infrastructure cloud d’Adobe Commerce), mais le storefront est toujours disponible pour les clients.
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Site en mode de maintenance mais disponible pour les clients

Cet article fournit un correctif pour l’activation du mode de maintenance (problème d’infrastructure cloud d’Adobe Commerce), mais le storefront est toujours disponible pour les clients.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

<u>Étapes à reproduire :</u>

1. Activez le mode de maintenance du site.
1. Accédez au storefront.

<u>Résultat attendu :</u>

La page de maintenance s’affiche.

<u>Résultat réel :</u>

Les pages de storefront s’affichent comme d’habitude.

## Cause

Les pages sont toujours mises en cache, de sorte que la page de maintenance ne s’affiche pas.

## Solution au site visible malgré le fait qu’il soit en mode de maintenance

1. SSH à votre environnement.
1. Exécutez la commande `php bin/magento cache:clean`.

## Lecture connexe

[Activez ou désactivez le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs.
