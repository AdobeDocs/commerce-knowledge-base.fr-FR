---
title: 'MDVA-37364 : attribut client personnalisé de type date rompt l’interface utilisateur de la grille'
description: Le correctif MDVA-37364 résout le problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille client. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-37364. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.4.
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364 : l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille

Le correctif MDVA-37364 résout le problème en raison duquel l’attribut client personnalisé de type date rompt l’interface utilisateur de la grille client. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-37364. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0-2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut client personnalisé de type date rompt l’interface utilisateur de la grille client.

<u>Étapes à reproduire</u> :

1. Créez un attribut personnalisé de type date :
   * Accédez à **Magasins** > **Attributs** > **Ajouter un attribut**.
   * Définissez le Type d’entrée sur Date.
   * Définissez l’option Ajouter à la colonne sur Oui.
   * Enregistrez l’attribut .
1. Allez à **Admin** > **Clients** > **Tous les Clients**.
   * Ajoutez l’attribut personnalisé nouvellement ajouté à la grille à partir de l’option Colonnes.
1. Créez/Modifiez un client et définissez la valeur du champ d’attribut de date personnalisé créé.
1. Enregistrez, réindexez et effacez le cache.
1. Accédez à **Customers** > **Tous les clients**.
   * Vérifiez la grille client.

<u>Résultats attendus</u> :

La grille d’administration du client affiche toutes les données, y compris la nouvelle date et le nouvel attribut personnalisé, sans interrompre l’interface utilisateur de la grille client.

<u>Résultats réels</u> :

L’interface utilisateur de la grille client d’administration est rompue.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre type de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [Outil de correctifs de qualité publié : un nouvel outil pour appliquer des correctifs de qualité](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) .
