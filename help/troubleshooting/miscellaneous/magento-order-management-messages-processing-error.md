---
title: Erreur de traitement de Magento Order Management System (OMS) pour Adobe Commerce
description: Cet article fournit une solution au problème d’erreur « getMode() » dans l’interface de ligne de commande exécutant « bin/magento oms:messages:process » dans Magento Order Management System (OMS) pour Adobe Commerce.
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%
---
# Erreur de traitement de Magento Order Management System (OMS) pour Adobe Commerce

Cet article fournit une solution au problème d’erreur `getMode()` dans le `bin/magento oms:messages:process` d’exécution de l’interface de ligne de commande de Magento Order Management System (OMS) pour Adobe Commerce.

## Produits et versions concernés

Cette erreur se produit lors de l’utilisation des versions 3.1.1 et 3.2.0 de MCOM Connector. Il est résolu dans MCOM Connector 3.3.0. Il n’est pas spécifique à une version MDC ou MOM.

## Problème

Lors de l’exécution de la commande suivante dans l’interface de ligne de commande :

`bin/magento oms:messages:process`

Un message d’erreur similaire au suivant apparaît dans l’interface de ligne de commande :

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
Cela se produit lorsque le connecteur tente de traiter des messages `magento.inventory.source_management`. Le connecteur tente de traiter ces messages comme s’il s’agissait d’un message `magento.inventory.source_stock_management.update` qui ne nécessite pas de valeur de mode. Comme il n’y a pas de mode dans les messages `magento.inventory.source_mangement`, l’erreur se produit.

## Solution

Pour résoudre le problème, exécutez l’instruction [!DNL SQL] suivante dans l’interface de ligne de commande, qui supprime tous les enregistrements de la table `mcom_api_messages` :

`delete from mcom_api_messages;`

## Lectures connexes

* Documents OMS [tutoriel sur la configuration du connecteur OMS](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/)
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
