---
title: "MDVA-36424 : les images liées au créateur de pages disparaissent lors de l’enregistrement"
description: Le correctif MDVA-36424 résout le problème de disparition des images associées aux éléments du créateur de pages lorsque la catégorie est enregistrée pour la deuxième fois dans le cas de plusieurs sites web, l’URL de base du site par défaut étant différente de l’URL d’administration. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 est installé. L’ID de correctif est MDVA-36424. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424 : les images liées au créateur de pages disparaissent lors de l’enregistrement.

Le correctif MDVA-36424 résout le problème de disparition des images associées aux éléments du créateur de pages lorsque la catégorie est enregistrée pour la deuxième fois dans le cas de plusieurs sites web, l’URL de base du site par défaut étant différente de l’URL d’administration. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.21 est installée. L’ID de correctif est MDVA-36424. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.6

**Compatible avec les versions de Magento :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les images multimédias associées aux éléments du créateur de pages ne sont pas enregistrées si l’URL de base du serveur principal est différente de l’URL de base du storefront.

<u>Étapes à reproduire</u>:

1. Créez un deuxième site web : site web2.
1. Définissez une URL de base différente pour le site web2 (l’URL de base utilisée dans l’administration doit être différente du second site web).
1. Définir le deuxième site web comme site web par défaut (**Magasins** > *Paramètres* > **Toutes les boutiques** > Sélectionnez le deuxième site web > définissez comme *Par défaut*).
1. Accédez à la page de catégorie dans le serveur principal, puis à une vue de modification de catégorie.
1. Accédez à **Contenu** > *Description*.
1. Ajoutez une colonne au contenu et définissez une image d’arrière-plan à l’aide de la galerie multimédia.
1. Enregistrez la catégorie.
1. Accédez au **Contenu** > *Description* de nouveau, l’image enregistrée s’affiche correctement.
1. Enregistrez à nouveau la catégorie.
1. Accédez au **Contenu** > *Description*.

<u>Résultats attendus</u>:

L’image n’est pas supprimée lors de l’enregistrement de la catégorie.

<u>Résultats réels</u>:

L’image est supprimée après l’enregistrement de la catégorie une seconde fois.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
