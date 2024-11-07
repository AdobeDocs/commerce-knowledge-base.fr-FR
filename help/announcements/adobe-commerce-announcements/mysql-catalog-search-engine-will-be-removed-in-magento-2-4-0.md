---
title: Le moteur de recherche de catalogue MySQL sera supprimé dans Adobe Commerce 2.4.0
description: Adobe Commerce sur site, Adobe Commerce sur l’infrastructure cloud et Magento Open Source 2.4.0 seront publiés dans les prochains mois. Pour Adobe Commerce On-Premise et Magento Open Source version 2.4.0 Elasticsearch 6.x ou 7.x, un composant est nécessaire et le moteur de recherche MySQL est supprimé. Dans Adobe Commerce sur l’infrastructure cloud, Elasticsearch est déjà requis.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Le moteur de recherche de catalogue MySQL sera supprimé dans Adobe Commerce 2.4.0

Adobe Commerce sur site, Adobe Commerce sur l’infrastructure cloud et Magento Open Source 2.4.0 seront publiés dans les prochains mois. Pour Adobe Commerce On-Premise et Magento Open Source version 2.4.0 Elasticsearch 6.x ou 7.x, un composant est nécessaire et le moteur de recherche MySQL est supprimé. Dans Adobe Commerce sur l’infrastructure cloud, Elasticsearch est déjà requis.

>[!WARNING]
>
>L’échec de l’installation/de la configuration d’Elasticsearch 6/7 avant la tentative de mise à niveau peut entraîner de sérieux problèmes avec Adobe Commerce. Veuillez noter que les mises à niveau de service sur Adobe Commerce sur l’infrastructure cloud ne peuvent pas être transférées vers l’environnement de production sans préavis de 48 heures ouvrables à notre équipe d’infrastructure. Cela est nécessaire, car nous devons nous assurer qu’un ingénieur du support de l’infrastructure est disponible pour mettre à jour votre configuration dans les délais voulus, avec un temps d’arrêt minimal pour votre environnement de production. Ainsi, 48 heures avant le moment où vos modifications doivent être en production [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle vous souhaitez que le processus de mise à niveau démarre.

La suppression du moteur de recherche MySQL est due au fait qu’Elasticsearch offre des fonctionnalités de recherche supérieures et des optimisations des performances du catalogue.

## Produits et versions concernés :

* Adobe Commerce sur site v2.4.0
* Magento Open Source v2.4.0

## Mise à niveau :

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>Moteur de recherche</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>Action</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">Vous devez installer Elasticsearch. Voir <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search">Installation et configuration de l’Elasticsearch</a> dans notre documentation destinée aux développeurs.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (sans version répertoriée)</td>
<td style="width: 478.2px;">Vous utilisez Elasticsearch 2 et devez effectuer la mise à jour vers Elasticsearch 7 (recommandé) ou 6. Pour plus d’informations, voir <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">Mise à niveau d’Elasticsearch</a> et <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/configure-search-engine">Configuration de Commerce pour utiliser Elasticsearch</a> dans la documentation destinée aux développeurs.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5 a atteint sa <a href="https://www.elastic.co/support/eol">fin de vie</a> et est obsolète dans Adobe Commerce 2.4.0. Mettez à jour vers Elasticsearch 7 (recommandé) ou 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch 6 ou 7</td>
<td style="width: 478.2px;">Vous n’êtes pas tenu d’effectuer d’autres étapes avant la mise à niveau vers Adobe Commerce 2.4.0.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Extension tierce</td>
<td style="width: 478.2px;">Vous n’avez pas besoin d’installer Elasticsearch. Adobe Commerce vous recommande de contacter le fournisseur de votre moteur de recherche pour déterminer si votre extension est entièrement compatible avec Adobe Commerce 2.4.0.</td>
</tr>
</tbody>
</table>

## Installation :

Lorsque Adobe Commerce on-premise et Magento Open Source 2.4.0 est publié, Elasticsearch est un composant obligatoire. Vous devez donc disposer d’un hôte Elasticsearch configuré et configuré avant d’installer la version 2.4.0. Voir [Installation et configuration de l’Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search) dans la documentation du développeur.

Par défaut, la recherche Adobe Commerce utilise Elasticsearch 7 comme moteur de recherche et tente de se connecter à un serveur à l’emplacement localhost:9200. Elasticsearch 6.x est également pris en charge. Si votre configuration ne correspond pas aux valeurs par défaut, vous pouvez configurer ces paramètres à l’aide d’arguments transmis à `setup:install`, de la même manière que la connexion à la base de données est configurée.

Par exemple, `setup:install --elasticsearch-host=es.mystore.com`

Pendant l’installation, la connexion de l’Elasticsearch est vérifiée et l’installation échoue si Adobe Commerce ne parvient pas à se connecter à un hôte Elasticsearch. Si cela se produit, vérifiez que votre Elasticsearch est opérationnel et que vous avez fourni les paramètres de connexion corrects.
