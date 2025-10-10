---
title: Comment demander une mise à niveau temporaire d’Adobe Commerce sur une infrastructure cloud
description: Si votre organisation prévoit un événement en ligne générant un trafic élevé, ou si vous constatez soudainement que votre site fait l’objet d’un événement à trafic élevé, vous pouvez déposer un [ticket d’assistance] (/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour demander une capacité cloud supplémentaire temporaire pour votre Adobe Commerce sur la boutique d’infrastructure cloud.
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: e59335b67e1f33e138e34cab93ce593836d14b48
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Comment demander une mise à niveau temporaire d’Adobe Commerce sur une infrastructure cloud

Si votre organisation prévoit un événement en ligne générant un trafic élevé, ou si vous constatez soudainement que votre site fait l’objet d’un événement à trafic élevé, vous pouvez déposer un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) afin de demander une capacité cloud supplémentaire temporaire pour votre boutique Adobe Commerce sur l’infrastructure cloud.

>[!NOTE]
>
>Un préavis de 48 heures ouvrables est requis pour les demandes de mise à niveau non urgentes. Les mises à niveau pour les campagnes promotionnelles ne sont pas considérées comme des urgences à moins que le site ne soit complètement non fonctionnel ou reçoive un trafic beaucoup plus élevé que prévu et que les performances aient été gravement dégradées.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Comment identifier les événements à trafic élevé

Dans les alertes New Relic, vous pouvez utiliser des conditions d’alerte de base pour définir des seuils qui s’adaptent au comportement de vos données.

Les alertes de ligne de base sont utiles pour créer des conditions d’alerte qui :

* Ne vous avertissez que lorsque les données se comportent de manière anormale.
* S’adapter de manière dynamique aux données et aux tendances changeantes, y compris les tendances quotidiennes ou hebdomadaires

En outre, les alertes de base fonctionnent bien avec les nouvelles applications lorsque vous n’avez pas encore de comportements connus.

Suivez ce lien pour en savoir plus sur New Relic [détection des anomalies avec intelligence appliquée](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

Si vous recevez une notification d’alerte suggérant un événement de trafic élevé, vous devrez peut-être envisager de [soumettre un ticket d’assistance](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) pour demander une capacité supplémentaire. Procédez comme suit.

## Comment surveiller les performances de votre site

Adobe fournit un ensemble de politiques d’alerte New Relic pour Adobe Commerce sur les infrastructures cloud, Pro plan architecture et Adobe Commerce sur les infrastructures cloud, Starter plan architecture Environnements de production permettant le suivi des mesures de performances clés suivantes :

* [Score Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* Taux d’erreurs
* Espace disque (disponible sur les environnements de production Pro Architecture uniquement)

Basées sur les bonnes pratiques du secteur, ces politiques définissent des seuils pour les conditions d’avertissement et critiques qui affectent les performances. Lorsque votre site rencontre un problème d’infrastructure ou d’application qui déclenche un seuil d’alerte, New Relic envoie des notifications d’alerte afin que vous puissiez résoudre le problème de manière proactive. Pour utiliser ces politiques, vous devez configurer des canaux de notification pour recevoir les messages d’alerte.

Suivez ce lien pour découvrir comment [configurer des alertes basées sur les performances](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## Étapes de demande de mise à niveau temporaire

Pour demander une capacité cloud supplémentaire temporaire, envoyez un [ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) au Centre d’assistance Adobe Commerce avec les informations suivantes :

>[!NOTE]
>
>Le choix *Holiday Surge Request* n&#39;est possible que pendant les mois d&#39;octobre à décembre.

1. Sélectionnez le produit [!DNL Adobe Commerce] pour lequel vous avez besoin d’une assistance :
   * [!DNL Commerce Cloud]
   * [!DNL Commerce on Managed Service]

1. Renseignez les champs suivants :
   * **[!UICONTROL Case Title]**
   * **[!UICONTROL Case Description]** *(assurez-vous qu’elles décrivent clairement le problème et le contexte.)*

1. Sélectionnez *Demande de modification d’infrastructure* dans le menu déroulant **[!UICONTROL Issue Reason]**.

1. Choisissez le **[!UICONTROL Environment]** dans le menu déroulant.

1. Sélectionnez le **[!UICONTROL Product Version]** approprié dans le menu déroulant.

1. Choisissez *Redimensionnement du projet cloud (vCPU)* dans le menu déroulant **[!UICONTROL Which Infra Change you would like to do today]**.

1. **Sélectionnez le[!UICONTROL Architecture]** :
   * *Architecture par défaut :* sélectionnez *Taille disponible suivante* dans le menu déroulant **Sélectionner la taille**.
   * *Architecture à l’échelle :* lorsque cette option est sélectionnée, l’écran se modifie pour afficher deux champs supplémentaires :
      * *Taille du nœud web*
      * *Taille du nœud de service* *(saisissez les tailles souhaitées pour chaque nœud)*

1. Saisissez le **[!UICONTROL From Date]** au format UTC (date et heure).

1. Saisissez le **[!UICONTROL To Date]** au format UTC (date et heure).

1. Fournissez **[!UICONTROL Project URL]** *(disponible sous https://accounts.magento.cloud/, généralement au format `https://[REGION].magento.cloud/projects/PROJECT_ID`)*

1. Saisissez le **[!UICONTROL Project ID]**.

1. Fournissez **[!UICONTROL Affected URL]** *(doit commencer par `http://` ou `https://`.)*

1. Sélectionnez **[!UICONTROL Priority]**.

1. Sélectionnez **[!UICONTROL Business Impact]**.

1. Confirmez **[!UICONTROL Time Zone]** *(par exemple, `(UTC-5:00) Indiana (East)`)*

1. Saisissez **[!UICONTROL Phone Number]** *(par exemple, `+12015550123`)*

1. Cliquez sur **[!UICONTROL Submit]** pour finaliser votre dossier d’assistance.

>[!NOTE]
>
>Une fois la mise à niveau planifiée, un système automatisé ajuste la taille de votre instance cloud. Vous ne pouvez pas recevoir de notification de ticket une fois la procédure terminée. Vous pouvez utiliser l’outil Observation pour Adobe Commerce pour afficher vos types d’instances AWS ou Azure afin de [vérifier la modification](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## Afficher l&#39;historique de vos uptailles

Vous pouvez afficher l’historique des redimensionnements demandés en demandant les informations à votre **CSM (Customer Success Manager)**.
Les informations suivantes sont disponibles pour chaque demande de redimensionnement :

* **Date de début de la taille** : date de la demande de mise à niveau.
* **Date de fin de la taille** : date à laquelle le cluster a été rétabli à sa taille précédente.
* **taille du processeur virtuel** : taille du cluster après la mise à niveau.
* **Utilisation en jours** : nombre de jours pendant lesquels le cluster a été mis à niveau.
* **Période vCPU** : modification de la taille du vCPU en fonction du nombre de jours d&#39;utilisation. (par exemple, la taille de vCPU 192 par 25 jours est égale à 4 800).


## Lecture connexe

* Pour obtenir des informations, des méthodes et des exemples sur la manière de mesurer et d’améliorer les performances du site, reportez-vous aux articles détaillés suivants de notre base de connaissances d’assistance :
   * [calcul de l’allocation de CPU pour Adobe Commerce sur le cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [Vérifiez si une mise à niveau des instances de l’hôte est nécessaire pour Adobe Commerce sur le cloud](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [Vérifiez la configuration CPU de l’hôte pour Adobe Commerce sur le cloud.](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* Pour plus d’informations sur l’identification des pannes, reportez-vous à la section [Identification et mesure des pannes pour Adobe Commerce sur le cloud](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) dans notre base de connaissances du support.
* Pour plus d’informations sur l’amélioration des performances du site afin d’éviter d’avoir à utiliser une augmentation de la capacité, consultez ces articles dans la documentation destinée aux développeurs :
   * [Dimensionnement de l’image](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [Mise en cache complète de la page](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [Outils CEE](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
