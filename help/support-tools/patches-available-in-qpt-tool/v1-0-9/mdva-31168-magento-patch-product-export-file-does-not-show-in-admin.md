---
title: 'Correctif MDVA-31168 : le fichier d’exportation de produit ne s’affiche pas dans l’administration'
description: Le correctif MDVA-31168 résout le problème en raison duquel le fichier CSV d’exportation de produit n’apparaît pas dans la liste des fichiers CSV exportables. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Correctif MDVA-31168 : le fichier d’exportation de produit ne s’affiche pas dans Admin

Le correctif MDVA-31168 résout le problème en raison duquel le fichier CSV d’exportation de produit n’apparaît pas dans la liste des fichiers CSV exportables. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.10 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce on-premise 2.3.5-p2.

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.1.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Conditions préalables</u>:

Installez Adobe Commerce avec des exemples de données.

<u>Étapes à reproduire :</u>

1. Créez un produit téléchargeable et affectez-le à **Balises** catégorie.
1. Lancez une exportation pour tous les produits.
1. Exécutez la commande suivante à partir de l’interface de ligne de commande :    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>Résultats attendus :</u>

Le fichier CSV d’exportation de produits contenant tous les produits s’affiche dans la liste de fichiers dans Admin, comme prévu.

<u>Résultats réels :</u>

Le fichier CSV d’exportation de produits contenant tous les produits ne s’affiche pas dans la liste dans Admin, bien que le fichier contenant uniquement des en-têtes soit généré dans la variable `/var` sur le serveur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
