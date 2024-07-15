---
title: Problèmes de libellés '[!UICONTROL salesRule] lors de la mise à niveau à partir des versions &lt; 2.4.5'
description: Appliquez un correctif pour résoudre les problèmes **[!UICONTROL salesRule]** lors de la mise à niveau à partir des versions Adobe Commerce &lt; 2.4.5.
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Problèmes de libellés **[!UICONTROL salesRule]** lors de la mise à niveau à partir des versions &lt; 2.4.5

La fonctionnalité d&#39;évaluation des étiquettes **[!UICONTROL salesRule]** a été introduite dans Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). Cette modification peut entraîner des problèmes lorsque vous effectuez une mise à niveau d’Adobe Commerce &lt; 2.4.5 vers n’importe quelle version >= 2.4.5. Après la mise à niveau, il est possible que **[!UICONTROL salesRule]** libellés ne correspondent pas. Pour résoudre le problème, un correctif doit être appliqué juste après la mise à niveau vers une version plus récente d’Adobe Commerce.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud &lt; 2.4.5

## Correctif

Utilisez le correctif ci-joint suivant :

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## Comment appliquer le correctif

1. Suivez les étapes décrites dans la section [Effectuer une mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) du guide Commerce.
1. Appliquez le correctif joint avant la phase **[!UICONTROL Update metadata]**.
(Vous pouvez également appliquer le correctif après avoir terminé la phase **[!UICONTROL Update metadata]**, mais vous devez exécuter à nouveau `bin/magento setup:upgrade`).
1. Passez au reste des étapes de [Effectuer une mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
