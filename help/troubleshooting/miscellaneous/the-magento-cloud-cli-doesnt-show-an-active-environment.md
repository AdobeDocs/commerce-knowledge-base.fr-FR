---
title: Le `Magento-cloud` [!DNL CLI]  n’affiche pas d’environnement actif
description: Cet article décrit un problème Adobe Commerce connu où "Magento-cloud" [!DNL CLI]  (outil de ligne de commande) n’affiche pas d’environnement actif.
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
source-git-commit: 5eac8bb54e205eff6a96e279295cd12db1009f0a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# `Magento-cloud` [!DNL CLI] n&#39;affiche pas d&#39;environnement actif

## Problème

Il existe plusieurs environnements actifs et vous tentez d’interagir avec un environnement en exécutant une commande `Magento-cloud` [!DNL CLI] (outil de ligne de commande). (Par exemple : `ssh`, `db:size`, `db:sql`, etc.)
Toutefois, l’invite permettant de choisir l’environnement souhaité ne répertorie pas cet environnement. (Par exemple : l’environnement d’intégration)

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

1. Recherchez la liste des environnements actifs et notez les noms des environnements :

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

2. Spécifiez l’identifiant de l’environnement à l’aide de votre commande :

`magento-cloud ssh -e integration`
