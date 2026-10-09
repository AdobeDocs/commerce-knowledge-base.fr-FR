---
title: L’[!DNL CLI] « Magento-cloud » n’affiche pas d’environnement actif
description: Cet article décrit un problème Adobe Commerce connu en raison duquel le [!DNL CLI] « Magento-cloud » (outil de ligne de commande) n’affiche pas d’environnement actif.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%
---
# L’[!DNL CLI] `Magento-cloud` n’affiche pas d’environnement actif

## Problème

Il existe plusieurs environnements actifs et vous essayez d’interagir avec un environnement en exécutant une commande `Magento-cloud` [!DNL CLI] (outil de ligne de commande). (Par exemple : `ssh`, `db:size`, `db:sql`, etc.)
Cependant, l’invite de choix de l’environnement souhaité ne répertorie pas cet environnement. (Par exemple : l’environnement d’intégration)

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## Cause

L’environnement peut ne pas être disponible en raison d’un déploiement en cours, bloqué ou en échec.

## Solution

Vous devrez spécifier manuellement l’environnement avec l’indicateur `e|-environment`.

1. Recherchez la liste des environnements actifs et notez les noms d’environnement :

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

&#x200B;2. Spécifiez l’identifiant de l’environnement à l’aide de la commande :

`magento-cloud ssh -e integration`
