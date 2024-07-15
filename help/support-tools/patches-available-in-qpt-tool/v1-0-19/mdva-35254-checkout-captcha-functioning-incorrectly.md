---
title: 'MDVA-35254 : le CAPTCHA d’extraction ne fonctionne pas correctement'
description: Le correctif MDVA-35254 corrige le problème en raison duquel les champs CAPTCHA ne s’affichaient pas après un nombre infructueux de tentatives de passage en caisse pour le paiement de tiers. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-35254. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254 : le CAPTCHA d’extraction ne fonctionne pas correctement

Le correctif MDVA-35254 corrige le problème en raison duquel les champs CAPTCHA ne s’affichaient pas après un nombre infructueux de tentatives de passage en caisse pour le paiement de tiers. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 est installé. L’ID de correctif est MDVA-35254. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.1-2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

Configurez CAPTCHA :

1. Installez et configurez le fournisseur de paiement tiers (par exemple : Braintree).
1. Accédez à **Magasin > Configuration > Client > Configuration client > CAPTCHA > Forms**.
1. Sélectionnez **Ordre de passage en caisse/placement**.
1. Conservez le **nombre de tentatives infructueuses de connexion** comme valeur par défaut (valeur par défaut = *3*).
1. Connectez-vous en tant que client.
1. Ajoutez n’importe quel produit au panier.
1. Accédez à la section paiement dans le passage en caisse.
1. Sélectionnez le mode de paiement **Carte de crédit** (Exemple : Braintree).
1. Effectuez trois tentatives de paiement infructueuses.

<u>Résultats attendus</u> :

Le champ CAPTCHA s’affiche lorsque le nombre de tentatives ayant échoué est atteint.

<u>Résultats réels</u> :

Le champ CAPTCHA ne s&#39;affiche jamais, seul le message d&#39;erreur s&#39;affiche : *Veuillez fournir le code CAPTCHA et réessayer.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
