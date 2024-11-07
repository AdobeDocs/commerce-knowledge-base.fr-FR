---
title: "ERREUR : échec du réchauffement sur Adobe Commerce sur l’infrastructure cloud"
description: "Cet article fournit une solution lorsque le cache de page se réchauffe et échoue avec une erreur :"
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# ERREUR : Échec du nettoyage sur Adobe Commerce sur l’infrastructure cloud

Cet article fournit une solution lorsque le cache de page se réchauffe et échoue avec une erreur :

*ERROR : Échec du réveil :`<website link>`*

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les [ versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Échec du nettoyage du cache.

<u>Étapes à reproduire</u> :

Démarrez les opérations de nettoyage du cache.

<u>Résultat attendu</u> :

Pages ou chargement de site entier.

<u>Résultat réel</u> :

Le site n’est pas disponible ou le temps de réponse est trop élevé. *ERROR : Échec du réveil :`<website link>`*

## Cause

Le nettoyage du cache ne fonctionne pas avec le contrôle d’accès HTTP activé.

## Solution

Assurez-vous que le contrôle d’accès n’est pas activé : accédez à la branche/l’environnement spécifique et cliquez sur l’icône **Paramètres** , puis vérifiez le paramètre **Contrôle d’accès HTTP** - le nettoyage du cache ne peut pas se produire dans ce scénario, et le contrôle d’accès doit être désactivé.

## Lecture connexe

* [Guide de l’utilisateur d’Adobe Commerce > Cache de page complète](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching) dans notre guide de l’utilisateur.
* [Réchauffement du cache et site indisponible sur Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) dans notre base de connaissances de support.
