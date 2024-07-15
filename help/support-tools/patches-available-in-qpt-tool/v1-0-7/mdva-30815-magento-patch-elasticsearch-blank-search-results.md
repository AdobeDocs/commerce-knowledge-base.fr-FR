---
title: "MDVA-30815 : résultats de recherche vierges Elasticsearch"
description: Le correctif MDVA-30815 corrige le problème en raison duquel Elasticsearch affiche une page vierge lorsque les options du limiteur de résultats de recherche sont modifiées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.5.
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815 : résultats de recherche vierges Elasticsearch

Le correctif MDVA-30815 corrige le problème en raison duquel Elasticsearch affiche une page vierge lorsque les options du limiteur de résultats de recherche sont modifiées. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.3.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque vous utilisez Elasticsearch, si vous modifiez les options du limiteur de résultats de recherche, Adobe Commerce affiche une page vierge.

<u>Conditions préalables</u> :

L’Elasticsearch est **enabled**. Accédez à **STORES** > **Paramètres** > **Configuration** > **Catalogue** > **Recherche catalogue**.

<u>Étapes à reproduire</u> :

1. Accédez à votre site.
1. Recherchez un produit dans le champ de recherche principal.
1. Une fois les pages de résultats de recherche affichées, cliquez sur la dernière page dans les pages de résultats de recherche.
1. Sélectionnez **Afficher xx par page** à partir de l’option de limiteur. Assurez-vous qu’il s’agit d’une limite de nombre de résultats de recherche différente de celle configurée actuellement.

<u>Résultats attendus</u> :

La page affiche le nombre configuré de résultats de produit.

<u>Résultats réels</u> :

La page vierge s’affiche. Cette erreur est également visible dans le `var/report` : *\`&quot;0&quot;:&quot;SQLSTATE\[42000\]: Erreur de syntaxe ou violation d’accès : 1064 Vous avez une erreur dans votre syntaxe SQL ; vérifiez le manuel correspondant à votre version de serveur MySQL pour connaître la syntaxe appropriée à utiliser près&#39;\`*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
