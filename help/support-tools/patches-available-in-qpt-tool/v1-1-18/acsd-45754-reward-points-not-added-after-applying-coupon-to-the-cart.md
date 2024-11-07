---
title: "ACSD-45754 : points de récompense non ajoutés après application d’un coupon au panier"
description: Le correctif ACSD-45754 résout le problème en raison duquel les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 est installé. L’ID de correctif est ACSD-45754. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754 : points de récompense non ajoutés après application d’un coupon au panier

Le correctif ACSD-45754 résout le problème en raison duquel les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.18 est installé. L’ID de correctif est ACSD-45754. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.4.5

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les points de récompense ne sont pas ajoutés après l’application d’un coupon au panier.

<u>Conditions préalables</u> :

Le mode de paiement PayPal est configuré.

<u>Étapes à reproduire</u> :

1. Créez des taux d’exchange de point de récompense en accédant à **Magasin** > **Autres paramètres** > **Taux d’Exchange de récompense**.
1. Créez une règle de prix de panier avec un code de bon pour appliquer 100 points de récompense aux clients connectés.
1. Extrayez un produit en tant que client connecté avec PayPal et le code de coupon.
1. Vérifiez l’historique des points de récompense sous le compte client dans l’administrateur.

<u>Résultats attendus</u> :

Les points de récompense sont ajoutés au client selon la règle de prix.

<u>Résultats réels</u> :

Aucun point de récompense n’est ajouté au client.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
