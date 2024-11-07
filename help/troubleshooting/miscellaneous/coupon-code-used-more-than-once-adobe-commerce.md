---
title: Le coupon pour une seule utilisation est utilisé plusieurs fois, Adobe Commerce
description: Cet article fournit une solution au problème lorsque les bons de règle de prix de panier ne fonctionnent pas correctement. Les commerçants configurent un coupon à usage unique et les clients peuvent l’utiliser plusieurs fois.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Le coupon pour une seule utilisation est utilisé plusieurs fois, Adobe Commerce

Cet article fournit une solution au problème lorsque les bons de règle de prix de panier ne fonctionnent pas correctement. Les commerçants configurent un coupon à usage unique et les clients peuvent l’utiliser plusieurs fois.


## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) version 2.4.3 et ultérieure

## Problème

Les commerçants configurent un coupon à usage unique et les clients peuvent l’utiliser plusieurs fois.

<u>Étapes à reproduire</u> :

1. Créez un coupon et configurez-le pour qu’il soit unique.
1. Passez à la caisse.
1. Utilisez le coupon que vous venez de créer.
1. Passez à nouveau en caisse et utilisez le même coupon.

<u>Résultat attendu</u> :

Le coupon ne peut être utilisé qu&#39;une seule fois. Un message s&#39;affiche : *Le code de coupon &quot;COUPON_NAME&quot; n&#39;est pas valide*.

<u>Résultat réel</u> :

Le coupon peut être utilisé plusieurs fois.


## Cause

Les commerçants n’ont pas de consommateur `sales.rule.update.coupon.usage` configuré et en cours d’exécution, ce qui entraîne un comportement incorrect.

## Solution

Ajoutez le consommateur `sales.rule.update.coupon.usage` au fichier `app/etc/env.php`.

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

Pour obtenir des instructions détaillées, reportez-vous à la section [Gestion des files d’attente de messages > Configuration](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) de notre documentation destinée aux développeurs.

## Lecture connexe

[Présentation des files d’attente de messages](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) dans notre documentation destinée aux développeurs.
