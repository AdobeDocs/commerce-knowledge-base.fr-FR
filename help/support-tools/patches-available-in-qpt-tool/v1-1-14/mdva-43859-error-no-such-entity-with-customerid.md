---
title: '''MDVA-43859 : Erreur "Aucune entité de ce type avec customerId =" enregistrée lors de la connexion du client supprimé"'
description: Le correctif MDVA-43859 corrige le problème en raison duquel l’erreur *Aucune entité avec customerId =* n’est consignée lorsqu’un client supprimé tente de se connecter. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-43859. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 62c4b6ee-88a0-40b8-9eb2-37b6cefa0b83
feature: Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-43859 : Erreur &quot;Aucune entité de ce type avec customerId =&quot; enregistrée lors de la suppression de la connexion du client

Le correctif MDVA-43859 corrige le problème en raison duquel l’erreur *Aucune entité de ce type avec customerId =* est consignée lorsqu’un client supprimé tente de se connecter. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 est installé. L’ID de correctif est MDVA-43859. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 à 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’erreur *Aucune entité de ce type avec customerId =* est consignée lorsqu’un client supprimé tente de se connecter.

<u>Étapes à reproduire</u> :

1. Créez un compte client à partir du front-end.
1. Déconnectez-vous et connectez-vous au compte client créé à l’étape 1.
1. Chargez le serveur principal dans un autre navigateur et accédez à la grille du client.
1. Supprimez le client créé à l’étape 1.
1. Revenez au premier navigateur et essayez de vous déconnecter.

<u>Résultats attendus</u> :

Le client est redirigé vers la page de connexion sans erreur.

<u>Résultats réels</u> :

Le client obtient l’erreur suivante : *Aucune entité de ce type avec customerId =*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
