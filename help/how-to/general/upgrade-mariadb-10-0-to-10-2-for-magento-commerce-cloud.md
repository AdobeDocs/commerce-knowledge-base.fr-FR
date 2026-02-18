---
title: Mise à niveau de MariaDB 10.0 vers 10.2 pour Adobe Commerce on cloud
description: Les versions 10.0 et 10.1 de MariaDB sont en fin de vie. [La prise en charge a pris fin le 31 mars 2019 et le 17 octobre 2020, respectivement](https://endoflife.date/mariadb). Cet article explique comment mettre à niveau MariaDB de 10.0 vers 10.2 ou 10.2 vers 10.3 ou vers 10.4, afin d’utiliser Adobe Commerce sur une infrastructure cloud.
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Mise à niveau de MariaDB 10.0 vers 10.2 pour Adobe Commerce on cloud

Les versions 10.0 et 10.1 de MariaDB sont en fin de vie. [L’assistance a pris fin le 31 mars 2019 et le 17 octobre 2020, respectivement](https://endoflife.date/mariadb). Cet article explique comment mettre à niveau MariaDB de 10.0 vers 10.2 ou 10.2 vers 10.3 ou vers 10.4, afin d’utiliser Adobe Commerce sur une infrastructure cloud.

>[!NOTE]
>
>MariaDB 10.0 est en fin de vie et n’est pas pris en charge dans les versions actuelles d’Adobe Commerce. Il est recommandé de quitter toute version en fin de vie dans les 30 jours suivant sa fin de vie.

## Produit et versions concernés

* MariaDB 10.2 est recommandé pour Adobe Commerce sur l’infrastructure cloud 2.3.x.
* MariaDB 10.4 est recommandé pour 2.4.x. MariaDB 10.3 est également compatible avec Adobe Commerce sur l’infrastructure cloud 2.4.x.

## Étapes de mise à niveau

Pour effectuer la mise à niveau de MariaDB 10.0 vers 10.2, 10.2 vers 10.3 ou vers 10.4, procédez comme suit :

1. Créez une sauvegarde [DB à l&#39;aide des commandes de sauvegarde ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots). Cette opération doit être effectuée avant les étapes 2 et 3 au cas où un problème se produirait lors de la mise à jour des tables/lignes.
1. [Vérifiez et convertissez tous les tableaux compacts en tableaux dynamiques](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html). Cela est nécessaire pour éviter toute perte de données potentielle lors de la mise à niveau de la base de données.
1. Recherchez les tables MYISAM. Vous devez [convertir toutes les tables MyISAM en InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
1. Après avoir préparé les tables et les lignes de la base de données (les deux étapes précédentes), créez une sauvegarde [DB à l&#39;aide des commandes de sauvegarde ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
1. [Ouvrez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) pour planifier la mise à niveau de MariaDB 10.0 vers 10.2 ou 10.2 vers 10.3 ou 10.4. Dans les détails du ticket, date et heure auxquelles vous souhaitez que la base de données soit mise à niveau. L’équipe d’assistance doit être avertie 48 heures à l’avance et l’équipe de développement des commerçants doit être disponible. Une fois l’heure et la date convenues pour la mise à niveau, procédez comme suit :
   1. Mettez votre site en mode de maintenance et arrêtez toutes les activités de base de données, par exemple crons.
   1. Créez une sauvegarde [DB à l&#39;aide des commandes de sauvegarde ECE-Tools DB](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots).
   1. Informez l’assistance que vous avez terminé la sauvegarde. Faites-le via votre ticket d’assistance. Pour connaître les étapes d’affichage et de suivi de vos tickets, reportez-vous au [Guide d’utilisation du centre d’aide Adobe Commerce : suivi de vos tickets](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-tickets) dans notre base de connaissances du support.
   1. L’équipe d’assistance Adobe Commerce lancera le processus de mise à niveau de MariaDB. Si toutes les étapes ci-dessus ont été effectuées et que la base de données est de taille moyenne, cela peut être fait en une heure environ. Les bases de données plus volumineuses prendront plus de temps. Vous serez informé via votre ticket une fois la mise à niveau terminée.
1. Désactivez le mode de maintenance. Consultez la section [&#x200B; Activer ou désactiver le mode de maintenance &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) dans la documentation destinée aux développeurs.

## Lectures connexes

Pour en savoir plus sur la configuration requise pour Adobe Commerce 2.4.x, consultez [Configuration requise pour Adobe Commerce 2.4 > Base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#database) dans la documentation destinée aux développeurs.
