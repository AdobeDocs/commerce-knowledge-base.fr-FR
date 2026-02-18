---
title: L'erreur 'Version actuelle de SGBDR non prise en charge' sur le déploiement
description: 'Cet article fournit une solution pour le cas où un déploiement échoue et que le journal de déploiement contienne l’erreur suivante : *la version actuelle du SGBDR n’est pas prise en charge*.'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# L&#39;erreur &#39;Version actuelle de SGBDR non prise en charge&#39; sur le déploiement

Cet article fournit une solution pour le cas où un déploiement échoue et que le journal de déploiement contienne l’erreur suivante : *la version actuelle du SGBDR n’est pas prise en charge*.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud, 2.3.0-2.3.7-p1, 2.4.0-2.4.3.

## Problème

Ce message d’erreur signifie que la version actuelle de MariaDB n’est plus prise en charge dans la version d’Adobe Commerce vers laquelle vous tentez d’effectuer la mise à niveau. MariaDB doit donc être mise à niveau vers une version compatible.


<u>Procédure à suivre </u> :

Tentative de déploiement.

<u>Résultat attendu </u> :

Déploiement réussi.

<u>Résultat réel</u> :

Le déploiement échoue avec le message d&#39;erreur suivant : *la version actuelle du SGBDR n&#39;est pas prise en charge*.

## Cause

Votre version de MariaDB n’est pas compatible avec la version d’Adobe Commerce vers laquelle vous essayez d’effectuer la mise à niveau.

## Solution

Vous devez mettre à niveau le service MariaDB vers une version compatible avant de mettre à niveau l’application.


Pour la branche d’intégration sur Adobe Commerce sur l’infrastructure cloud Architecture de plan Pro (et toutes les branches dans l’architecture de démarrage), veuillez suivre [Configurer le service](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/service/services-yaml) dans notre documentation destinée aux développeurs.

Pour l’architecture du plan Pro d’évaluation et de production sur Adobe Commerce sur les infrastructures cloud, [envoyez un ticket d’assistance](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) pour demander que les services soient mis à niveau avant de déployer la mise à niveau de la version d’Adobe Commerce.


## Lecture connexe

* [Bonnes pratiques relatives aux builds et au déploiement](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) dans notre documentation destinée aux développeurs.
* [Mise à niveau d’Adobe Commerce 2.3.5 : des tableaux compacts à dynamiques](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=fr) dans notre base de connaissances d’assistance.
