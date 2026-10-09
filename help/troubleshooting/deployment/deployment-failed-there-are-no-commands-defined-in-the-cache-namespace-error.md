---
title: 'Échec du déploiement lors du vidage du cache : ''Aucune commande n''est définie dans l''erreur ''espace de noms du cache'''
description: Cet article fournit une solution au problème d’échec du déploiement avec l’erreur suivante **Aucune commande n’est définie dans l’espace de noms du cache**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%
---

# Échec du déploiement lors du vidage du cache : erreur « Aucune commande n’est définie dans l’espace de noms du cache »

>[!WARNING]
>
>Sauvegardez d’abord la base de données, si vous le faites dans un site de production actif, avant d’effectuer ces étapes.

Cet article fournit une solution au problème d’échec de déploiement d’et d’apparition de l’une des erreurs du journal, comme suit :

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.4.x

## Problème

<u>Procédure à suivre </u> :

Tentative de déploiement.

<u>Résultats attendus</u> :

Le déploiement a réussi.

<u>Résultats réels</u> :

Le déploiement échoue. Dans les journaux, une erreur de déploiement s’affiche avec un message similaire au suivant *Il n’existe aucune commande dans l’espace de noms du cache*.

### Cause

La table **`core_config_data`** contient des configurations pour un ID de magasin ou un ID de site web qui n’existe plus dans la base de données. Cela se produit lorsque vous avez importé une sauvegarde de base de données à partir d’une autre instance ou d’un autre environnement et que les configurations de ces étendues restent dans la base de données bien que le ou les magasins/sites web associés aient été supprimés.

### Solution

Si vous n’avez eu qu’un seul site web, le deuxième test pour les sites web ne s’applique pas et vous n’avez qu’à tester les magasins.

Pour résoudre ce problème, identifiez les lignes non valides restantes de ces configurations.

1. Envoyez le SSH au serveur et exécutez la commande suivante :

   `bin/magento`

1. Le message d’erreur peut indiquer quelles lignes et tables restent dans la base de données à partir des sites supprimés. Par exemple, voici une erreur indiquant que le magasin demandé est introuvable :

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. Exécutez cette requête [!DNL MySQL] pour vérifier que le magasin est introuvable, ce qui est indiqué par le message d’erreur à l’étape 2.

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Exécutez l’instruction [!DNL MySQL] suivante pour supprimer les lignes non valides :

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Exécutez à nouveau cette commande :

   `bin/magento`

   Si vous obtenez une erreur telle que celle ci-dessous, qui indique que le site web portant l’ID X demandé est introuvable, vous disposez des configurations restantes dans la base de données du ou des sites web, ainsi que des magasins qui ont été supprimés.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Exécutez cette requête [!DNL MySQL] et vérifiez que le site web est introuvable :

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Exécutez cette instruction [!DNL MySQL] pour supprimer les lignes non valides de la configuration du site web :

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Pour confirmer que la solution a fonctionné, exécutez à nouveau la commande `bin/magento`. Vous ne devriez plus voir les erreurs et pouvez procéder au déploiement avec succès.

## Lecture connexe

* [Résolution des problèmes de déploiement d’Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter)
* [Vérification du journal de déploiement si l’interface utilisateur de Cloud comporte une erreur « journal arrêté »](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
