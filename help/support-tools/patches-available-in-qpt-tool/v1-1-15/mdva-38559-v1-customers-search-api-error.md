---
title: 'MDVA-38559: /V1/customers/search API renvoie une erreur'
description: Le correctif MDVA-38559 corrige le problème en raison duquel l’API `/V1/customers/search` renvoie une erreur pour les clients qui ont plusieurs abonnements. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15 est installé. L’ID de correctif est MDVA-38559. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.
exl-id: 434fe78c-c384-4fa8-b26a-cb00007e490e
feature: REST, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38559 : /V1/customers/search API renvoie une erreur

Le correctif MDVA-38559 corrige le problème en raison duquel la variable `/V1/customers/search` L’API renvoie une erreur pour les clients qui ont plusieurs abonnements. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.15 est installée. L’ID de correctif est MDVA-38559. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

`/V1/customers/search` L’API renvoie une erreur pour les clients qui ont plusieurs abonnements.

<u>Conditions préalables</u>:

La boutique Adobe Commerce utilise plusieurs sites web.

<u>Étapes à reproduire</u>:

1. Accédez à **Magasin** > **Configuration** > **Client** > **Configuration client** > **Options de partage de compte** et sélectionnez **Global**.
1. Accédez à **Clients** > **Tous les clients**, sélectionnez **Modifier** sur n’importe quel client, puis sélectionnez **Newsletter**.
1. Abonnez-vous à une newsletter pour plusieurs sites web et enregistrez le client.
1. Envoyez la requête suivante :

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>Résultats attendus</u>:

Les résultats de recherche du client s’affichent.

<u>Résultats réels</u>:

L’erreur suivante est consignée dans exception.log : *L’élément (Magento\Customer\Model\Customer\Interceptor) avec le même ID &quot;1&quot; existe déjà.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
