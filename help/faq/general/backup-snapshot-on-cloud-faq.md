---
title: "Sauvegarde (instantané) sur le cloud : FAQ"
description: Cet article décrit les principes de base de la sauvegarde de vos environnements avec des instantanés sur Adobe Commerce sur l’infrastructure cloud.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 0958a8923e27c1341f4b536812b26205685b2b81
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Sauvegarde (instantané) sur Cloud : FAQ

Cet article décrit la sauvegarde de vos environnements avec des instantanés sur Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.x
* Plans d’architecture : Starter, Pro Legacy, Pro

## Instantané d’environnement, formule Pro

### Environnements intermédiaires et de production

* Les instantanés manuels ne sont pas disponibles pour les environnements d’évaluation et de production sur le plan Pro.
* Création automatique d’instantanés **quel que soit l’état d’activation** de votre site (instantanés également créés pour les sites qui n’ont pas encore été lancés). Les sauvegardes automatiques ne sont pas publiques car elles sont stockées dans un système distinct. Vous pouvez [envoyer un ticket d’assistance Adobe Commerce ;](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) pour demander une sauvegarde spéciale ou pour restaurer à partir d’une sauvegarde spécifique en indiquant la date, l’heure et le fuseau horaire dans le ticket. Notez également que la prise en charge n’effectue pas la restauration ou la restauration de la base de données ; ils récupèrent l’instantané, mais vous devez restaurer la base de données vous-même.
* Les sauvegardes sont créées à l’aide de la variable **instantanés Amazon Web Services Elastic Block Store (AWS EBS) chiffrés**.
* Les instantanés d’environnement incluent votre système complet (système de fichiers et base de données).
* Temps de rétention pour les instantanés automatiques **est différent** et suit [le planning](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=en#backup-and-disaster-recovery).

>[!NOTE]
>La console Cloud affiche toujours [!UICONTROL No backup] dans les environnements d’évaluation et de production. Vous pouvez uniquement effectuer des sauvegardes à partir de l’environnement d’intégration. Sélectionner **[!UICONTROL Backup]** dans le menu déroulant représentant des points de suspension.
>![cloud_console_backup.png](assets/cloud_console_backup.png)





### Environnement d’intégration (développement)

* Votre [Environnement d’intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) is **ne pas être sauvegardé automatiquement**, mais vous pouvez créer des instantanés **manuellement**.
* Vous pouvez créer des instantanés manuels pour les environnements d’intégration sur les magasins non actifs.
* Vous pouvez avoir **plusieurs instantanés** qui ont été déclenchés manuellement.
* Un instantané déclenché manuellement est stocké pour **7 jours**.

**Articles connexes dans notre documentation destinée aux développeurs :**

* [Sauvegarde et reprise après sinistre](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Création d’un instantané](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html)

## Instantané de l’environnement, plan de démarrage

* Tous les types d’environnements (intégration, évaluation, production) **ne sont pas sauvegardées automatiquement ;**, mais vous pouvez créer des instantanés manuellement.
* Vous pouvez créer des instantanés manuels. **quel que soit l’état d’activation** de votre site (instantanés également créés pour les sites qui n’ont pas encore été lancés).
* Un instantané déclenché manuellement est stocké pour **7 jours**.

## Restauration d’un instantané d’environnement

Pour restaurer un instantané existant (sur l’environnement pris en charge : Intégration, Évaluation, Production sur le plan de démarrage ou Intégration sur le plan Pro), suivez les étapes de la section [Gestion des sauvegardes : restauration d’une sauvegarde manuelle](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) dans notre guide Commerce on Cloud Infrastructure.

## Sauvegarde de la base de données (DB)

La sauvegarde DB fait partie d’un instantané Cloud :

>>
Un instantané est une sauvegarde complète d’un environnement qui inclut toutes les données persistantes de tous les services en cours d’exécution (par exemple, **votre base de données MySQL ;**, Redis, etc.) et tous les fichiers stockés sur les volumes montés.

>[!NOTE]
>
>Les volumes montés incluent uniquement/se réfèrent aux [Monts modifiables](/docs/commerce-cloud-service/user-guide/configure/app/properties/properties.html?lang=en#mounts) et n’inclura pas l’ensemble de votre répertoire /app. Comme pour les autres fichiers, ils sont créés/générés par [processus de création et de déploiement](/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=en#deployment-workflow), et vous devrez également extraire les fichiers restants de votre référentiel Git.

[Instantanés et gestion des sauvegardes](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) dans notre documentation destinée aux développeurs.

Soumettre uniquement une [demande d’assistance](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) pour un instantané de la base de données de Pro Production et de l’évaluation si vous avez besoin de la base de données à un moment donné. Si vous avez besoin d’une sauvegarde actuelle de votre base de données uniquement (dans n’importe quel environnement), consultez l’article de la base de connaissances : [Générer des vidages de base de données sur Cloud](/help/how-to/general/create-database-dump-on-cloud.md).
