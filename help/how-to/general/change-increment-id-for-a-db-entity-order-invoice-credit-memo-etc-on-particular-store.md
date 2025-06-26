---
title: Modifier l'ID incrément d'une entité de base de données (commande, facture, avoir, etc.) dans un magasin particulier
description: Cet article explique comment modifier l’ID d’incrément d’une entité de base de données (DB) Adobe Commerce (commande, facture, avoir, etc.) sur une boutique Adobe Commerce spécifique à l’aide de l’instruction SQL « ALTER TABLE ».
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: e33d0bf6c857d0d54ec1373db79910d78296b054
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Modifier l&#39;ID incrément d&#39;une entité de base de données (commande, facture, avoir, etc.) dans un magasin particulier

Cet article explique comment modifier l’ID d’incrément d’une entité de base de données (DB) Adobe Commerce (commande, facture, avoir, etc.) sur une boutique Adobe Commerce spécifique à l’aide de l’instruction SQL `ALTER TABLE`.

>[!NOTE]
>
>Cet article décrit uniquement comment modifier la valeur numérique de départ de l&#39;ID incrément pour les commandes, les factures, les avoirs, etc.
>
>Elle ne couvre pas la modification du format d’ID d’incrément ou l’ajout de préfixes/suffixes personnalisés (par exemple, modifier le 10000001 en ORDER-10000001, MYSTORE-10000001, 2A10000001, etc.)
>
>Pour personnaliser le format, vous aurez besoin d’une extension personnalisée ou d’un travail de développement.

## Versions affectées

* Adobe Commerce on-premise : 2.x.x
* Adobe Commerce sur l’infrastructure cloud : 2.x.x
* MySQL : toute [version prise en charge](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/system-requirements)

## Quand devez-vous modifier l’ID d’incrément (cas) ?

Vous devrez peut-être modifier l’ID d’incrément pour les nouvelles entités de base de données dans les cas suivants :

* Après une restauration par sauvegarde irréversible sur un site actif
* Certains enregistrements de commande ont été perdus, mais leurs identifiants sont déjà utilisés par les passerelles de paiement (comme PayPal) pour votre compte marchand actuel. Dans ce cas, les passerelles de paiement arrêtent le traitement des nouvelles commandes ayant les mêmes ID, renvoyant l&#39;erreur « ID de facture en double »

>[!NOTE]
>
>Vous pouvez également résoudre le problème de passerelle de paiement pour PayPal en autorisant plusieurs paiements par ID de facture dans les Préférences de réception des paiements de PayPal. Voir [Demande rejetée de la passerelle PayPal - problème de facture en double](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-26838) dans notre base de connaissances du support.

## Étapes préalables

1. Recherchez les magasins et les entités pour lesquels le nouvel ID d’incrément doit être modifié.
1. [Connexion](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) à votre base de données MySQL. Pour Adobe Commerce sur les infrastructures cloud, vous devez d’abord [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr).
1. Vérifiez la valeur auto\_increment actuelle pour la table de séquences d&#39;entités à l&#39;aide de la requête suivante :

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Exemple

Si vous vérifiez une incrémentation automatique pour une commande sur le magasin avec l’*ID=1*, le nom de la table serait :

```sql
'sequence_order_1'
```

Si la valeur de la colonne `auto_increment` est *1234*, la commande suivante passée dans le magasin avec *ID=1* aura le *ID \#100001234*.

### Documentation connexe

* [Configurez une connexion à la base de données MySQL distante](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote) dans notre documentation destinée aux développeurs.

## Mettre à jour l’entité pour modifier l’ID d’incrément

Mettez à jour l&#39;entité à l&#39;aide de la requête suivante :

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Important : la nouvelle valeur d’incrément doit être supérieure à la valeur actuelle, et non inférieure.

### Exemple

Après avoir exécuté la requête suivante :

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

la prochaine commande passée dans le magasin avec *ID=1* aura le *ID \#100002000*.

## Étapes supplémentaires recommandées dans l’environnement de production (cloud)

Avant d’exécuter la requête `ALTER TABLE` sur l’environnement de production d’Adobe Commerce sur l’infrastructure cloud, nous vous recommandons vivement d’effectuer les étapes suivantes :

* Tester l’ensemble de la procédure de modification de l’ID d’incrément dans votre environnement d’évaluation
* [Créer](/help/how-to/general/create-database-dump-on-cloud.md) une sauvegarde de base de données pour restaurer votre base de données de production en cas d’échec

## Documentation connexe

* [Créer une image mémoire de la base de données sur Cloud](/help/how-to/general/create-database-dump-on-cloud.md) dans notre base de connaissances d’assistance
* [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr) dans notre documentation destinée aux développeurs
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
