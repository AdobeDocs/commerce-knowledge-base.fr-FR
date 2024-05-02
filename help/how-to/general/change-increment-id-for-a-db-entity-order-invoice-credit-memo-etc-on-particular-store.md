---
title: Modifier l’identifiant d’incrément d’une entité DB (commande, facture, note de crédit, etc.) sur un magasin particulier
description: Cet article explique comment modifier l’identifiant d’incrément d’une entité de base de données Adobe Commerce (DB) (commande, facture, note de crédit, etc.) sur un magasin Adobe Commerce spécifique à l’aide de l’instruction SQL "ALTER TABLE".
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Modifier l’identifiant d’incrément d’une entité DB (commande, facture, note de crédit, etc.) sur un magasin particulier

Cet article explique comment modifier l’identifiant d’incrément d’une entité de base de données Adobe Commerce (DB) (commande, facture, note de crédit, etc.) sur un magasin Adobe Commerce spécifique à l’aide de la variable `ALTER TABLE` Instruction SQL.

## Versions affectées

* Adobe Commerce sur site : 2.x.x
* Adobe Commerce sur l’infrastructure cloud : 2.x.x
* MySQL : any [version prise en charge](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## Quand devez-vous modifier l’ID d’incrément (cas) ?

Vous devrez peut-être modifier l’ID d’incrément pour les nouvelles entités de base de données dans les cas suivants :

* Après une restauration sur un site Live
* Certains enregistrements de commande ont été perdus, mais leurs identifiants sont déjà utilisés par les passerelles de paiement (comme PayPal) pour votre compte marchand actuel. Dans ce cas, les passerelles de paiement arrêtent de traiter de nouvelles commandes ayant le même identifiant, renvoyant l’erreur &quot;Dupliquer l’identifiant de facture&quot;.

>[!NOTE]
>
>Vous pouvez également résoudre le problème de passerelle de paiement pour PayPal en autorisant plusieurs paiements par identifiant de facture dans les préférences de réception des paiements de PayPal. Voir [Demande de rejet de la passerelle PayPal - problème de facture en double](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) dans notre base de connaissances de soutien.

## Étapes préalables

1. Recherchez les magasins et les entités pour lesquels le nouvel ID d’incrément doit être modifié.
1. [Connexion](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) à votre base de données MySQL. Pour Adobe Commerce sur l’infrastructure cloud, vous devez d’abord [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Vérifiez la valeur auto\_incrément actuelle de la table de séquence d’entités à l’aide de la requête suivante :

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Exemple

Si vous cochez une auto-incrémentation pour une commande sur le magasin avec *ID=1*, le nom de la table serait :

```sql
'sequence_order_1'
```

Si la valeur de la variable `auto_increment` column is *1234*, la commande suivante placée dans le magasin avec *ID=1* aura la variable *ID \#100001234*.

### Documentation connexe

* [Configuration d’une connexion de base de données MySQL distante](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) dans notre documentation destinée aux développeurs.

## Mettre à jour l’entité pour modifier l’ID d’incrément

Mettez à jour l’entité à l’aide de la requête suivante :

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>Important : La nouvelle valeur d’incrément doit être supérieure à la valeur actuelle, et non inférieure !

### Exemple

Après avoir exécuté la requête suivante :

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

commande suivante placée dans le magasin avec *ID=1* aura la variable *ID \#100002000*.

## Autres étapes recommandées dans l’environnement de production (Cloud)

Avant d’exécuter la fonction `ALTER TABLE` sur l’environnement de production d’Adobe Commerce sur l’infrastructure cloud, il est vivement recommandé d’effectuer les étapes suivantes :

* Testez l’ensemble de la procédure de modification de l’identifiant d’incrément dans votre environnement d’évaluation.
* [Créer](/help/how-to/general/create-database-dump-on-cloud.md) sauvegarde de la base de données pour restaurer la base de données de production en cas d’échec

## Documentation connexe

* [Création d’un vidage de base de données sur Cloud](/help/how-to/general/create-database-dump-on-cloud.md) dans notre base de connaissances de soutien.
* [SSH vers votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) dans notre documentation destinée aux développeurs.
