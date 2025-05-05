---
title: Délai d’exécution plus long pour les points d’entrée web asynchrones en bloc après le correctif de sécurité APSB25-08
description: Cet article fournit un correctif pour le problème où les requêtes POST rest/all/async/bulk/V1/products pour plus de 1 000 entrées subissent une augmentation significative du temps d’exécution après l’application du correctif de sécurité APSB25-08.
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
source-git-commit: fce7f860b9fddd694b311ffc4acd56a48c06e14b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Délai d’exécution plus long pour tous les points d’entrée web asynchrones en bloc après le correctif de sécurité APSB25-08

Cet article fournit un correctif pour tous les points d’entrée web asynchrones en bloc, tels que les `POST rest/all/async/bulk/V1/products` comportant plus de 1 000 entrées, qui présentent des temps d’exécution considérablement plus longs après l’application du correctif de sécurité APSB25-08.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p9

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8

## Problème

Après l’application du correctif de sécurité APSB25-08, les requêtes `POST rest/all/async/bulk/V1/products` comportant plus de 1 000 entrées prennent beaucoup plus de temps à s’exécuter.

<u>Procédure à suivre </u> :

1. Envoyez une requête `POST rest/all/async/bulk/V1/products` comportant plus de 1 000 entrées (le nom, le SKU et la description sont suffisants).
1. Notez la durée de la requête.
1. Appliquez le correctif de sécurité APSB25-08 et nettoyez les données générées et le cache à l’aide de `se:di:co`.
1. Exécutez `bin/magento c:f`.
1. Accédez à storefront pour vous assurer que le cache et les fichiers générés sont en place.
1. Répétez la requête de l’étape 1.
1. Notez l’augmentation du temps nécessaire à la requête.
1. Supprimez le correctif de sécurité APSB25-08, videz le cache, régénérez le code et répétez la requête de l’étape 1 pour confirmer que le temps d’exécution revient à la normale. (Facultatif)

<u>Résultats attendus</u> :

Le temps d’exécution des requêtes `async/bulk` a considérablement augmenté après l’application du correctif de sécurité.

<u>Résultats réels</u> :

Le temps d’exécution des requêtes `async/bulk` n’aurait pas dû augmenter de manière significative après l’application du correctif de sécurité, bien qu’une certaine augmentation du temps soit attendue.

## Solution

Pour résoudre ce problème, appliquez le [AC-14078-2-4x-composer-patch.zip](assets/AC-14078-2-4x-composer-patch.zip).

## Application du correctif

Décompressez le fichier et consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=fr) dans notre base de connaissances d’assistance pour obtenir des instructions.

## Lecture connexe

* [Mise à jour de sécurité disponible pour Adobe Commerce - APSB25-08](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
