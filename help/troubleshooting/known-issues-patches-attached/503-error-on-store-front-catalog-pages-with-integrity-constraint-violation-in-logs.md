---
title: Erreur 503 sur les pages du catalogue frontal du magasin avec "violation de contrainte d’intégrité" dans les journaux
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.0 lié à l’inaccessibilité des pages du catalogue frontal du magasin.
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Erreur 503 sur les pages du catalogue frontal du magasin avec &quot;violation de contrainte d’intégrité&quot; dans les journaux

>[!NOTE]
>
>Cet article fournit un correctif comme solution de contournement, mais le problème a été corrigé de manière permanente dans Adobe Commerce sur la version 2.3.3 de l’infrastructure cloud. Il est recommandé d’effectuer la mise à niveau vers la version 2.3.3. Suivez les étapes décrites dans la section [Mise à niveau de la version Adobe Commerce](https://devdocs.magento.com/cloud/project/project-upgrade.html) dans notre documentation destinée aux développeurs.

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.0 lié à l’inaccessibilité des pages du catalogue frontal du magasin, avec un message d’erreur similaire à ce qui suit dans le journal : *Violation de contrainte d’intégrité : 1062 Entrée en double &#39;%entry%&#39; pour la clé &#39;PRINCIPAL&#39;, la requête était : INSERTION DANS \`search\_tmp\_%number%*.

## Problème

Les pages du catalogue frontal de la boutique deviennent inaccessibles de manière inattendue. Le journal des erreurs présente une description d’erreur similaire à celle-ci : *Violation de contrainte d’intégrité : 1062 Entrée en double &#39;%entry%&#39; pour la clé &#39;PRINCIPAL&#39;, la requête était : INSERTION DANS \`search\_tmp\_%number%*.

Le problème est lié à la recherche et à l’existence d’un index obsolète ainsi que du nouvel index après réindexation.

## Solution

Pour résoudre le problème, vous devez supprimer les index obsolètes de l’Elasticsearch et appliquer le correctif pour les empêcher d’apparaître.

Pour répertorier tous les index, utilisez la commande suivante :

<pre>curl -X GET %élasticsearch_domain%:%élasticsearch_port%/_cat/index</pre>

Pour supprimer les index obsolètes, recherchez-les dans la base, puis utilisez la commande suivante :

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

Exemple :

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## Correctif

Les correctifs sont joints à cet article. Pour télécharger un correctif, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom de fichier requis, ou cliquez sur l’un des liens suivants :

[Téléchargez MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch.](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[Téléchargez MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch.](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## Versions Adobe Commerce compatibles

Les correctifs ont été créés pour les éditions et versions suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)
* Adobe Commerce sur l’infrastructure cloud 2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)

La variable `MDVA-9590_EE_2.2.0_COMPOSER_v2` Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.0.X, 2.1.X, 2.2.X et 2.3.0 à 2.3.3
* Adobe Commerce On-Premise 2.0.X, 2.1.X, 2.2.X et 2.3.0 - 2.3.3

La variable `MDVA-13203_EE_2.2.4_V1_COMPOSER` Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.0.X, 2.1.X, 2.2.X et 2.3.0 à 2.3.3
* Adobe Commerce On-Premise 2.0.X, 2.1.X, 2.2.X et 2.3.0 - 2.3.3

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

## Liens utiles

* [Emplacement des fichiers journaux pour Adobe Commerce sur l’architecture du plan de démarrage de l’infrastructure cloud](/help/how-to/general/log-locations-directories-for-starter-plan.md) dans notre base de connaissances de soutien.
* [Emplacement des fichiers journaux pour Adobe Commerce sur l’architecture du plan de l’infrastructure cloud Pro](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md) dans notre base de connaissances de soutien.
* [Emplacement des fichiers journaux pour Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html) dans notre documentation destinée aux développeurs.

## Fichiers attachés
