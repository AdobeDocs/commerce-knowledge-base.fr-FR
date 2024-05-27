---
title: Mise à niveau de MariaDB 10.4 vers 10.5 pour Adobe Commerce sur le cloud
description: MariaDB 10.4 a atteint la fin de la prise en charge le 18 juin 2024. Cet article explique comment mettre à niveau MariaDB de 10.4 vers 10.5 pour continuer à utiliser Adobe Commerce sur l’infrastructure cloud.
feature: Best Practices, Cloud
source-git-commit: 401a36722b3336b47dd76bb12ace34f0bf55b8e6
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# Mise à niveau de MariaDB 10.4 vers 10.5 pour Adobe Commerce sur le cloud

MariaDB est une base de données Open Source d’entreprise utilisée avec Adobe Commerce.

MariaDB 10.4 atteint la fin de la prise en charge sur [18 juin 2024](https://endoflife.date/mariadb). Vous n’êtes plus compatible PCI lorsque vous utilisez une version non prise en charge de MariaDB. Cet article explique comment effectuer la mise à niveau de MariaDB 10.4 vers 10.5 pour continuer à utiliser Adobe Commerce sur l’infrastructure cloud.

>[!NOTE]
>
>MariaDB 10.4 arrivant en fin de vie (EOL), elle ne sera plus prise en charge dans les versions actuelles d’Adobe Commerce. Il est recommandé de quitter n’importe quelle version de fin de vie dans les 30 jours suivant sa fin de vie.

## Produit et versions concernés

* Toutes les Adobe Commerce sur site et sur l’infrastructure cloud 2.4.4 et 2.4.5

## Solution

Adoptez les nouveaux correctifs uniquement de sécurité (2.4.4-p9 ou 2.4.5-p8) qui sortent le 11 juin 2024, afin de garantir la compatibilité avec MariaDB 10.5. Suivez ensuite les étapes ci-dessous pour mettre à niveau MariaDB 10.4 vers 10.5.

### Étapes de mise à niveau pour les déploiements cloud

1. Créez un [Sauvegarde de base de données à l’aide des commandes de sauvegarde de base de données de CEE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Cette sauvegarde doit être effectuée avant les étapes 2 et 3, au cas où un problème se produirait lors de la mise à jour des tableaux/lignes.
1. [Vérifier et convertir tous les tableaux compacts en tableaux dynamiques](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Cette étape est nécessaire pour éviter toute perte potentielle de données lors de la mise à niveau de la base de données.
1. Recherchez les tables MYISAM. Vous devez [Convertir tous les tableaux MyISAM en InnoD](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. Après avoir préparé les tableaux et les lignes de la base de données (les deux étapes précédentes), créez un [Sauvegarde de base de données à l’aide des commandes de sauvegarde de base de données de CEE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Ouverture d’un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour planifier la mise à niveau de MariaDB 10.4 vers 10.5. Dans le ticket, indiquez la date et l’heure de mise à niveau de la base de données. L’équipe d’assistance doit être avisée pendant 48 heures et l’équipe de développement du commerçant doit être disponible. Une fois l&#39;heure et la date convenues pour la mise à niveau, procédez comme suit :
   1. Placez votre site en mode de maintenance, puis arrêtez toute activité DB, par exemple, crons.
   1. Créez un [Sauvegarde de base de données à l’aide des commandes de sauvegarde de base de données de CEE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Dites à l’assistance que vous avez terminé la sauvegarde via votre ticket d’assistance. Pour obtenir les étapes de visualisation et de tracking des tickets, reportez-vous à la section [Guide de l’utilisateur du centre d’aide Adobe Commerce : suivi des tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) dans notre base de connaissances de soutien.
   1. L’équipe d’assistance Adobe Commerce commence ensuite le processus de mise à niveau de MariaDB. Si toutes les étapes ci-dessus ont été effectuées et que la taille de la base de données est moyenne, le processus dure environ une heure. Les grandes bases de données prennent plus de temps. Une fois l&#39;upgrade effectué, vous en êtes informé via votre ticket.
1. Désactivez le mode de maintenance. Voir [Activer ou désactiver le mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs.

## Lecture connexe

* [Guide des bonnes pratiques de mise à niveau de DB](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) pour les déploiements sur site.
* [Mise à niveau de MariaDB 10.0 vers 10.2 pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) dans notre base de connaissances de soutien.
* [Stratégie de cycle de vie Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) dans notre documentation destinée aux développeurs.
