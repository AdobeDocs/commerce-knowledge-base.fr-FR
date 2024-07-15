---
title: 'MDVA-29954 : adresse incorrecte envoyée au nouvel e-mail d’enregistrement de l’utilisateur de la société'
description: Le correctif MDVA-29954 résout le problème en raison duquel les emails "Nouvelle demande d’enregistrement de société" et "Vous avez été lié à une société" sont envoyés à partir d’une adresse email incorrecte. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954 : adresse incorrecte envoyée au nouvel e-mail d’enregistrement des utilisateurs de la société

Le correctif MDVA-29954 résout le problème en raison duquel les emails &quot;Nouvelle demande d’enregistrement de société&quot; et &quot;Vous avez été lié à une société&quot; sont envoyés à partir d’une adresse email incorrecte. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.5-p2, 2.4.0 et 2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u> :

Installez Adobe Commerce avec B2B, avec les **fonctionnalités B2B** et la **société** activée.

<u>Étapes à reproduire</u> :

1. Cliquez sur la liste déroulante **Créer un compte** sur le storefront, puis sélectionnez **Créer un compte d’entreprise**.
1. Renseignez les champs obligatoires et enregistrez le compte.
1. Activez la **Société** à partir du serveur principal (**Client** > **Entreprises**).
1. Vérifiez l’adresse électronique que vous avez utilisée pour l’enregistrement.
1. Définissez le **mot de passe administrateur de la société** en suivant les instructions envoyées par courrier électronique.
1. Connectez-vous à l’interface avec le **mot de passe administrateur de la société**.
1. Créez un nouvel **utilisateur de la société** dans **Mon compte** > **Utilisateurs de la société** > **Ajouter un nouvel utilisateur**.
1. Accédez à **Magasins** > **Configurations** > **Adresses électroniques de magasin général** > **Contact général**, et cochez **Envoyer un courrier électronique**.
1. Accédez à l’e-mail que vous avez utilisé pour enregistrer le **nouvel utilisateur** à l’étape 7.

<u>Résultats attendus</u> :

L&#39;email &quot;Vous avez été lié à une société&quot; est envoyé à partir d&#39;une adresse email avec la même valeur que pour l&#39;**Email expéditeur** de l&#39;étape 8.

<u>Résultats réels</u> :

L&#39;e-mail &quot;Vous avez été lié à une société&quot; est envoyé à partir de l&#39;e-mail **Admin des entreprises**.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
