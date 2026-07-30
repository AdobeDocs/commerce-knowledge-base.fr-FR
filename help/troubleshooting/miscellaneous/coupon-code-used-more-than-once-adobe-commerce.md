---
title: Le coupon à usage unique est utilisé plusieurs fois, Adobe Commerce
description: Cet article fournit une solution au problème de fonctionnement incorrect des coupons de règle de prix de panier. Les commerçants configurent un coupon à usage unique et les clients peuvent l'utiliser plusieurs fois.
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Le coupon à usage unique est utilisé plusieurs fois, Adobe Commerce

Cet article fournit une solution au problème de fonctionnement incorrect des coupons de règle de prix de panier. Les commerçants configurent un coupon à usage unique et les clients peuvent l&#39;utiliser plusieurs fois.


## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 et versions ultérieures

## Problème

Les commerçants configurent un coupon à usage unique et les clients peuvent l&#39;utiliser plusieurs fois.

<u>Procédure à suivre </u> :

1. Créez un coupon et configurez-le pour une utilisation unique.
1. Passer en caisse.
1. Utilisez le bon que vous venez de créer.
1. Passez à nouveau à la caisse et utilisez le même coupon.

<u>Résultat attendu </u> :

Le coupon ne peut être utilisé qu&#39;une seule fois. Un message s’affiche : *Le code de coupon « COUPON_NAME » n’est pas valide*.

<u>Résultat réel</u> :

Le coupon peut être utilisé plusieurs fois.


## Cause

Les commerçants n’ont pas `sales.rule.update.coupon.usage` client configuré et en cours d’exécution, ce qui entraîne un comportement incorrect.

## Solution

Ajoutez le client `sales.rule.update.coupon.usage` au fichier `app/etc/env.php`.

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

Pour obtenir des instructions détaillées, consultez [Gestion des files d’attente des messages > Configuration](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration) dans la documentation destinée aux développeurs.

## Lecture connexe

[Présentation des files d’attente des messages](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) dans notre documentation destinée aux développeurs.
