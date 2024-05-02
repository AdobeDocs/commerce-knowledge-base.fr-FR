---
title: '[!UICONTROL salesRule] problèmes de libellés lors de la mise à niveau à partir des versions &lt; 2.4.5'
description: Appliquez un correctif pour traiter le **[!UICONTROL salesRule]Problèmes ** lors de la mise à niveau à partir des versions d’Adobe Commerce &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** problèmes de libellés lors de la mise à niveau des versions &lt; 2.4.5

La variable **[!UICONTROL salesRule]** la fonctionnalité d’évaluation des étiquettes a été introduite dans Adobe Commerce. [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). Cette modification peut entraîner des problèmes lorsque vous effectuez une mise à niveau d’Adobe Commerce &lt; 2.4.5 vers n’importe quelle version >= 2.4.5. Après la mise à niveau, il est possible que **[!UICONTROL salesRule]** les libellés ne correspondent pas. Pour résoudre le problème, un correctif doit être appliqué juste après la mise à niveau vers une version plus récente d’Adobe Commerce.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud &lt; 2.4.5

## Correctif

Utilisez le correctif ci-joint suivant :

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Comment appliquer le correctif

1. Suivez les étapes décrites dans la section [Effectuer une mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) dans le guide Commerce.
1. Appliquez le correctif joint avant la **[!UICONTROL Update metadata]** phase.
(Vous pouvez également appliquer le correctif une fois que vous avez terminé la **[!UICONTROL Update metadata]** mais ensuite vous devez exécuter `bin/magento setup:upgrade` une fois de plus).
1. Passez au reste des étapes de la section [Effectuer une mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
