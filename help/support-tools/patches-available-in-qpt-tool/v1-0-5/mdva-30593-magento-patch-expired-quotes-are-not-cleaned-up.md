---
title: "Correctif MDVA-30593 : les guillemets expirés ne sont pas nettoyés"
description: Le correctif MDVA-30593 résout le problème en raison duquel les guillemets qui ont expiré selon le paramètre **Durée de vie des citations** ne sont pas nettoyés. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.4.
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Correctif MDVA-30593 : les guillemets expirés ne sont pas nettoyés

Le correctif MDVA-30593 résout le problème où les guillemets qui ont expiré selon le paramètre **Durée de vie des guillemets**, ne sont pas nettoyés. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.4.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0-2.3.3.x

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les citations, qui ont expiré selon le paramètre **Durée de vie des citations**, ne sont pas nettoyées.

<u>Étapes à reproduire :</u>

1. Dans l’administrateur Commerce, accédez à **Magasins** > **Configuration** > **Ventes** > **Passage en caisse** > **Panier**.
1. Définissez **Durée de vie des citations (jours)** = *1*
1. Enregistrez la configuration et effacez le cache.
1. Connectez-vous en tant que client.
1. Ajoutez un produit au panier.
1. Au bout d&#39;une journée, retournez dans le panier.

<u>Résultat attendu :</u>

Le prix est effacé et le produit est retiré du panier, car l’ancien prix n’est plus valide.

<u>Résultat réel :</u>

Le produit est toujours dans le panier.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
