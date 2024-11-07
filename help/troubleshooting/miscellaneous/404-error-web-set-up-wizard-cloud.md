---
title: Erreur 404 introuvable lors de l’accès à l’Assistant de configuration web via le panneau d’administration
description: Cet article fournit une solution pour lorsque vous rencontrez une erreur 404 introuvable lors de la tentative d’accès à l’assistant de configuration web via le panneau d’administration.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Erreur 404 introuvable lors de l’accès à l’Assistant de configuration web via le panneau d’administration

Cet article fournit une solution pour lorsque vous rencontrez une erreur 404 introuvable lors de la tentative d’accès à l’assistant de configuration web via le panneau d’administration.

## Produits et versions concernés

* La fonctionnalité Assistant de configuration web a été abandonnée dans Adobe Commerce (toutes les méthodes de déploiement) 2.3.6 et supprimée dans la version 2.4.0.

## Problème

Lors de l’installation d’une extension à l’aide de l’assistant de configuration web, une page 404 s’affiche.

<u>Étapes à reproduire</u> :

Le marchand clique sur l’assistant de configuration web pour installer un nouveau module/nouvelle intégration.

<u>Résultat attendu</u> :

Installations du module/de l’intégration.

<u>Résultat réel</u> :

Une erreur 404 s’affiche.

## Cause

L’assistant de configuration web a été désactivé pour toutes les instances Adobe Commerce sur les instances d’infrastructure cloud ; il n’est pas possible de l’activer. Les extensions doivent être installées via le compositeur.

## Solution

Cette fonctionnalité est désactivée sur Adobe Commerce sur l’infrastructure cloud.

Pour plus d’informations sur l’exécution de mises à jour ou l’installation de modules externes pour Adobe Commerce sur notre infrastructure cloud, voir [Installation, gestion et mise à niveau d’extensions](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions) dans la documentation destinée aux développeurs.
Pour plus d’informations sur l’exécution des mises à jour ou l’installation de modules externes pour Adobe Commerce sur site, voir [Installation rapide](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) dans la documentation destinée aux développeurs.

## Lecture connexe

* Voir [Installer une extension](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension) dans notre documentation destinée aux développeurs.
