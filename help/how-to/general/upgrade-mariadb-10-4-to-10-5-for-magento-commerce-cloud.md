---
title: Mise à niveau de MariaDB 10.4 vers 10.5 pour Adobe Commerce on cloud
description: La prise en charge de MariaDB 10.4 prendra fin le 18 juin 2024. Cet article explique comment mettre à niveau MariaDB de la version 10.4 vers la version 10.5 pour continuer à utiliser Adobe Commerce sur l’infrastructure cloud.
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 9e218e3fadbf9941c94d309fcfb6f258d2f4faf2
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Mise à niveau de MariaDB 10.4 vers 10.5 pour Adobe Commerce on cloud

MariaDB est une base de données open source d’entreprise utilisée avec Adobe Commerce.

La prise en charge de MariaDB 10.4 arrivera à son terme le [18 juin 2024](https://endoflife.date/mariadb). Vous n’êtes plus compatible PCI lorsque vous utilisez une version de MariaDB non prise en charge. Cet article explique comment effectuer une mise à niveau de MariaDB 10.4 vers la version 10.5 pour continuer à utiliser Adobe Commerce sur l’infrastructure cloud.

>[!NOTE]
>
>MariaDB 10.4 atteignant sa fin de vie, il ne sera plus pris en charge dans les versions actuelles d’Adobe Commerce. Il est recommandé de quitter toute version en fin de vie dans les 30 jours suivant sa fin de vie.

## Produit et versions concernés

* Toutes les infrastructures Adobe Commerce on-premise et on-cloud 2.4.4 et 2.4.5

## Solution

Adoptez les nouveaux correctifs de sécurité uniquement (2.4.4-p9 ou 2.4.5-p8) qui seront publiés le 11 juin 2024 pour garantir la compatibilité avec MariaDB 10.5. Suivez ensuite les étapes ci-dessous pour effectuer la mise à niveau de MariaDB 10.4 vers 10.5.

### Étapes de mise à niveau pour les déploiements cloud

1. Créez une sauvegarde [DB à l&#39;aide des commandes de sauvegarde ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Cette sauvegarde doit être effectuée avant les étapes 2 et 3 au cas où un problème se produirait lors de la mise à jour des tables/lignes.
1. [Vérifiez et convertissez tous les tableaux compacts en tableaux dynamiques](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade). Cette étape est nécessaire pour éviter une perte de données potentielle lors de la mise à niveau de la base de données.
1. Recherchez les tables MYISAM. Vous devez [convertir toutes les tables MyISAM en InnoD](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud).
1. Après avoir préparé les tables et les lignes de la base de données (les deux étapes précédentes), créez une sauvegarde [DB à l&#39;aide des commandes de sauvegarde ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Ouvrez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) pour planifier la mise à niveau de MariaDB 10.4 vers la version 10.5. Dans le ticket, indiquez la date et l’heure auxquelles vous souhaitez que la base de données soit mise à niveau. L’équipe d’assistance doit être avertie 48 heures à l’avance et l’équipe de développement du commerçant doit être disponible. Une fois l’heure et la date convenues pour la mise à niveau, procédez comme suit :
   1. Mettez votre site en mode de maintenance et arrêtez toutes les activités de base de données, par exemple crons.
   1. Créez une sauvegarde [DB à l&#39;aide des commandes de sauvegarde ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Informez l’assistance que vous avez terminé la sauvegarde via votre ticket d’assistance. Pour connaître les étapes d’affichage et de suivi de vos tickets, reportez-vous au [Guide d’utilisation du centre d’aide Adobe Commerce : suivi de vos tickets](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-tickets) dans notre base de connaissances du support.
   1. L’équipe d’assistance d’Adobe Commerce commence ensuite le processus de mise à niveau de MariaDB. Si toutes les étapes ci-dessus ont été effectuées et que la base de données est de taille moyenne, le processus prend environ une heure. Les bases de données plus volumineuses prennent plus de temps. Une fois la mise à niveau terminée, vous en êtes informé via votre ticket.
1. Désactivez le mode de maintenance. Consultez la section [&#x200B; Activer ou désactiver le mode de maintenance &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans la documentation destinée aux développeurs.

>[!NOTE]
>
>Il est recommandé de créer une sauvegarde de la base de données avant et après chaque étape de mise à niveau afin d’éliminer toute possibilité de perte de données. Vous pouvez ainsi revenir à une étape précédente en cas de problème à tout moment pendant la mise à niveau de la version.

## Lectures connexes

* [Guide des bonnes pratiques de mise à niveau de la base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/prerequisites) pour les déploiements sur site.
* [Mettez à niveau MariaDB 10.0 vers 10.2 pour Adobe Commerce sur le cloud](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud) dans notre base de connaissances d’assistance.
* [Politique relative au cycle de vie d’Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) dans notre documentation destinée aux développeurs.
