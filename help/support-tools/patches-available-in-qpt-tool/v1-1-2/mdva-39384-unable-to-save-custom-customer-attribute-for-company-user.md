---
title: 'MDVA-39384 : impossible d’enregistrer l’attribut client personnalisé pour l’utilisateur de la société'
description: Le correctif MDVA-39384 résout le problème en raison duquel l’attribut client personnalisé pour un utilisateur de la société n’est pas enregistré. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-39384. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384 : impossible d’enregistrer l’attribut client personnalisé pour l’utilisateur de la société

Le correctif MDVA-39384 résout le problème en raison duquel l’attribut client personnalisé pour un utilisateur de la société n’est pas enregistré. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-39384. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’attribut client personnalisé pour un utilisateur de la société n’est pas enregistré.

<u>Conditions préalables</u> :

Les modules B2B sont installés.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasins** > Paramètres > **Configuration** > **Fonctionnalités B2B** et définissez l’option **Activer la société** sur Oui.
1. Créez un attribut client personnalisé :
   * Valeurs requises : Oui (facultatif, activez-le afin que l’erreur de validation s’affiche).
   * Afficher sur Storefront : Oui.
   * Forms à utiliser dans : toutes disponibles dans la liste.
1. Créez une société et connectez-vous en tant qu’administrateur de la société.
1. Accédez à Structure d’entreprise dans votre compte.
1. Cliquez sur le lien **Ajouter un utilisateur**.
1. Remplissez le formulaire, y compris l’attribut personnalisé.
1. Cliquez sur **Enregistrer**.

<u>Résultats attendus</u> :

Les valeurs d’attribut personnalisées sont enregistrées avec le nouvel utilisateur de la société.

<u>Résultats réels</u> :

Les valeurs d’attribut personnalisées ne sont PAS enregistrées avec le nouvel utilisateur de la société.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
