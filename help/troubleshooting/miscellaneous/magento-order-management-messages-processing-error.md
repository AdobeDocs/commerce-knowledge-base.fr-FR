---
title: Système Magento Order Management (OMS) pour l’erreur de traitement Adobe Commerce
description: Cet article fournit une solution au problème lorsque vous obtenez une erreur "getMode()" dans l’interface de ligne de commande exécutant "bin/magento oms".:messages:dans le système de Magento Order Management (OMS) pour Adobe Commerce.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Système Magento Order Management (OMS) pour l’erreur de traitement Adobe Commerce

Cet article fournit une solution au problème lorsque vous obtenez une `getMode()` erreur dans l’exécution de l’interface de ligne de commande. `bin/magento oms:messages:process` dans le système Magento Order Management (OMS) pour Adobe Commerce.

## Produits et versions concernés

Cette erreur se produit lors de l’utilisation des versions 3.1.1 et 3.2.0 de MCOM Connector. Ce problème est résolu dans MCOM Connector 3.3.0. Il n’est pas spécifique à une version MDC ou MOM.

## Problème

Lors de l’exécution de la commande suivante dans l’interface de ligne de commande :

`bin/magento oms:messages:process`

Un message d’erreur similaire au suivant est généré dans l’interface de ligne de commande :

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## Cause

Cela se produit lorsque le connecteur tente de traiter `magento.inventory.source_management` messages. Le connecteur tente de traiter ces messages comme s’ils étaient un `magento.inventory.source_stock_management.update` qui ne nécessite pas de valeur de mode. Parce qu’il n’existe aucun mode dans la variable `magento.inventory.source_mangement` , l’erreur se produit.

## Solution

Pour résoudre le problème, exécutez l’instruction SQL suivante dans l’interface de ligne de commande, qui supprime tous les enregistrements de la variable `mcom_api_messages` table :

`delete from mcom_api_messages;`

## Lecture connexe

Voir les documents OMS [Tutoriel sur la configuration du connecteur OMS](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).
