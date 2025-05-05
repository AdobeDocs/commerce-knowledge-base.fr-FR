---
title: Système Magento Order Management (OMS) pour l’erreur de traitement Adobe Commerce
description: Cet article fournit une solution au problème lorsque vous obtenez une erreur "getMode()" dans l’interface de ligne de commande exécutant "bin/magento oms:messages:process" dans le système Magento Order Management (OMS) pour Adobe Commerce.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Système Magento Order Management (OMS) pour l’erreur de traitement Adobe Commerce

Cet article fournit une solution au problème lorsque vous obtenez une erreur `getMode()` dans l’interface de ligne de commande exécutant `bin/magento oms:messages:process` dans le système de Magento Order Management (OMS) pour Adobe Commerce.

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

Â
Cela se produit lorsque le connecteur tente de traiter des messages `magento.inventory.source_management`. Connector tente de traiter ces messages comme s’ils étaient un message `magento.inventory.source_stock_management.update` nécessitant une valeur de mode. Comme il n&#39;y a pas de mode dans les messages `magento.inventory.source_mangement`, l&#39;erreur se produit.

## Solution

Pour résoudre le problème, exécutez l’instruction [!DNL SQL] suivante dans l’interface de ligne de commande qui supprime tous les enregistrements de la table `mcom_api_messages` :

`delete from mcom_api_messages;`

## Lecture connexe

* [ Tutoriel de configuration du connecteur OMS](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/)
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
