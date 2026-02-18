---
title: Le moteur de recherche catalogue MySQL sera supprimé dans Adobe Commerce 2.4.0
description: Adobe Commerce on-premise, Adobe Commerce on cloud infrastructure et Magento Open Source 2.4.0 seront publiés dans les prochains mois. Pour Adobe Commerce On-premise et Magento Open Source version 2.4.0, Elasticsearch 6.x ou 7.x sera un composant obligatoire et le moteur de recherche MySQL sera supprimé. Dans Adobe Commerce sur les infrastructures cloud, Elasticsearch est déjà requis.
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Le moteur de recherche catalogue MySQL sera supprimé dans Adobe Commerce 2.4.0

Adobe Commerce on-premise, Adobe Commerce on cloud infrastructure et Magento Open Source 2.4.0 seront publiés dans les prochains mois. Pour Adobe Commerce On-premise et Magento Open Source version 2.4.0, Elasticsearch 6.x ou 7.x sera un composant obligatoire et le moteur de recherche MySQL sera supprimé. Dans Adobe Commerce sur les infrastructures cloud, Elasticsearch est déjà requis.

>[!WARNING]
>
>Si vous n’installez pas/configurez Elasticsearch 6/7 avant d’essayer d’effectuer la mise à niveau, vous risquez de rencontrer de graves problèmes avec Adobe Commerce. Notez que les mises à niveau de service sur Adobe Commerce sur les infrastructures cloud ne peuvent pas être envoyées à l’environnement de production sans préavis de 48 heures ouvrables à notre équipe en charge de l’infrastructure. Cela est nécessaire car nous devons nous assurer qu’un ingénieur du support à l’infrastructure est disponible pour mettre à jour votre configuration dans le délai souhaité avec un temps d’arrêt minimal pour votre environnement de production. Ainsi, 48 heures avant le moment où vos modifications doivent être mises en production [soumettez un ticket d’assistance](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) détaillant la mise à niveau de service requise et indiquant l’heure à laquelle vous souhaitez que le processus de mise à niveau démarre.

La raison de la suppression du moteur de recherche MySQL est qu’Elasticsearch fournit des fonctionnalités de recherche supérieures ainsi que des optimisations des performances de catalogue.

## Produits et versions concernés :

* Adobe Commerce on-premise v2.4.0
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
<td style="width: 478.2px;">Vous devez installer Elasticsearch. Voir <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/search/overview-search">Installation et configuration d’Elasticsearch</a> dans notre documentation destinée aux développeurs.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch (sans version répertoriée)</td>
<td style="width: 478.2px;">Vous utilisez Elasticsearch 2 et devez effectuer la mise à jour vers Elasticsearch 7 (recommandé) ou 6. Voir <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">Mise à niveau d’Elasticsearch</a> et <a href="https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/search/configure-search-engine">Configuration de Commerce pour utiliser Elasticsearch</a> dans notre documentation destinée aux développeurs pour plus de détails.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH 5</td>
<td style="width: 478.2px;">Elasticsearch 5 a atteint sa <a href="https://www.elastic.co/support/eol">fin de vie</a> et a été abandonné dans Adobe Commerce 2.4.0. Mettez à jour vers Elasticsearch 7 (recommandé) ou 6.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch 6 ou 7</td>
<td style="width: 478.2px;">Il n’est pas nécessaire d’effectuer d’autres étapes avant la mise à niveau vers Adobe Commerce 2.4.0.</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Extension tierce</td>
<td style="width: 478.2px;">Il n’est pas nécessaire d’installer Elasticsearch. Adobe Commerce vous recommande de contacter le fournisseur de votre moteur de recherche pour déterminer si votre extension est entièrement compatible avec Adobe Commerce 2.4.0.</td>
</tr>
</tbody>
</table>

## Installation :

Lors de la publication d’Adobe Commerce On-premise et de Magento Open Source 2.4.0, Elasticsearch sera un composant obligatoire. Vous devez donc disposer d’une configuration d’hôte Elasticsearch et d’un paramétrage de celle-ci avant d’installer la version 2.4.0. Consultez [Installation et configuration d’Elasticsearch](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/search/overview-search) dans notre documentation destinée aux développeurs.

Par défaut, la recherche Adobe Commerce utilise Elasticsearch 7 comme moteur de recherche et tente de se connecter à un serveur sur localhost:9200. Elasticsearch 6.x est également pris en charge. Si votre configuration ne correspond pas aux valeurs par défaut, vous pouvez configurer ces paramètres à l’aide des arguments transmis à `setup:install`, de la même manière que la connexion à la base de données est configurée.

Par exemple, `setup:install --elasticsearch-host=es.mystore.com`

Lors de l’installation, la connexion à Elasticsearch est vérifiée et l’installation échoue si Adobe Commerce ne parvient pas à se connecter à un hôte Elasticsearch. Si cela se produit, vérifiez que votre Elasticsearch est en cours d’exécution et que vous avez fourni les paramètres de connexion appropriés.
