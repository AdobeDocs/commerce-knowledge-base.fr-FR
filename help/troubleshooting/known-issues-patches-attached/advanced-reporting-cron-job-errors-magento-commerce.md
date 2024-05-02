---
title: Erreurs de tâche de création de rapports avancées Adobe Commerce
description: Cet article fournit des correctifs pour les problèmes liés aux tâches de création de rapports avancés dans Adobe Commerce, qui peuvent entraîner une erreur 404 pour les clients qui tentent d’accéder aux rapports avancés.
exl-id: c11a5faf-a243-411a-af0f-585a401e6e39
feature: Cache
role: Developer
source-git-commit: 6287e708c830680e04dd068b64cf63ca13ecdedb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Erreurs de tâche de création de rapports avancées Adobe Commerce

Cet article fournit des correctifs pour les problèmes liés aux tâches de création de rapports avancés dans Adobe Commerce, qui peuvent entraîner une erreur 404 pour les clients qui tentent d’accéder aux rapports avancés.

## Produits et versions concernés

Adobe Commerce (toutes les options de déploiement) 2.3.x

## Problème

Un client obtient une erreur 404 lorsqu’il tente d’accéder aux rapports avancés et qu’il y a des erreurs dans les journaux associés à `analytics_collect_data job` .

## Versions de Magento compatibles :

Les correctifs sont compatibles (mais peuvent ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip): Adobe Commerce (toutes les options de déploiement) 2.3.1-2.3.4-p2
* [MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (toutes les options de déploiement) 2.3.0
* [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip): Adobe Commerce (toutes les options de déploiement) 2.3.0

## **Solution**

Pour résoudre le problème, veuillez appliquer le correctif approprié joint à cet article. Pour le télécharger, cliquez sur les liens suivants :

* Télécharger [MDVA-19391\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip)
* Télécharger [MDVA-15136\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip)
* Télécharger [MDVA-18980\_EE\_2.3.1\_COMPOSER\_v1.patch](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

Pour vérifier quel correctif utiliser :

<ol><li>Consultez les journaux à l’aide de la commande suivante :<code>grep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz</code>
</li><li>Selon l'erreur que vous voyez, sélectionnez un correctif à l'aide des informations du tableau suivant.<table style="width: 826px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center">
<p>Erreur</p>
</td>
<td class="wysiwyg-text-align-center">Correctif</td>
</tr>
<tr>
<td>
<pre>report.CRITICAL : erreur lors de l’exécution d’une tâche cron {"exception":"[objet] (RuntimeException(code: 0): erreur lors de l’exécution d’une tâche cron à l’adresse /srv/public_html/vendor/magento/module-cron/Observer/ProcessCronQueueObserver.php:327, TypeError(code: 0): substr_count() exige que le paramètre 1 soit une chaîne, null étant donné à l’adresse /srv/public_html/vendor/magento/module-page-builder-analytics/Model/ContentTypeUsageReportProvider.php:106)"}"}.</pre>OU<pre>report.ERROR : Cron Job analytics_collect_data a une erreur : substr_count() s’attend à ce que le paramètre 1 soit une chaîne, null étant donné. Statistiques : {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384}
  [] []</pre>
<p> </p>
</td>
<td>Appliquer<a href="assets/MDVA-19391_EE_2.3.1_COMPOSER_v1.patch">MDVA-19391_EE_2.3.1_COMPOSER_v1.patch.zip</a>, effacez le cache et attendez 24 heures pour que la tâche s’exécute à nouveau et réessayez.</td>
</tr>
<tr>
<td>
<p><em>Échec de l'ouverture du fichier /tmp/analytics/tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/../tmp/.../tmp/.../tmp/../tmp/..../tmp/.... /tmp/../tmp/../</em></p>
</td>
<td>Appliquer<a href="assets/MDVA-15136_EE_2.2.6_COMPOSER_v1.patch">MDVA-15136_EE_2.2.6_COMPOSER_v1.patch.zip</a>, effacez le cache et attendez 24 heures pour que la tâche s’exécute à nouveau et réessayez.</td>
</tr>
<tr>
<td><em>Chiffre non valide</em></td>
<td>Appliquer<a href="assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch">MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip</a>, effacez le cache et attendez 24 heures pour que la tâche s’exécute à nouveau et réessayez.</td>
</tr>
</tbody>
</table>
</li></ol>

## Comment appliquer le correctif

Décompressez le fichier et suivez les instructions de la section [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Lecture connexe

[Le fichier ne peut pas être supprimé. Warning!unlink : aucune erreur de fichier ou de répertoire de ce type de la part de l’administrateur](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)
