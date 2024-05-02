---
title: "Alertes gérées sur Adobe Commerce : alertes MariaDB"
description: '"Cet article décrit les étapes de dépannage lorsque vous recevez des alertes MariaDB pour Adobe Commerce dans New Relic. Les alertes MariaDB surveillent la charge de requête élevée ainsi que les requêtes DML excessives. Les deux peuvent entraîner une dégradation de l’expérience utilisateur, voire des temps d’arrêt. Vous pouvez recevoir quatre types d''alertes :'''
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Alertes gérées sur Adobe Commerce : alertes MariaDB

Cet article décrit les étapes de dépannage lorsque vous recevez des alertes MariaDB pour Adobe Commerce dans New Relic. Les alertes MariaDB surveillent la charge de requête élevée ainsi que les requêtes DML excessives. Les deux peuvent entraîner une dégradation de l’expérience utilisateur, voire des temps d’arrêt. Vous pouvez recevoir quatre types d’alertes :

* Avertissement des requêtes DML
* Requêtes DML critiques

## **Produits et versions concernés**

Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro

## Problème

Vous recevrez une alerte gérée dans New Relic si vous vous êtes inscrit à [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) et un ou plusieurs seuils d’alerte ont été dépassés. Ces alertes ont été développées par Adobe pour fournir aux clients un ensemble standard utilisant les informations du service d’assistance et d’ingénierie.

**Faites-le !**

* Abandonnez tout déploiement planifié jusqu’à ce que cette alerte soit effacée.
* Mettez votre site en mode de maintenance immédiatement si votre site est ou ne répond plus complètement. Pour les étapes, voir [Guide d’installation > Activer ou désactiver le mode de maintenance](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) dans notre documentation destinée aux développeurs. Veillez à ajouter votre adresse IP à la liste des adresses IP exemptées afin de vous assurer que vous pouvez toujours accéder à votre site pour la résolution des problèmes. Pour connaître les étapes, voir [Maintenir la liste des adresses IP exemptées](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt).
* Terminez tous les scripts, tels que les imports, qui peuvent être la cause de l’alerte si les performances du site sont affectées.

**Ne le faites pas !**

* Exécutez des indexeurs ou des crons supplémentaires qui peuvent entraîner une contrainte supplémentaire sur MariaDB.
* Effectuez les tâches administratives principales (c’est-à-dire l’administration de Commerce, l’importation/exportation de données).
* Effacez le cache.

## Solution

**Requêtes DML (requêtes qui modifient la base de données à l’aide de UPDATE, INSERT et DELETE)**

Si vous recevez une alerte critique de requêtes DML à l’étape 1. Si vous recevez une alerte d’avertissement de requêtes HTML à l’étape 2.

1. Vérifiez si un ticket d’assistance Adobe Commerce existe. Pour connaître les étapes, consultez notre base de connaissances [Suivi des tickets d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets). L’assistance a peut-être reçu une alerte de seuil New Relic, créé un ticket et commencé à travailler sur le problème. S’il n’existe aucun ticket, créez-en un. Le ticket doit comporter les informations suivantes :
1. Raison de contact : sélectionnez &quot;Alerte New Relic MariaDB reçue&quot;.
1. Description de l’alerte.
1. [Lien d’incident New Relic](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Elle est incluse dans votre [Alertes gérées pour Adobe Commerce](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md).
1. Pour identifier la source du problème, essayez d’identifier les requêtes DML :
1. Vérifier les opérations de votre base de données à l’aide des étapes de New Relic [Pages d’IU APM > Surveillance > Page Bases de données](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) .
1. Trier par NOMBRE D’APPELS, puis OPÉRATION. Examinez les opérations INSERT, DELETE et UPDATE.
1. Recherchez un AVG élevé.
1. Cliquez pour rechercher les appels d’opération de base de données. Cela permet d’identifier les transactions qui utilisent cette requête par temps.
1. Recherchez des optimisations de code ou des optimisations opérationnelles :
1. Optimisations du code : optimisez les requêtes avec des insertions/mises à jour en masse, minimisez l’utilisation des index ou le ralentissement du code.
1. Optimisations opérationnelles : déchargez les modifications de données gourmandes en ressources vers des temps de trafic plus courts.
1. Optimisations supplémentaires : vérifiez que vous utilisez la dernière version de CEE-Outils. Pour connaître les étapes, voir [Cloud pour Adobe Commerce > Mise à jour de la version des outils de mise à jour](https://devdocs.magento.com/cloud/project/ece-tools-update.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

* Pour rechercher d’autres problèmes courants de MariaDB, reportez-vous à la section [Problèmes de base de données les plus courants pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html).
* Pour consulter les bonnes pratiques relatives aux bases de données, voir [Bonnes pratiques relatives aux bases de données pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html).
