---
title: Transformation en OpenSearch pour Adobe Commerce sur Cloud 2.4.4
promoted: true
description: Adobe Commerce sur l’infrastructure cloud 2.4.4 ne prendra pas en charge les versions d’Elasticsearch après la version 7.10. **Vous devez d’abord effectuer la mise à niveau vers Adobe Commerce 2.4.4, puis passer immédiatement de Elasticsearch à l’Adobe OpenSearch 1.2.x.** afin de fournir des instructions détaillées plus proches de la version GA d’Adobe Commerce 2.4.4.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Transformation en OpenSearch pour Adobe Commerce sur Cloud 2.4.4

Adobe Commerce sur l’infrastructure cloud 2.4.4 ne prendra pas en charge les versions d’Elasticsearch après la version 7.10. **Vous devez d’abord effectuer la mise à niveau vers Adobe Commerce 2.4.4, puis passer immédiatement de l’Elasticsearch à l’Adobe OpenSearch 1.2.x.** afin de fournir des instructions détaillées plus près de la version GA d’Adobe Commerce 2.4.4.

>[!NOTE]
>
>Le commutateur doit être effectué quel que soit le fournisseur de cloud.

Adobe Commerce sur site ajoute la prise en charge d’Elasticsearch 7.16 et d’OpenSearch 1.2 dans toutes les versions de correctifs de mars 2022 (2.4.4, 2.4.3-p2 et 2.3.7-p3). Dans la version 2.4.4, Adobe Commerce sur l’infrastructure cloud passera à OpenSearch en tant que moteur de recherche par défaut. Par conséquent, les marchands doivent utiliser OpenSearch à la place d’Elasticsearch avant la mise à niveau vers Adobe Commerce 2.4.4 ou version ultérieure. Les commerçants avec des déploiements sur site Adobe Commerce peuvent utiliser Elasticsearch ou OpenSearch, car Adobe Commerce continuera à prendre en charge les deux.


## Qu’est-ce qu’OpenSearch ?

OpenSearch est une fourchette d&#39;Elasticsearch et de Kibana. Elle est gérée par AWS au lieu d’Elastic.co. Pour en savoir plus, consultez GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch).

**Compatibilité entre les versions :**

**Adobe Commerce sur l’infrastructure cloud prend-il en charge Elasticsearch 7.10 ?**

**Oui** - à compter de la mi-janvier 2022, Adobe Commerce sur les versions d’infrastructure cloud 2.4.3-p1, 2.4.3-p2 et 2.3.7-p3 prennent en charge Elasticsearch 7.10.

Pour Adobe Commerce On-Premise, la dernière version de 7.16.x est recommandée pour atténuer Log4j.

## Migration :

## Quand les marchands peuvent-ils migrer vers OpenSearch ?

Après Adobe Commerce 2.4.4.

Toutefois, avant de commencer la mise à niveau vers Adobe Commerce 2.4.4, les commerçants doivent se trouver sur une version actuelle d’Adobe Commerce qui prend en charge Elasticsearch 7.10 et être au moins Elasticsearch avant de commencer la mise à niveau vers Adobe Commerce 2.4.4 ou OpenSearch.

## Que peuvent faire les commerçants (Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site) qui ne sont pas sur 2.4.4 ? Peuvent-ils effectuer une mise à niveau vers une version d’Elasticsearch prise en charge (7.10, 7.16.1) ou vers OpenSearch ? Doivent-ils se trouver sur la dernière version prise en charge pour ce faire (comme 2.4.3-p1, 2.3.7-p2, 2.4.3-p1) ?

Si la version de base d’Adobe Commerce sur laquelle ils se trouvent prend en charge Elasticsearch 7.10, ils peuvent l’utiliser.

Pour plus d’informations sur la compatibilité des versions, voir [Configuration requise](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) dans la documentation destinée aux développeurs.

>[!NOTE]
>
>Il est recommandé de planifier la mise à niveau vers Adobe Commerce 2.4.4 dès que possible, car Elasticsearch 7.10 sera en fin de vie en mai 2022.

Les partenaires d’Adobe peuvent s’inscrire à notre programme bêta [ici](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html) pour accéder à notre code bêta4 le plus récent qui a été testé par rapport à Elasticsearch 7.16.1 et OpenSearch 1.1.
