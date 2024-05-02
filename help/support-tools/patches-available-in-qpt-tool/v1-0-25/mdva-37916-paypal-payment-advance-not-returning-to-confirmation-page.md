---
title: 'MDVA-37916 : PayPal payment Advanced not return to page de confirmation'
description: Le correctif de qualité MDVA-37916 pour Adobe Commerce corrige le problème de paiement de PayPal Advanced qui ne revenait pas à la page de confirmation après paiement. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 est installé. L’ID de correctif est MDVA-37916. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916 : les paiements payants avancés ne reviennent pas à la page de confirmation

Le correctif de qualité MDVA-37916 pour Adobe Commerce corrige le problème de paiement de PayPal Advanced qui ne revenait pas à la page de confirmation après paiement. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.25 est installée. L’ID de correctif est MDVA-37916. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
Adobe Commerce sur l’infrastructure cloud 2.3.6-p1

**Compatible avec les versions d’Adobe Commerce :**
Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.6-2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le client n’est pas redirigé vers la page de confirmation du paiement après paiement lors de l’utilisation de la méthode avancée Paiements de paiement PayPal .

<u>Étapes à reproduire</u>: [Screencast](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. Ajoutez le produit au panier et accédez à l’étape de paiement de la page de passage en caisse.
1. Sélectionner **Carte de crédit (avancé)** option de paiement.
1. Cliquez sur **Continuer** pour afficher l’iframe avec le formulaire de paiement.
1. Remplissez le formulaire de paiement avec les détails de la carte de crédit sandbox.
   * Numéro de carte : 444 333 222 111 ou 411 11 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
   * Date d’expiration : 12/23
   * C.S. : 123
1. Cliquez sur **Payer maintenant**.

<u>Résultats attendus</u>:

Une fois le paiement traité et le paiement réussi, vous êtes redirigé vers la page de confirmation de commande.

<u>Résultats réels</u>:

* Vous n’êtes PAS redirigé vers la page de confirmation de commande.
* Mais l’ordre a été créé dans Adobe Commerce.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de qualité dans notre base de connaissances de support, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) de notre base de connaissances en matière de soutien.
