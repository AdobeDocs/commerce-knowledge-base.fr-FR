---
title: Mise à niveau de MariaDB 10.0 vers 10.2 pour Adobe Commerce sur le cloud
description: MariaDB 10.0 et 10.1 sont en fin de vie (EOL). [Le support a pris fin le 31 mars 2019 et le 17 octobre 2020, respectivement](https://endoflife.date/mariadb). Cet article explique comment mettre à niveau MariaDB de 10.0 vers 10.2 ou 10.2 vers 10.3 ou vers 10.4, afin d’utiliser Adobe Commerce sur l’infrastructure cloud.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Mise à niveau de MariaDB 10.0 vers 10.2 pour Adobe Commerce sur le cloud

MariaDB 10.0 et 10.1 sont en fin de vie (EOL). [La prise en charge s’est terminée le 31 mars 2019 et le 17 octobre 2020, respectivement](https://endoflife.date/mariadb). Cet article explique comment mettre à niveau MariaDB de 10.0 vers 10.2 ou 10.2 vers 10.3 ou vers 10.4, afin d’utiliser Adobe Commerce sur l’infrastructure cloud.

>[!NOTE]
>
>MariaDB 10.0 est en fin de vie et n’est pas prise en charge dans les versions actuelles d’Adobe Commerce. Il est recommandé de quitter n’importe quelle version de fin de vie dans les 30 jours suivant sa fin de vie.

## Produit et versions concernés

* MariaDB 10.2 est recommandée pour Adobe Commerce sur l’infrastructure cloud 2.3.x.
* MariaDB 10.4 est recommandée pour la version 2.4.x. MariaDB 10.3 est également compatible avec Adobe Commerce sur l’infrastructure cloud 2.4.x.

## Etapes de mise à niveau

Pour effectuer la mise à niveau de MariaDB 10.0 vers 10.2 ou 10.2 vers 10.3 ou vers 10.4, procédez comme suit :

1. Créez une [sauvegarde de base de données à l’aide des commandes de sauvegarde de base de données CEE-Outils](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Cela doit être effectué avant les étapes 2 et 3, au cas où un problème se produirait lors de la mise à jour des tableaux/lignes.
1. [Cochez et convertissez toutes les tables compactes en tables dynamiques](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=fr). Cela est nécessaire pour éviter toute perte potentielle de données lors de la mise à niveau de la base de données.
1. Recherchez les tables MYISAM. Vous devez [convertir toutes les tables MyISAM en InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=fr).
1. Après avoir préparé les tables et les lignes de la base de données (les deux étapes précédentes), créez une [sauvegarde de base de données à l’aide des commandes de sauvegarde de base de données CEE-Outils](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Ouvrez un ticket de support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour planifier la mise à niveau de MariaDB 10.0 vers 10.2 ou 10.2 vers 10.3 ou 10.4. Dans le détail du ticket, indiquez la date et l’heure de la mise à niveau de la base de données. L’équipe d’assistance doit recevoir un avis de 48 heures et l’équipe de développement des commerçants doit être disponible. Une fois l&#39;heure et la date convenues pour la mise à niveau, procédez comme suit :
   1. Placez votre site en mode de maintenance, puis arrêtez toute activité DB, par exemple crons.
   1. Créez une [sauvegarde de base de données à l’aide des commandes de sauvegarde de base de données CEE-Outils](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Dites à l’assistance que vous avez terminé la sauvegarde. Effectuez cette opération via votre ticket d’assistance. Pour obtenir des instructions sur l’affichage et le suivi de vos tickets, consultez le [Guide de l’utilisateur du centre d’aide Adobe Commerce : Tracker vos tickets](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets) dans notre base de connaissances d’assistance.
   1. L’équipe d’assistance d’Adobe Commerce lancera le processus de mise à niveau de MariaDB. Si toutes les étapes ci-dessus ont été effectuées et que la base de données est de taille moyenne, cela peut être fait en une heure environ. Les grandes bases de données prendront plus de temps. Vous en serez informé via votre ticket une fois l&#39;upgrade terminé.
1. Désactivez le mode de maintenance. Reportez-vous à la section [Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur les exigences d’Adobe Commerce 2.4.x, reportez-vous à la section [Configuration requise d’Adobe Commerce 2.4 > Base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/system-requirements#database) dans notre documentation destinée aux développeurs.
