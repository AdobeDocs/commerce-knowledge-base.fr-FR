---
title: 'MDVA-42046 : valeur incorrecte attribuée pour l’attribut de produit'
description: Le correctif MDVA-42046 corrige le problème en raison duquel une valeur incorrecte est affectée à l’attribut de produit lors de la mise à jour d’un produit avec un champ de saisie de date. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 est installé. L’ID de correctif est MDVA-42046. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046 : valeur incorrecte attribuée à l’attribut de produit

Le correctif MDVA-42046 corrige le problème en raison duquel une valeur incorrecte est affectée à l’attribut de produit lors de la mise à jour d’un produit avec un champ de saisie de date. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 est installé. L’ID de correctif est MDVA-42046. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.3.5-p2 et 2.4.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après avoir enregistré un produit avec les champs `news_from_date` et/ou `news_to_date`, les valeurs de ces champs sont réinitialisées par défaut.

<u>Étapes à reproduire</u> :

1. Créez un produit simple.
1. Exportez le produit créé à l’étape 1.
1. Dans le fichier CSV exporté, placez certaines valeurs dans les champs `news_from_date` et `news_to_date` . Par exemple, 2021-05-15 et 2021-06-18.
1. Importez le produit à l’aide du fichier CSV modifié.
1. Ajoutez des colonnes supplémentaires &quot;Définir le produit comme nouveau à partir de la date&quot; et &quot;Définir le produit comme nouveau à la date&quot; à la grille de produit.
1. Ouvrez la page de modification du produit et, sans modification, cliquez sur **Enregistrer**.
1. Revenez à la grille de produit et vérifiez les données du produit.

<u>Résultats attendus</u> :

&quot;Définir le produit comme nouveau à partir de la date&quot; et &quot;Définir le produit comme nouveau à la date&quot; sont les mêmes que avant l’enregistrement.

<u>Résultats réels</u> :

* Les valeurs des colonnes &quot;Définir le produit comme nouveau à partir de la date&quot; et &quot;Définir le produit comme nouveau à la date&quot; sont modifiées.

* La colonne &quot;Définir le produit comme nouveau à partir de la date&quot; indique la date actuelle et la colonne &quot;Définir le produit comme nouveau à la date&quot; est vide.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
