---
title: "ACSD-42807 : symbole de devise personnalisée non affiché sur storefront"
description: Le correctif ACSD-42807 corrige le problème en raison duquel le symbole de devise personnalisé ne s’affiche pas sur le storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 est installé. L’ID de correctif est ACSD-42807. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807 : le symbole de devise personnalisé ne s’affiche pas sur storefront

Le correctif ACSD-42807 corrige le problème en raison duquel le symbole de devise personnalisé ne s’affiche pas sur le storefront. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.17 est installée. L’ID de correctif est ACSD-42807. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le symbole de devise personnalisé ne s’affiche pas sur le storefront.

<u>Étapes à reproduire</u>:

1. Accédez à **Magasin** > **Paramètres** > **Configurations** > **Général** > **Configuration de devise** et sélectionnez une devise personnalisée. Par exemple, **Mexique, peso**.
1. Accédez à **Magasin** > **Paramètres** > **Configurations** > **Général** > **Options de paramètres régionaux** et sélectionnez **Espagnol (Mexique)**.
1. Accédez à **Magasin** > **Symboles de devise** et configurez le symbole monétaire sur **MX$**.
1. Vérifiez le symbole de devise sur l’interface utilisateur frontale.

<u>Résultats attendus</u>:

Le symbole de devise par défaut est &quot;MX$&quot; avec une devise définie comme &quot;Mexique&quot; et un paramètre régional défini comme &quot;Espagnol (Mexique)&quot;.

<u>Résultats réels</u>:

Le symbole monétaire par défaut affiche &quot;$&quot;.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
