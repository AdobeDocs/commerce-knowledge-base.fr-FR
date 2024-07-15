---
title: 'MDVA-30845 : la déconnexion de la connexion au fournisseur d’expédition échoue'
description: Le correctif MDVA-30845 corrige le problème en raison duquel l’erreur *Désolé, aucun guillemet n’est disponible pour cette commande pour l’instant* s’affiche lorsque vous ne vous connectez pas à UPS XML/USPS/DHL pendant le passage en caisse, et aucune autre méthode de livraison n’est disponible. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.2.
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845 : la connexion au fournisseur d’expédition échoue

Le correctif MDVA-30845 corrige le problème en raison duquel l&#39;erreur *Désolé, aucun guillemet n&#39;est disponible pour cette commande à l&#39;heure actuelle* s&#39;affiche lorsque vous ne vous connectez pas à UPS XML/USPS/DHL pendant le passage en caisse, et aucune autre méthode de livraison n&#39;est disponible. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.3.5-p2.

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.5-2.3.6.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Pendant le passage en caisse, l&#39;erreur *Désolé, aucun guillemet n&#39;est disponible pour cette commande pour l&#39;instant* s&#39;affiche lorsque vous ne vous connectez pas à UPS XML/USPS/DHL, et aucune autre méthode de livraison n&#39;est disponible.

<u>Étapes à reproduire :</u>

1. Créez un produit.
1. Activez et configurez le mode de livraison XML UPS.
1. Ajoutez le produit au panier au premier plan du magasin.
1. Assurez-vous que les méthodes d&#39;expédition UPS et l&#39;expédition à taux fixe sont disponibles.
1. Modifiez votre fichier d’hôtes afin d’empêcher l’USP de se connecter à sa passerelle.
1. Au niveau du magasin, essayez d’obtenir des tarifs et passez à nouveau à la caisse.

<u>Résultat réel :</u>

*Désolée, aucune entre guillemets n&#39;est disponible pour cette commande à l&#39;heure actuelle*, et l&#39;expédition à taux fixe n&#39;est pas disponible.

<u>Résultat attendu :</u>

Aucun message d’erreur n’est affiché et l’expédition à taux fixe est disponible.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.


## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
