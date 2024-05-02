---
title: "ACSD-54983 : UID de l’utilisateur de l’entreprise avec GraphQL non disponible avec l’utilisateur inactif"
description: Appliquez le correctif ACSD-54983 pour résoudre le problème Adobe Commerce en raison duquel il n’est pas possible d’obtenir l’UID de l’utilisateur de l’entreprise avec la requête GraphQL lorsque l’état de l’utilisateur est défini sur inactif.
feature: GraphQL
role: Admin, Developer
exl-id: 57e7b9ca-3421-4b50-86b4-abdf1b3d79d1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-54983 : UID de l’utilisateur de l’entreprise avec GraphQL non disponible avec l’utilisateur inactif

Le correctif ACSD-54983 corrige le problème lorsqu’il n’est pas possible d’obtenir l’UID de l’utilisateur de l’entreprise avec la requête GraphQL lorsque l’état de l’utilisateur est défini sur inactif. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.43 est installée. L’ID de correctif est ACSD-54983. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible d’obtenir l’UID de l’utilisateur de l’entreprise avec la requête GraphQL lorsque l’état de l’utilisateur est défini sur inactif.

<u>Étapes à reproduire</u>:

1. Créez une société avec un utilisateur administrateur. Par exemple, company@test.com.
1. Créez un client.
1. Affectez le nouveau client à une entreprise.
1. Obtenir un **[!UICONTROL company admin token]**.
1. En utilisant la variable **[!UICONTROL company admin token]**, récupérez la structure de l’entreprise. Voir [Renvoi de la structure de l’entreprise](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) dans notre documentation destinée aux développeurs.
1. La réponse contient uniquement *ACTIF* clients avec leurs identifiants.
1. Mettez à jour l’utilisateur de la société vers *INACTIVE*.
1. Récupérez à nouveau la structure de l’entreprise.

<u>Résultats attendus</u>:

Il est possible d’obtenir l’UID de l’utilisateur de la société lorsque l’état est défini sur inactif.

<u>Résultats réels</u>:

Les clients inactifs ne figurent pas dans la liste. Impossible d’obtenir l’UID de l’utilisateur de la société lorsque l’état est défini sur inactif.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
