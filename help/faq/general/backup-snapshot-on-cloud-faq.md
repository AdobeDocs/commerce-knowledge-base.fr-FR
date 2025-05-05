---
title: 'Sauvegarde (instantané) sur le cloud : FAQ'
description: Cet article couvre les principes de base de la sauvegarde de vos environnements avec des instantanés sur Adobe Commerce sur les infrastructures cloud.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: cfaa7043eed9cc5369f5317b10609d97a91d5861
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# Sauvegarde (instantané) sur le cloud : FAQ

Cet article traite de la sauvegarde de vos environnements avec des instantanés sur Adobe Commerce sur les infrastructures cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.x
* Plans d&#39;architecture : Starter, Pro Legacy, Pro

## Instantané de l&#39;environnement, Pro plan

### Environnements d’évaluation et de production

* Les instantanés manuels ne sont pas disponibles pour les environnements d&#39;évaluation et de production sur Pro Plan.
* Les instantanés automatiques sont créés **quel que soit l’état d’activation** de votre site (les instantanés sont également créés pour les sites qui n’ont pas encore été lancés). Les sauvegardes automatiques ne sont pas accessibles au public, car elles sont stockées dans un système distinct.
Vous pouvez [envoyer un ticket d’assistance Adobe Commerce](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) pour demander une sauvegarde spéciale ou pour restaurer à partir d’une sauvegarde spécifique en indiquant la date, l’heure et le fuseau horaire dans le ticket. La prise en charge ne génère pas d’instantanés manuels à la demande.
Notez également que la prise en charge n’effectue pas la restauration de la base de données à votre place : l’instantané est récupéré, mais vous devez restaurer la base de données vous-même.
* Les sauvegardes sont créées à l’aide des instantanés **encrypted Amazon Web Services Elastic Block Store (AWS EBS)**.
* Les instantanés d’environnement incluent l’ensemble du système (système de fichiers et base de données).
* La durée de conservation des instantanés automatiques **est différente** et suit [le planning](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=en#backup-and-disaster-recovery).

>[!NOTE]
>La console cloud affiche toujours les [!UICONTROL No backup] dans les environnements d’évaluation et de production. Vous pouvez uniquement effectuer des sauvegardes à partir de l’environnement d’intégration. Sélectionnez **[!UICONTROL Backup]** dans le menu déroulant représentant des points de suspension.
>![cloud_console_backup.png](assets/cloud_console_backup.png)





### Environnement d’intégration (développement)

* Votre [environnement d’intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) n’est **sauvegardé automatiquement**, mais vous pouvez créer des instantanés **manuellement**.
* Vous pouvez créer des instantanés manuels pour les environnements d’intégration sur des magasins non actifs.
* Vous disposez peut-être de **instantanés multiples** qui ont été déclenchés manuellement.
* Un instantané déclenché manuellement est stocké pendant **7 jours**.

**Articles connexes dans notre documentation destinée aux développeurs :**

* [Sauvegarde et reprise après sinistre](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Création d’un instantané](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html)

## Instantané d’environnement, Plan de démarrage

* Tous les types d’environnements (intégration, évaluation, production) **ne sont pas sauvegardés automatiquement** mais vous pouvez créer des instantanés manuellement.
* Vous pouvez créer des instantanés manuels **quel que soit l’état actif** de votre site (des instantanés sont également créés pour les sites qui n’ont pas encore été lancés).
* Un instantané déclenché manuellement est stocké pendant **7 jours**.

## Restaurer un instantané d’environnement

Pour restaurer un snapshot existant (sur l’environnement pris en charge : Intégration, Staging, Production sur le plan de démarrage ou Intégration sur le plan Pro), suivez les étapes décrites dans la section [ Gestion des sauvegardes : Restaurer une sauvegarde manuelle ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) dans notre Guide de Commerce sur les infrastructures cloud.

## Sauvegarde de la base de données (BD)

La sauvegarde de la base de données fait partie d’un instantané du cloud :

&#x200B;>>
Un instantané est une sauvegarde complète d’un environnement qui comprend toutes les données persistantes de tous les services en cours d’exécution (par exemple, **votre base de données MySQL**, Redis, etc.) et tous les fichiers stockés sur les volumes montés.

>[!NOTE]
>
>Les volumes montés incluent uniquement/font référence aux [montages inscriptibles](/docs/commerce-cloud-service/user-guide/configure/app/properties/properties.html?lang=en#mounts) et n’incluent pas la totalité de votre répertoire /app. Quant aux autres fichiers, ils sont créés/générés par [le processus de création et de déploiement](/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=en#deployment-workflow) et vous devrez également extraire les fichiers restants de votre référentiel Git.

[Snapshots et gestion des sauvegardes](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) dans notre documentation destinée aux développeurs.

Envoyez une [demande d’assistance](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) pour un instantané de base de données à partir de Pro Production and Staging uniquement si vous avez besoin de la base de données à un moment donné. Si vous avez uniquement besoin d’une sauvegarde à jour de votre base de données (sur n’importe quel environnement), consultez l’article de la base de connaissances : [Générer des vidages de base de données sur le cloud](/help/how-to/general/create-database-dump-on-cloud.md).
