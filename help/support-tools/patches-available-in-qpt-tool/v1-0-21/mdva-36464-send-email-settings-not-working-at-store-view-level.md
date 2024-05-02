---
title: "MDVA-36464 : les paramètres d’envoi d’email ne fonctionnent pas au niveau de l’affichage en magasin"
description: Le correctif MDVA-36464 corrige le problème en raison duquel les paramètres d’envoi des emails ne fonctionnent pas au niveau de l’affichage en magasin. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21 est installé. L’ID de correctif est MDVA-36464. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464 : les paramètres d’envoi d’email ne fonctionnent pas au niveau de l’affichage en magasin

Le correctif MDVA-36464 corrige le problème en raison duquel les paramètres d’envoi des emails ne fonctionnent pas au niveau de l’affichage en magasin. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.21 est installée. L’ID de correctif est MDVA-36464. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.0-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Condition préalable requise :</u>

Installez Adobe Commerce propre.

<u>Étapes à reproduire</u>:

1. Créer un site web, un magasin et une vue de magasin supplémentaires (dans cet exemple, le deuxième site web est *site web2*).
1. Désactiver **Notification par email** au niveau mondial dans **Magasin** > **Config** > **Avancé** > **Système** > **Paramètres d’envoi de courrier**.
1. Activer **Notification par email** sur le *site web2* niveau (**Désactiver les communications par courrier électronique** = *Non*).
1. Dans Admin, créez un utilisateur, puis affectez-le à l’ *site web2*.
1. Dans Admin, sur la page de modification du client, cliquez sur **Réinitialiser le mot de passe** pour le client créé ci-dessus à l’étape 4.

<u>Résultats attendus</u>:

Les deux **courrier électronique de bienvenue** et la variable **réinitialisation du mot de passe** sont envoyées, comme prévu, car **Désactiver les communications par courrier électronique** = *Non* pour le deuxième site web (exemple : *site web2*).

<u>Résultats réels</u>:

* La variable **courrier électronique de bienvenue** après la création du nouveau client n’est pas déclenchée.
* La variable **réinitialisation du mot de passe** n’est pas déclenchée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
