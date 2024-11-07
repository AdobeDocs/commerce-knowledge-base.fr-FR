---
title: Échec du chargement du site en raison du mode de maintenance activé
description: "Cet article fournit un correctif pour les cas où votre site ne se charge pas en raison de l’activation ou de la désactivation automatique du mode de maintenance. Vous pouvez recevoir un message d’erreur : *Service temporairement indisponible Le serveur ne peut temporairement pas traiter votre demande en raison de problèmes de temps d’arrêt de maintenance ou de capacité.*"
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Échec du chargement du site en raison du mode de maintenance activé

Cet article fournit un correctif pour les cas où le mode de maintenance n’est pas chargé en raison de l’activation ou de la désactivation automatique du mode de maintenance. Vous pouvez recevoir un message d’erreur : *Service temporairement indisponible Le serveur est temporairement incapable de traiter votre demande en raison de problèmes de temps d’arrêt de maintenance ou de capacité.*

## Versions et produits concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x
* Adobe Commerce on-premise 2.2.x, 2.3.x

## Problème

Le mode de maintenance fait partie du processus de déploiement. Cependant, si elle a été activée automatiquement et n’a pas été désactivée, ou si le mode de maintenance activé manuellement par le commerce et a oublié de le désactiver, cela peut entraîner un échec du déploiement.

## Cause

Le fait que le mode de maintenance soit activé empêche le chargement du site.

## Solution

Pour vérifier l’état actuel du mode de maintenance, exécutez la commande suivante à partir de l’interface de ligne de commande :

```
bin/magento maintenance:status
```

Pour désactiver le mode de maintenance, exécutez la commande suivante dans l’interface de ligne de commande :

```
bin/magento maintenance:disable
```

## Lecture connexe

Pour savoir quand utiliser le mode de maintenance, reportez-vous à la section [Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) de notre documentation destinée aux développeurs.
