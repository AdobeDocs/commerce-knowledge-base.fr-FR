---
title: Alertes gérées pour Adobe Commerce
description: Si vous êtes un client d’architecture de plan Adobe Commerce on Cloud Infrastructure Pro, vous pouvez utiliser des alertes gérées pour comprendre l’intégrité de votre site. Si vous êtes un client de l’architecture de plan de démarrage de l’infrastructure cloud d’Adobe Commerce, vous ne recevrez que des alertes pour les conditions Apdex et de taux d’erreur.
exl-id: 4d08eaad-a3ce-4f6c-9c32-58e44e1d6534
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Alertes gérées pour Adobe Commerce


Nous avons configuré des tableaux de bord et des alertes clés pour vous aider à comprendre quand votre site atteint des niveaux de stockage critique et d’Apdex (satisfaction des utilisateurs concernant les applications et le temps de réponse des services). Cela peut vous aider à agir avant de remarquer des temps de réponse lents ou une panne. Vous pourrez résoudre les problèmes liés aux alertes à l’aide des articles répertoriés ci-dessous. Avant de pouvoir utiliser les alertes, vous devez d&#39;abord configurer les canaux de notification. Reportez-vous à [Configuration des canaux de notification New Relic](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels) dans notre documentation destinée aux développeurs.

>[!NOTE]
>
>Si les alertes gérées pour la stratégie d’alerte Adobe Commerce ne sont pas disponibles, cela peut être dû au fait que ce compte a été créé ou que New Relic a été récemment configuré. Un processus est exécuté tous les mardis pour ajouter la stratégie d’alerte à ces comptes. La stratégie d’alerte doit vous être accessible le lendemain de l’exécution du processus suivant. Si la stratégie est toujours manquante, [envoyer une demande d’assistance Adobe Commerce ;](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) et incluez votre ID de projet.

Reportez-vous au tableau ci-dessous pour obtenir des liens vers les articles de la base de connaissances décrivant les étapes de dépannage pour ces alertes :

* Alertes gérées pour Adobe Commerce : alerte d’avertissement du processeur
* Alertes gérées pour Adobe Commerce : alerte critique du processeur
* Alertes gérées pour Adobe Commerce : alerte d’avertissement de mémoire
* Alertes gérées pour Adobe Commerce : alerte critique en mémoire
* Alertes gérées pour Adobe Commerce : alerte d’avertissement Apdex
* Alertes gérées pour Adobe Commerce : alerte critique Apdex
* Alertes gérées pour Adobe Commerce : alerte d’avertissement sur le disque
* Alertes gérées pour Adobe Commerce : alerte critique sur le disque
* Alertes gérées sur Adobe Commerce : alertes MariaDB
* Alertes gérées sur Adobe Commerce : alerte d’avertissement de mémoire réduite
* Alertes gérées sur Adobe Commerce : permet de réduire l’alerte critique de mémoire

>[!NOTE]
>
>Les seuils définis pour les alertes d’avertissement et les alertes critiques reposent sur des recherches que nous effectuons à l’aide de données de performances historiques sur notre base de clients. Ils représentent les dernières informations provenant des équipes d’assistance et d’ingénierie d’Adobe Commerce. Veuillez noter que ces seuils peuvent être modifiés en fonction des dernières analyses en cours. Le flux d’alerte type consiste à recevoir des alertes inférieures à supérieures en termes de gravité. Par conséquent, vous recevrez probablement une alerte d’avertissement avant de recevoir une alerte critique. Reportez-vous aux liens vers les articles pour connaître les étapes de dépannage.

<table style="width: 128.434%; height: 660px;" width="100%">
<tbody>
<tr style="height: 44px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 44px;">
<p><strong>Gravité</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 44px;">
<p><strong>CPU</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 44px;">
<p><strong>Mémoire</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 44px;">
<p><strong>Disque</strong></p>
</td>
<td class='"wysiwyg-text-align-center wysiwyg-text-align-center' style="width: 9%; height: 44px;">
<p><strong>Apdex</strong></p>
</td>
<td style="width: 7.058036%; height: 44px;">
<p><strong>MariaDB</strong></p>
</td>
<td class="wysiwyg-text-align-center med-col">
<p><strong>Redis Memory</strong></p>
</td>
<td class="wysiwyg-text-align-center large-col" style="width: 24.5638%; height: 44px;">
<p><strong>Article de dépannage</strong></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Avertissement</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md">Alertes gérées pour Adobe Commerce : alerte d’avertissement du processeur</a><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md"></a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Critique</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-cpu-critical-alert.md">Alertes gérées pour Adobe Commerce : alerte critique du processeur</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Avertissement</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-memory-warning-alert.md">Alertes gérées pour Adobe Commerce : alerte d’avertissement de mémoire</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Critique</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">
<p> </p>
<p>✅</p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-memory-critical-alert.md#_critical_memory">Alertes gérées pour Adobe Commerce : alerte critique en mémoire</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Avertissement</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Alertes gérées pour Adobe Commerce : alerte d’avertissement Apdex</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Critique</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-critical-alert.md">Alertes gérées pour Adobe Commerce : alerte critique Apdex</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Avertissement</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md">Alertes gérées pour Adobe Commerce : alerte d’avertissement sur le disque</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">Critique</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md">Alertes gérées pour Adobe Commerce : alerte critique sur le disque</a></p>
</td>
</tr>
<tr style="height: 44px;">
<td style="width: 17.8571%; height: 44px;">Avertissement et critique</td>
<td style="width: 6.14286%; height: 44px;"> </td>
<td style="width: 10.5714%; height: 44px;"> </td>
<td style="width: 7.14286%; height: 44px;"> </td>
<td style="width: 9%; height: 44px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 44px;">✅</td>
<td style="width: 24.5638%; height: 44px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 44px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-mariadb-alerts.md">Alertes gérées sur Adobe Commerce : alertes MariaDB</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">Avertissement</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-warning-alert.md">Alertes gérées sur Adobe Commerce : alerte d’avertissement de mémoire réduite</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">Critique</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-critical-alert.md">Alertes gérées sur Adobe Commerce : permet de réduire l’alerte critique de mémoire</a></p>
</td>
</tr>
</tbody>
</table>
