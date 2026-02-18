---
title: 'Sauvegarde (instantané) sur le cloud : FAQ'
description: Cet article couvre les principes de base de la sauvegarde de vos environnements avec des instantanés sur Adobe Commerce sur les infrastructures cloud.
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 9e218e3fadbf9941c94d309fcfb6f258d2f4faf2
workflow-type: tm+mt
source-wordcount: '709'
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
Vous pouvez [envoyer un ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) pour demander une sauvegarde spéciale ou pour restaurer à partir d’une sauvegarde spécifique en indiquant la date, l’heure et le fuseau horaire dans le ticket. Une fois que l’équipe d’infrastructure a fourni l’instantané, pour déterminer la date et l’heure de la prise initiale, exécutez la commande suivante à partir de l’emplacement où l’instantané a été placé :

  `cat /mnt/recovery/vol-<volume_id>/snap.time`

  Exemple de sortie :

  <strong>2025-01-13 08:42:17.123000+00:00</strong>


* La prise en charge ne génère pas d’instantanés manuels à la demande. Notez également que la prise en charge n’effectue pas la restauration de la base de données à votre place : l’instantané est récupéré, mais vous devez restaurer la base de données vous-même.
* Les instantanés automatiques sont créés **quel que soit l’état d’activation** de votre site (les instantanés sont également créés pour les sites qui n’ont pas encore été lancés). Les sauvegardes automatiques sont stockées dans un système distinct et ne sont pas accessibles au public.
Vous pouvez [envoyer un ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) pour demander une sauvegarde spéciale ou pour restaurer à partir d’une sauvegarde spécifique en indiquant la date, l’heure et le fuseau horaire dans le ticket. La prise en charge ne génère pas d’instantanés manuels à la demande.
Notez également que la prise en charge n’effectue pas la restauration de la base de données à votre place : l’instantané est récupéré, mais vous devez restaurer la base de données vous-même.
* Les sauvegardes sont créées à l’aide des instantanés **encrypted Amazon Web Services Elastic Block Store (AWS EBS)**.
* Les instantanés d’environnement incluent l’ensemble du système (système de fichiers et base de données).
* La durée de conservation des instantanés automatiques **est différente** et suit [le planning](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery).

>[!NOTE]
>
>La console cloud affiche toujours les [!UICONTROL No backup] dans les environnements d’évaluation et de production. Vous pouvez uniquement effectuer des sauvegardes à partir de l’environnement d’intégration. Sélectionnez **[!UICONTROL Backup]** dans le menu déroulant représentant des points de suspension.
>
>![cloud_console_backup.png](assets/cloud_console_backup.png)

### Environnement d’intégration (développement)

* Votre [environnement d’intégration](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242) n’est **sauvegardé automatiquement**, mais vous pouvez créer des instantanés **manuellement**.
* Vous pouvez créer des instantanés manuels pour les environnements d’intégration sur des magasins non actifs.
* Vous disposez peut-être de **instantanés multiples** qui ont été déclenchés manuellement.
* Un instantané déclenché manuellement est stocké pendant **7 jours**.

**Articles connexes dans notre documentation destinée aux développeurs :**

* [Sauvegarde et reprise après sinistre](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#backup-and-disaster-recovery)
* [Créer un instantané](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots)

## Instantané d’environnement, Plan de démarrage

* Tous les types d’environnements (intégration, évaluation, production) **ne sont pas sauvegardés automatiquement** mais vous pouvez créer des instantanés manuellement.
* Vous pouvez créer des instantanés manuels **quel que soit l’état actif** de votre site (des instantanés sont également créés pour les sites qui n’ont pas encore été lancés).
* Un instantané déclenché manuellement est stocké pendant **7 jours**.

## Restaurer un instantané d’environnement

Pour restaurer un snapshot existant (sur l’environnement pris en charge : Intégration, Staging, Production sur le plan de démarrage ou Intégration sur le plan Pro), suivez les étapes décrites dans la section [&#x200B; Gestion des sauvegardes : Restaurer une sauvegarde manuelle &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) dans notre Guide de Commerce sur les infrastructures cloud.

## Sauvegarde de la base de données (BD)

La sauvegarde de la base de données fait partie d’un instantané du cloud :

Un instantané est une sauvegarde complète d’un environnement qui comprend toutes les données persistantes de tous les services en cours d’exécution (par exemple, **votre base de données MySQL**, Redis, etc.) et tous les fichiers stockés sur les volumes montés.

>[!NOTE]
>
>Les volumes montés ne comprennent/ne font référence qu&#39;aux [montages inscriptibles](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/properties#mounts) et n&#39;incluent pas l&#39;ensemble de votre répertoire `/app`. Quant aux autres fichiers, ils sont créés/générés par [le processus de création et de déploiement](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow) et vous devrez également extraire les fichiers restants de votre référentiel Git.

[Snapshots et gestion des sauvegardes](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/snapshots) dans notre documentation destinée aux développeurs.

Envoyez une [demande d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) pour un instantané de base de données à partir de Pro Production and Staging uniquement si vous avez besoin de la base de données à un moment donné. Si vous avez uniquement besoin d’une sauvegarde à jour de votre base de données (sur n’importe quel environnement), consultez l’article de la base de connaissances : [Générer des vidages de base de données sur le cloud](/help/how-to/general/create-database-dump-on-cloud.md).
