---
title: 'MDVA-30102 : le cache de Redis devient plein'
description: Le correctif MDVA-30102 résout le problème de saturation du cache Redis et de génération d’erreurs, ce qui entraîne des problèmes avec les pages de liste de produits (PLP) et les pages de détails du produit (PDP), comme les produits manquants. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 est installé.
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102 : le cache de Redis devient plein

Le correctif MDVA-30102 résout le problème de saturation du cache Redis et de génération d’erreurs, ce qui entraîne des problèmes avec les pages de liste de produits (PLP) et les pages de détails du produit (PDP), comme les produits manquants. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 est installé.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le cache des redis est saturé et les `maxmemory` alloués semblent insuffisants. Le cache de mise en page n’avait pas de durée de vie (TTL) et n’a pas été exclu, ce qui a entraîné une croissance du cache et l’expulsion d’autres clés de Redis. Par conséquent, toute la mémoire Redis a été allouée au cache de mise en page.

<u>Conditions préalables</u> :

* L’utilisateur doit se trouver sur Adobe Commerce 2.4 et disposer de 100 000 produits simples (le type de produit n’a pas d’importance) et de 50 catégories.
* Le cache des redis doit être configuré conformément aux étapes décrites dans le [Guide de configuration d’Adobe Commerce > Utiliser des redis pour la page Adobe Commerce et le cache par défaut](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) de notre documentation destinée aux développeurs.

<u>Étapes à reproduire</u> :

1. Parcourez tous les PDP et PLP. Vous pouvez utiliser [OWASP ZAP](https://www.zaproxy.org/) pour analyser le site.
1. Observez l’utilisation de la mémoire Redis.
1. Vérifiez également la configuration actuelle et la mémoire utilisée. Exécutez la commande suivante dans l’interface de ligne de commande. Il recherche la mémoire utilisée, le maximum de mémoire, les clés expulsées et le temps de réapprovisionnement en jours :

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>Résultats attendus</u> :

Le cache des redis ne doit pas croître rapidement.

<u>Résultats réels</u> :

Le cache Redis peut atteindre ~5 Go. Il existe une limite maximale de 8 Go de mémoire Redis, donc si vous avez des produits 1M, vous allez manquer de mémoire très rapidement.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
