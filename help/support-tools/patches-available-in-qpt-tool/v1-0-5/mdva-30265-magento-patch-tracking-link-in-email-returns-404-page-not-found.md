---
title: '''MDVA-30265 : lien de tracking dans les retours d''email 404 Page introuvable'''
description: Le correctif MDVA-30265 résout le problème de l’erreur "404 Page introuvable" lorsque le client clique sur le lien de suivi de l’expédition dans l’email de confirmation de commande. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265 : lien de suivi dans les retours d’email 404 Page introuvable

Le correctif MDVA-30265 résout le problème de l’erreur &quot;404 Page introuvable&quot; lorsque le client clique sur le lien de suivi de l’expédition dans l’email de confirmation de commande. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 à 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une fois la livraison créée pour une commande passée, un email contenant des informations de tracking et un lien pour suivre la commande est envoyé au client. Cependant, lorsque le client clique sur le lien de suivi de l’expédition dans l’email, cela renvoie une erreur &quot;404 Page introuvable&quot;.

<u>Étapes à reproduire</u> :

1. Installez Adobe Commerce 2.4. Pour les étapes, reportez-vous à la section [Installation d’Adobe Commerce à l’aide du compositeur](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) de notre documentation destinée aux développeurs.
1. passé une commande ;
1. Accédez au panneau d’administration > **Ventes** > **Commandes**. Recherchez l’ordre que vous venez de créer et ouvrez-le.
1. Créez une envoi et ajoutez un numéro de tracking (Carrier = Valeur personnalisée). Pour les étapes, reportez-vous à [Order Management > Création d’un envoi](https://docs.magento.com/user-guide/sales/shipments-create.html) dans notre guide d’utilisation.
1. Vous recevez un email. Cliquez sur le lien de tracking pour vérifier qu&#39;il fonctionne.
1. Créez une facture. Pour les étapes, reportez-vous à [Order Management > Création d&#39;une facture](https://docs.magento.com/user-guide/sales/invoice-create.html) dans notre guide d&#39;utilisation. Cliquez à nouveau sur le lien de tracking ci-dessus.

<u>Résultats attendus</u> :

Le lien de tracking doit fonctionner même après la création de la facture.

<u>Résultats réels</u> :

Après la création de la facture, le lien de tracking ne fonctionne pas et renvoie une page d&#39;erreur &quot;404 Page introuvable&quot;.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
