---
title: "[!DNL Fastly] FAQ sur l’activation du cloaking d’origine"
description: Cette FAQ aborde les questions courantes concernant l’activation du cloaking d’origine  [!DNL Fastly] dans Adobe Commerce (mise en oeuvre complète depuis 2021).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# [!DNL Fastly] FAQ sur l’activation du cloaking d’origine

Cette FAQ aborde les questions courantes concernant l’activation du cloaking d’origine [!DNL Fastly] dans Adobe Commerce (mise en oeuvre complète depuis 2021).

## Qu’est-ce que le cloaking d’origine [!DNL Fastly] ?

Le cloaking d’origine est une fonctionnalité de sécurité qui permet à Adobe Commerce sur l’infrastructure cloud de bloquer tout trafic [!DNL non-Fastly] (pour empêcher les attaques DDoS, d’accéder à l’infrastructure cloud (origine).

## Quels sont les avantages du cloaking d’origine ?

Le cloaking d’origine est conçu pour empêcher le trafic de contourner le [!DNL Fastly Web Application Firewall] (WAF) et de le router à travers le flux strictement défini de **[!DNL Fastly]** > **équilibreur de charge** > **Instances**. Avec cette implémentation, tout le trafic est garanti via le WAF [!DNL Fastly] ainsi que le WAF interne intégré dans l’équilibreur de charge.

## Pourquoi cette activation du bouchon d’origine se produit-elle ?

Cette fonctionnalité a été initialement créée pour bénéficier à Adobe Commerce sur l’infrastructure cloud.

## Dois-je demander l’activation du cloaking d’origine pour mon projet ?

Non. Cette fonctionnalité aurait déjà dû être mise en oeuvre sur tous les projets cloud et tous les projets qui ont été configurés depuis 2021 l’auraient été par défaut.

## Le cloaking d’origine change-t-il l’adresse IP sortante ?

Non, ça ne marche pas.

## Le cloaking d’origine a-t-il un impact sur l’API REST ?

[!DNL Fastly] ne met pas en cache les appels d’API. Par conséquent, le client doit accepter la modification. Le masquage d’origine bloque uniquement les demandes qui vont directement à l’origine, par exemple :

* Production

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* Évaluation

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* StagingX

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

Dans cet exemple, le client pourra toujours accéder à l’API s’il change l’URL en ``mywebsite.com`` :

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Ce changement aura-t-il une incidence sur le déploiement et les temps d’arrêt ?

Non, cette modification aura un impact **NOT** sur le déploiement et le temps d’arrêt.

## Si le projet comporte plusieurs environnements d’évaluation, le bouclier d’origine sera-t-il appliqué à tous les environnements d’évaluation ?

Oui, si le projet comporte plusieurs environnements intermédiaires, la modification sera appliquée à tous les environnements intermédiaires.
