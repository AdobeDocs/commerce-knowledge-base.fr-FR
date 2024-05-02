---
title: 'MDVA-28511 : les lettres accentuées pendent les paiements de flux de production'
description: Le correctif MDVA-28511 résout le problème lorsque les paiements via **Payflow Pro** ne sont pas terminés pour les noms de clients avec des lettres accentuées.
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511 : lettres accentuées pendent les paiements de flux de production

Le correctif MDVA-28511 résout le problème lors des paiements par le biais de **Payflow Pro** ne complétez pas les noms de clients avec des lettres accentuées.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.14 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.3.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Condition requise</u>:

Activer **Payflow Pro** mode de paiement par carte de crédit.

<u>Étapes à reproduire</u>:

1. Ajoutez un produit au panier et passez à la page de passage en caisse.
1. Définissez un nom de client avec des lettres accentuées. (Exemple : **Ãtienne Ãillin**)
1. Passez aux étapes de paiement.
1. Sélectionner **Payflow Pro** as **Carte de crédit** et renseignez les détails de la carte de crédit.
1. Cliquez sur le bouton **Passer commande** bouton .

<u>Résultats attendus</u>:

La commande se termine sans problème, comme prévu.

<u>Résultats réels</u>:

La commande ne se termine pas et les journaux affichent une erreur similaire à celle-ci :

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
