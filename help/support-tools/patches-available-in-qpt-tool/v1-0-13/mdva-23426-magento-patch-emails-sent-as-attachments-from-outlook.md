---
title: 'Correctif du Magento MDVA-23426 : emails envoyés en tant que pièces jointes depuis Outlook'
description: Le correctif du Magento MDVA-23426 corrige le problème d’envoi des emails en tant que pièces jointes par le Magento à partir de MS Outlook. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 est installé. Veuillez noter que le problème a été corrigé dans Magento 2.3.5.
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Correctif du Magento MDVA-23426 : emails envoyés en tant que pièces jointes depuis Outlook

Le correctif du Magento MDVA-23426 corrige le problème d’envoi des emails en tant que pièces jointes par le Magento à partir de MS Outlook. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.13 est installée. Veuillez noter que le problème a été corrigé dans Magento 2.3.5.

## Produits et versions concernés

**Le correctif est créé pour la version du Magento :** Magento Commerce Cloud 2.3.3.

**Compatible avec les versions de Magento :** Magento Commerce et Magento Commerce Cloud 2.3.3 - 2.3.4-p2.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les emails sont reçus avec un corps vide et le contenu est inclus en tant que pièce jointe.

<u>Conditions préalables :</u> Outlook/Exchange est utilisé comme combinaison client/serveur.

<u>Étapes à reproduire :</u> 1. Envoyez une commande, la notification de commande ou la notification d&#39;envoi est envoyée.2. L&#39;email est reçu.

<u>Résultat réel :</u> Le message électronique s’affiche avec un corps vide et le contenu est inclus en tant que pièce jointe avec un libellé ATT\* au message électronique. <u>Résultat attendu :</u>

L&#39;email est reçu sans pièce jointe et le corps de l&#39;email contient le contenu.

## Appliquer le correctif

Pour savoir comment appliquer un correctif QPT, utilisez les liens suivants en fonction de votre produit Magento :

* Magento Commerce : DevDocs [Application de correctifs à l’aide de l’outil Correctifs de qualité](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) .
* Magento Commerce Cloud : DevDocs [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) .

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) .
* [Correctif pour un problème de Magento avec l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) .

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
