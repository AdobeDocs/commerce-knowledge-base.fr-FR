---
title: Extension Manager n’affiche aucune extension dans Adobe Commerce 2.3.x
description: Cet article fournit une solution de contournement pour les extensions manquantes dans l’Extension Manager d’administration d’Adobe Commerce 2.3.x après avoir acheté des extensions via le Commerce Marketplace.
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Extension Manager n’affiche aucune extension dans Adobe Commerce 2.3.x

Cet article fournit une solution de contournement pour les extensions manquantes dans l’Extension Manager d’administration d’Adobe Commerce 2.3.x après avoir acheté des extensions via le Commerce Marketplace.

## Produits et versions concernés

* Version Adobe Commerce (toutes les méthodes de déploiement) 2.3.x

## Problème

Lorsque vous achetez des extensions via le Commerce Marketplace, vous ne pouvez pas les installer à l’aide de l’Extension Manager Adobe Commerce principale. Lorsque vous ajoutez vos clés d’accès et que vous effectuez une synchronisation avec Marketplace, l’Extension Manager n’affiche aucune extension.

La **solution** pour le problème consiste à utiliser la ligne de commande Installation d’Adobe Commerce, comme indiqué dans la [Installation générale de l’interface de ligne de commande](https://devdocs.magento.com/extensions/install/) de notre documentation destinée aux développeurs.

<u>Étapes à reproduire</u> :

1. Achetez une extension via le Commerce Marketplace.
1. Ajoutez les clés d’accès de votre extension et synchronisez-les avec Marketplace.
1. Accédez à la section Extension Manager de l’administrateur.

<u>Résultat attendu</u> :

L’extension apparaît dans la section Extension Manager de l’administrateur Commerce.

<u>Résultat réel</u> :

**Aucune extension n&#39;apparaît dans la section Extension Manager de l&#39;administrateur Commerce, comme dans l&#39;image ci-dessous :**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## Solution

Utilisez la ligne de commande Installation d’Adobe Commerce comme illustré dans la [Installation générale de l’interface de ligne de commande](https://devdocs.magento.com/extensions/install/) de notre documentation destinée aux développeurs.
