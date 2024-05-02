---
title: "[!DNL Fastly] FAQ sur l’activation du verrouillage d’origine"
description: Cette FAQ présente les questions courantes relatives à [!DNL Fastly] activation du cloaking d’origine dans Adobe Commerce (mise en oeuvre complète depuis 2021).
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 348a1f6e455aff9ad7c562ea20c95f27c9ee0b86
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# [!DNL Fastly] FAQ sur l’activation du verrouillage d’origine

Cette FAQ présente les questions courantes relatives à [!DNL Fastly] activation du cloaking d’origine dans Adobe Commerce (mise en oeuvre complète depuis 2021).

## Présentation [!DNL Fastly] les cloaking d&#39;origine ?

Le cloaking d’origine est une fonctionnalité de sécurité qui permet à Adobe Commerce sur l’infrastructure cloud de bloquer tout type de [!DNL non-Fastly] trafic (pour empêcher les attaques DDoS, en allant à l’infrastructure cloud (origine).

## Quels sont les avantages du cloaking d’origine ?

Le masquage des origines est conçu pour empêcher le trafic de contourner la variable [!DNL Fastly Web Application Firewall] (WAF) et le routage via le flux strictement défini de **[!DNL Fastly]** > **Équilibreur de charge** > **Instances**. Avec cette mise en oeuvre, tout le trafic est garanti par la variable [!DNL Fastly] WAF ainsi que le WAF interne intégré dans l’équilibreur de charge.

## Pourquoi cette activation du bouchon d’origine se produit-elle ?

Cette fonctionnalité a été initialement créée pour bénéficier à Adobe Commerce sur l’infrastructure cloud.

## Dois-je demander l’activation du cloaking d’origine pour mon projet ?

Non. Cette fonctionnalité aurait déjà dû être mise en oeuvre sur tous les projets cloud et tous les projets qui ont été configurés depuis 2021 l’auraient été par défaut. Cependant, vous pouvez demander que le cloaking d’origine soit désactivé pour votre projet en procédant comme suit : [envoi d’une demande d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Le cloaking d’origine change-t-il l’adresse IP sortante ?

Non, ça ne marche pas.

## Le cloaking d’origine a-t-il un impact sur l’API REST ?

[!DNL Fastly] ne met pas en cache les appels d’API. Par conséquent, le client doit accepter la modification. Le masquage d’origine bloque uniquement les demandes qui vont directement à l’origine, par exemple :

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

Dans cet exemple, le client pourra toujours accéder à l’API s’il change l’URL en ``mywebsite.com``:

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## Ce changement aura-t-il une incidence sur le déploiement et les temps d’arrêt ?

Non, cette modification va **NOT** impacter le déploiement et les temps d’arrêt.

## Si le projet comporte plusieurs environnements d’évaluation, le bouclier d’origine sera-t-il appliqué à tous les environnements d’évaluation ?

Oui, si le projet comporte plusieurs environnements intermédiaires, la modification sera appliquée à tous les environnements intermédiaires.
