---
title: "Échec du déploiement : aucune commande n’est définie dans l’erreur d’espace de noms 'cache'"
description: Cet article fournit une solution au problème lorsque le déploiement échoue avec l’erreur suivante **Aucune commande n’est définie dans l’espace de noms du cache**.
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1a8a4e1eada859a6712a43536d7bad26d1ce1244
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Échec du déploiement : aucune commande n’est définie dans l’erreur d’espace de noms &quot;cache&quot;

>[!WARNING]
>
>Sauvegardez d’abord la base de données, si vous effectuez cette opération dans un site de production actif, avant d’effectuer ces étapes.

Cet article fournit une solution au problème lorsque votre déploiement échoue et que l’une des erreurs dans le journal ressemble à ceci :

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.4.x

## Problème  

<u>Étapes à reproduire</u> :

Tentative de déploiement. 

<u>Résultats attendus</u> :

Déploiement réussi.

<u>Résultats réels</u> :

Vous ne déployez pas correctement. Dans les journaux, une erreur de déploiement s’affiche avec un message similaire au *suivant. Il n’y a aucune commande dans l’espace de noms du cache*.

### Cause

La table **core_config_data** contient des configurations pour un ID de magasin ou un ID de site web qui n’existe plus dans la base de données. Cela se produit lorsque vous avez importé une sauvegarde de base de données à partir d’une autre instance/un autre environnement et que les configurations de ces portées restent dans la base de données bien que le ou les magasins/sites web associés aient été supprimés.

### Solution

Si vous n’avez qu’un seul site web, le deuxième test pour les sites web ne s’applique pas, et il vous suffit de le tester pour les magasins.

Pour résoudre ce problème, identifiez les lignes non valides restantes de ces configurations.

1. SSH sur le serveur et exécutez la commande suivante :

   `bin/magento`

1. Le message d’erreur peut indiquer les lignes et les tableaux qui restent dans la base de données des sites supprimés. Par exemple, l’erreur suivante indique que le magasin demandé est introuvable :

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. Exécutez cette requête MySql pour vérifier que le magasin est introuvable, ce qui est indiqué par le message d’erreur à l’étape 2. 

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Exécutez l’instruction MySql suivante pour supprimer les lignes non valides : 

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store); 
   ```

1. Exécutez à nouveau cette commande :

   `bin/magento`

   Si vous obtenez une erreur comme celle ci-dessous qui indique que le site web avec l’ID X demandé est introuvable, il reste des configurations.        dans la base de données du ou des sites web, ainsi que des magasins qui ont été supprimés.

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   Exécutez cette requête MySql et vérifiez que le site web est introuvable :

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. Exécutez cette instruction MySql pour supprimer les lignes non valides de la configuration du site web :

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

Pour confirmer que la solution a fonctionné, réexécutez la commande `bin/magento`. Les erreurs ne doivent plus s’afficher et le déploiement peut réussir.

## Lecture connexe

* [Dépannage du déploiement d’Adobe Commerce](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html)
* [Vérification du journal de déploiement si l’interface utilisateur de Cloud a &quot;extrait de journal&quot;](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
