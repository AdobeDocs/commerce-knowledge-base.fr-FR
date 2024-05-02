---
title: Comment demander une mise à niveau temporaire d’Adobe Commerce sur l’infrastructure cloud
description: Si votre entreprise prévoit un événement en ligne où vous prévoyez un trafic élevé ou si vous constatez soudainement que votre site connaît un trafic élevé, vous pouvez envoyer un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) afin de demander une capacité cloud supplémentaire temporaire pour votre Adobe Commerce sur la boutique d’infrastructures cloud.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: a445bae7f013b29cb83fc96eb26dcbfd186a4de7
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# Comment demander une mise à niveau temporaire d’Adobe Commerce sur l’infrastructure cloud

Si votre entreprise prévoit un événement en ligne où le trafic est élevé ou si vous constatez soudainement que votre site subit un événement de trafic important, vous pouvez enregistrer un événement [Ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour demander une capacité cloud supplémentaire temporaire pour votre Adobe Commerce sur la boutique d’infrastructures cloud.

>[!NOTE]
>
>Un avis de 48 heures ouvrées est requis pour les demandes de mise à niveau non urgentes. Les mises à niveau pour les campagnes promotionnelles ne sont pas considérées comme des urgences, sauf si le site est complètement infonctionnel ou reçoit un trafic beaucoup plus élevé que prévu et que les performances ont été fortement dégradées.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, tous [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Comment identifier les événements à trafic élevé

Dans les alertes New Relic, vous pouvez utiliser des conditions d’alerte de base pour définir des seuils qui s’ajustent au comportement de vos données.

Les alertes de base sont utiles pour créer des conditions d’alerte qui :

* Vous avertit uniquement lorsque les données se comportent de manière anormale.
* S’adapter de manière dynamique aux tendances et données changeantes, y compris aux tendances quotidiennes ou hebdomadaires.

En outre, les alertes de base fonctionnent bien avec les nouvelles applications lorsque vous n’avez pas encore de comportements connus.

Suivez ce lien pour en savoir plus sur New Relic [Détection des anomalies avec intelligence appliquée](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Si vous recevez une notification d’alerte qui suggère un événement de trafic élevé, vous devrez peut-être envisager [envoi d’un ticket d’assistance](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) demande d’une capacité supplémentaire. Suivez les étapes ci-dessous.

## Comment surveiller les performances de votre site

Adobe fournit un ensemble de stratégies d’alerte New Relic pour l’architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro et Adobe Commerce sur l’infrastructure cloud Architecture de plan de démarrage Environnements de production pour effectuer le suivi des mesures de performances clés suivantes :

* [Score d’application](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Taux d’erreur
* Espace disque (disponible sur les environnements de production d’architecture Pro uniquement)

Basées sur les bonnes pratiques du secteur, ces politiques définissent des seuils d’avertissement et de conditions critiques qui affectent les performances. Lorsque votre site rencontre un problème d’infrastructure ou d’application qui déclenche un seuil d’alerte, New Relic envoie des notifications d’alerte afin que vous puissiez résoudre le problème de manière proactive. Pour utiliser ces stratégies, vous devez configurer les canaux de notification afin de recevoir les messages d’alerte.

Suivez ce lien pour savoir comment [configuration des alertes basées sur les performances](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Étapes pour demander une mise à niveau temporaire

Suivez les étapes ci-dessous pour envoyer une [Ticket d’assistance](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) pour demander une capacité cloud supplémentaire temporaire :

Envoyer un [Ticket d’assistance au Centre d’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), après avoir saisi les informations suivantes :

>[!NOTE]
>
>La variable *Demande d’augmentation des vacances* Le choix n’est possible qu’entre octobre et décembre.

1. Sélectionnez le produit Adobe Commerce pour lequel vous recherchez de l’aide.
1. Renseignez les quatre premiers champs (Produit, Organisation, Type d’implémentation, Objet).
1. Sélectionner *Infrastructure cloud Adobe Commerce* dans le **Motif de contact** menu déroulant.
1. Sélectionner *Demande de capacité de survol des vacances* dans le **Raison de contact pour l’infrastructure Adobe Commerce** options de liste déroulante. Cliquez sur **OK** dans le message contextuel demandant un avis de 48 heures ouvrées pour les demandes de capacité cloud supplémentaire temporaires.
1. Sélection des dates des champs obligatoires **Redimensionner la date de début** et **Redimensionner la date de fin**. La valeur préférée **Redimensionner l’heure de début** est également un champ obligatoire.
1. Renseignez les quatre champs suivants.
1. Dans le **Description** , si vous disposez d’informations supplémentaires sur la taille, indiquez-le ici. Si aucune taille spécifique plus grande n’est requise, nous vous redimensionnerons jusqu’à la prochaine capacité d’environnement plus grande. Par défaut, la taille de la taille actuelle des requêtes volumineuses sera la plus grande suivante. Si vous avez besoin de capacité supplémentaire, veuillez l’indiquer dans la variable **Description** champ . L’augmentation de la capacité sera déduite des jours de surge ou des jours vCPU prévus. La fenêtre d’augmentation de capacité est généralement de cinq jours, mais si vous avez besoin de plus ou moins de jours, veuillez l’indiquer dans votre [Ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>Une fois la mise à niveau planifiée, un système automatisé ajuste la taille de votre instance cloud. Vous ne pouvez recevoir aucune notification de ticket une fois la procédure terminée. Vous pouvez utiliser l’outil Observation pour Adobe Commerce pour afficher vos types d’instances AWS ou Azure sur [vérifier la modification](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Afficher l’historique de vos upgrades

Vous pouvez afficher l’historique des redimensionnements demandés dans votre [Portail de projet (interface utilisateur d’intégration)](/docs/commerce-cloud-service/start/onboarding.html#cloud-project-portal-(onboarding-ui)), sous **Projet** > **Services** > **Suivi de l’utilisation du processeur**.
Les informations suivantes sont disponibles pour chaque requête de redimensionnement :

* **Date de début de la taille**: date de la requête de mise à niveau.
* **Date de fin de la taille**: date à laquelle la grappe a été renvoyée à la taille précédente.
* **vCPU Size**: taille de la grappe après la mise à niveau.
* **Jours d’utilisation**: pendant le nombre de jours pendant lesquels la grappe a été mise à niveau.
* **Période vCPU**: modification de la taille du processeur virtuel en fonction du nombre de jours pendant lesquels il a été utilisé. (par exemple, la taille du processeur virtuel de 192 sur 25 jours est égale à 4 800).


## Lecture connexe

* Pour obtenir des informations, des méthodes et des exemples sur la manière de mesurer et d’améliorer les performances du site, reportez-vous aux articles détaillés suivants de notre base de connaissances d’assistance :
   * [Calcul de l’allocation du processeur pour Adobe Commerce sur le cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Vérifiez si la mise à niveau des instances de l’hôte est nécessaire pour Adobe Commerce sur le cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Vérification de la configuration du processeur de l’hôte pour Adobe Commerce sur le cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Pour plus d&#39;informations sur l&#39;identification des pannes, reportez-vous à la section [Identifier et mesurer les pannes d’Adobe Commerce sur le cloud](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) dans notre base de connaissances de soutien.
* Pour plus d’informations sur l’amélioration des performances du site afin d’éviter d’utiliser une capacité accrue, reportez-vous à ces articles dans notre documentation destinée aux développeurs :
   * [Dimensionnement des images](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Mise en cache complète des pages](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [CEE-Outils](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
