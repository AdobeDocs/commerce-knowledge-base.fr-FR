---
title: 'MDVA-31006 : erreur 10415 des commandes en double paypal'
description: Le correctif MDVA-31006 corrige le problème en raison duquel l’utilisation du paiement de paiement de paiement PayPal Express crée des commandes en double avec une erreur 10415. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé. Le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006 : erreur 10415 des commandes en double de Paypal

Le correctif MDVA-31006 corrige le problème en raison duquel l’utilisation du paiement de paiement de paiement PayPal Express crée des commandes en double avec une erreur 10415. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 est installé. Le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 - 2.4.0

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur n’est pas envoyé sur la page de succès des commandes Adobe Commerce. Il actualise donc la page vierge et la deuxième commande est passée, ce qui entraîne la duplication des commandes.

<u>Conditions préalables</u> :

* Adobe Commerce est installé.
* Le paiement du paiement du passage en caisse PayPal Express est configuré.
* Connectez-vous à l’administrateur Commerce. Accédez à **Magasins** > **Configuration** > **Ventes** > **Méthodes de paiement** > sélectionnez **Paypal Express Checkout** > **Configurer** > **Paramètres avancés** > **Ignorer l’étape de révision des commandes** > *No* 7}.

<u>Étapes à reproduire</u> :

1. Connectez-vous en tant qu’utilisateur.
1. Sélectionnez un élément et cliquez sur **Ajouter au panier**.
1. Cliquez sur le panier et cliquez sur **Passez en caisse**.
1. Passez à la fenêtre PayPal Express et effectuez un paiement.
1. Vous êtes redirigé vers la page de révision des commandes d’Adobe Commerce.
1. Appuyez sur le bouton **Passer commande** .
1. Émuler une erreur système en raison de problèmes d’infrastructure du serveur. L’utilisateur voit une page vierge.
1. Actualisez la page.

<u>Résultats attendus</u> :

* Le client est redirigé vers la page Révision de la commande et voit un message d’erreur &quot;*&quot;. Une transaction de paiement réussie a déjà été effectuée. Vérifiez si la commande a été passée.*&quot;
* Dans le fichier payment.log, situé dans `/var/log/payment.log`, il y a une erreur 10415, mais une seule commande a été créée.

<u>Résultats réels</u> :

* Comme le client n’est pas envoyé sur la page de succès de la commande Adobe Commerce, il actualise la page vierge et une deuxième commande est placée, de sorte que deux commandes dupliquées sont créées.
* Dans le fichier payment.log, qui se trouve dans `/var/log/payment.log`, il y a une erreur 10415.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
