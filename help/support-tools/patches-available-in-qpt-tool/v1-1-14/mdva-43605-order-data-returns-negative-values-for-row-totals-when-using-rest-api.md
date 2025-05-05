---
title: 'MDVA-43605 : les données de commande renvoient des valeurs négatives pour les totaux de lignes lors de l’utilisation de l’API REST'
description: Le correctif MDVA-43605 corrige le problème en raison duquel les données de commande renvoyaient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-43605. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 8a679e85-1681-42c3-b072-18797198bdc4
feature: REST, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# MDVA-43605 : Les données de commande renvoient des valeurs négatives pour les totaux de lignes lors de l’utilisation de l’API REST.

Le correctif MDVA-43605 corrige le problème en raison duquel les données de commande renvoyaient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-43605. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les données de commande renvoient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API REST.

<u>Étapes à reproduire</u> :

1. Activez la livraison gratuite.
1. Accédez à **Configuration** > **Catalogue** > **Price** > et définissez Périmètre du prix du catalogue = site web.
1. Accédez à **Configuration** > **Ventes** > **Taxe** et mettez à jour :
   * Classe fiscale pour l’expédition = Produits taxables
   * Paramètres de calcul :
      * Prix du catalogue = TVA incluse
      * Prix de livraison = Prix inclus
      * Application De La Remise Sur Les Prix = Impôt Inclus
   * Paramètres d’affichage du prix : taxes comprises (tous les champs)
   * Paramètres d’affichage du panier : taxes incluses (tous les champs)
   * Commandes, factures, notes de crédit :
      * Afficher le montant de la livraison = Taxe incluse
1. Créer un taux d&#39;imposition pour les Etats-Unis (Etat = &#39;*&#39;), Taux % = 24,00
1. Créez une règle fiscale avec le taux de taxe ci-dessus.
1. Créez une règle de prix de panier avec un coupon spécifique, et Réduction = 50 $ du montant fixe pour l’ensemble du panier.
1. Créez quatre produits aux prix suivants : 8,90 $, 5,90 $, 6,90 $ et 5,95 $.
1. Créez une commande d’administration comprenant quatre de ces produits à l’aide du code de bon créé à l’étape précédente. Utilisez la livraison gratuite.
1. Le paiement ne doit pas être obligatoire, car le code du coupon couvre le total du panier.
1. Récupérez la commande qui vient d’être créée via le point de terminaison de l’API REST :

   ```json
   GET rest/V1/orders/1
   ```

<u>Résultats attendus</u> :

Les valeurs `base_row_total` et `base_row_total_incl_tax` de la réponse sont nulles.

<u>Résultats réels</u> :

Les champs `base_row_total` et `base_row_total_incl_tax` de la réponse ont des valeurs négatives.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
