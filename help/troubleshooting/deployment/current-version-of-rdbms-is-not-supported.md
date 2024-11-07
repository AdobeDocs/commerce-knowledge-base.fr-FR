---
title: Erreur "Version actuelle du SGBDR non prise en charge" lors du déploiement
description: "Cet article fournit une solution pour lorsqu’un déploiement échoue et que l’erreur suivante s’affiche dans le journal de déploiement : *la version actuelle du SGBDR n’est pas prise en charge*."
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Erreur &quot;Version actuelle du SGBDR non prise en charge&quot; lors du déploiement

Cet article fournit une solution pour lorsqu’un déploiement échoue et que vous obtenez l’erreur suivante dans le journal de déploiement : *la version actuelle du SGBDR n’est pas prise en charge*.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problème

Ce message d’erreur signifie que la version actuelle de MariaDB n’est plus prise en charge dans la version d’Adobe Commerce vers laquelle vous essayez de mettre à niveau et que MariaDB doit être mise à niveau vers une version compatible.


<u>Étapes à reproduire</u> :

Tentative de déploiement.

<u>Résultat attendu</u> :

Déploiement réussi.

<u>Résultat réel</u> :

Échec du déploiement avec le message d’erreur : *la version actuelle de SGBDR n’est pas prise en charge*.

## Cause

Votre version de MariaDB n’est pas compatible avec la version d’Adobe Commerce vers laquelle vous essayez de mettre à niveau.

## Solution

Vous devez mettre à niveau le service MariaDB vers une version compatible avant de mettre à niveau l’application.


Pour la branche d’intégration sur l’architecture de plan Adobe Commerce on Cloud Infrastructure Pro (et toutes les branches dans l’architecture Starter), suivez [Configurer le service](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml) dans notre documentation destinée aux développeurs.

Pour l’architecture du plan d’évaluation et de production sur Adobe Commerce sur l’infrastructure cloud Pro, [ envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour demander que les services soient mis à niveau avant de déployer la mise à niveau de la version d’Adobe Commerce.


## Lecture connexe

* [Bonnes pratiques pour les versions et le déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) dans notre documentation destinée aux développeurs.
* [Mise à niveau d’Adobe Commerce 2.3.5 : compacte dans les tables dynamiques](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) dans notre base de connaissances de prise en charge.
