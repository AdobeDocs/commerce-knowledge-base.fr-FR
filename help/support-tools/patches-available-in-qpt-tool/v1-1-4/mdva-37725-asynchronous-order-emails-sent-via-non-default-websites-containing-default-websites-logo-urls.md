---
title: "MDVA-37725 : les emails envoyés via des sites non par défaut contiennent les URL de logo du site par défaut"
description: Le correctif MDVA-37725 corrige le problème en raison duquel les emails de commande asynchrones sont envoyés via des sites web non par défaut contenant des URL de logo du site web par défaut.
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725 : les emails envoyés via des sites non par défaut contiennent les URL de logo du site par défaut.

>[!WARNING]
>
> Le correctif MDVA-37725 est obsolète.

Le correctif MDVA-37725 corrige le problème en raison duquel les emails de commande asynchrones sont envoyés via des sites web non par défaut contenant des URL de logo du site web par défaut. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4 est installé. L’ID de correctif est MDVA-37725. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les emails de commande asynchrones sont envoyés par le biais de sites web autres que les sites par défaut contenant les URL de logo du site web par défaut.

<u>Conditions préalables</u> :

1. Le deuxième site web/magasin/magasin-view doit avoir été créé.
1. La configuration **Envoi asynchrone** doit être activée à partir de **Magasins** > **Paramètres** > **Configuration** > **Ventes** > **Adresse électronique des ventes** > **Paramètres généraux**.
1. La configuration **Ajouter le code de magasin aux URL** est activée pour faciliter l’accès au site Web secondaire à partir de **Magasins** > **Paramètres** > **Configuration** > **Options d’URL**.

<u>Étapes à reproduire</u> :

1. Passer des commandes dans les premier et deuxième magasins.
1. Exécutez cron pour envoyer les emails de vente.
1. Consultez l’e-mail du deuxième site Web.

<u>Résultats attendus</u> :

L’URL du logo de l’email contient l’URL du deuxième site web.

<u>Résultats réels</u> :

L’URL du logo de l’email contient l’URL du site web par défaut.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
