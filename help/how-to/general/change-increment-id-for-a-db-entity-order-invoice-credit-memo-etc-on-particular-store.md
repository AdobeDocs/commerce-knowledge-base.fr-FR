---
title: Modifiez l’identifiant d’incrément d’une entité DB (commande, facture, note de crédit, etc.) sur un magasin particulier.
description: Cet article explique comment modifier l’ID d’incrément d’une entité de base de données Adobe Commerce (DB) (commande, facture, note de crédit, etc.) sur un magasin Adobe Commerce particulier à l’aide de l’instruction SQL "ALTER TABLE".
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Modifiez l’identifiant d’incrément d’une entité DB (commande, facture, note de crédit, etc.) sur un magasin particulier.

Cet article explique comment modifier l’ID d’incrément d’une entité de base de données Adobe Commerce (DB) (commande, facture, note de crédit, etc.) sur un magasin Adobe Commerce particulier à l’aide de l’instruction SQL `ALTER TABLE`.

## Versions affectées

* Adobe Commerce sur site : 2.x.x
* Adobe Commerce sur l’infrastructure cloud : 2.x.x
* MySQL : toute [version prise en charge](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements-tech.html#database)

## Quand devez-vous modifier l’ID d’incrément (cas) ?

Vous devrez peut-être modifier l’ID d’incrément pour les nouvelles entités de base de données dans les cas suivants :

* Après une restauration sur un site Live
* Certains enregistrements de commande ont été perdus, mais leurs identifiants sont déjà utilisés par les passerelles de paiement (comme PayPal) pour votre compte marchand actuel. Dans ce cas, les passerelles de paiement arrêtent de traiter de nouvelles commandes ayant le même identifiant, renvoyant l’erreur &quot;Dupliquer l’identifiant de facture&quot;.

>[!NOTE]
>
>Vous pouvez également résoudre le problème de passerelle de paiement pour PayPal en autorisant plusieurs paiements par identifiant de facture dans les préférences de réception des paiements de PayPal. Voir [Demande de refus de la passerelle PayPal - problème de facture en double](/help/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.md) dans notre base de connaissances d’assistance.

## Étapes préalables

1. Recherchez les magasins et les entités pour lesquels le nouvel ID d’incrément doit être modifié.
1. [Connectez-vous](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) à votre base de données MySQL. Pour Adobe Commerce sur l’infrastructure cloud, vous devez d’abord [SSH dans votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Vérifiez la valeur auto\_incrément actuelle de la table de séquence d’entités à l’aide de la requête suivante :

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### Exemple

Si vous cochez une auto-incrémentation pour une commande sur le magasin avec *ID=1*, le nom de la table sera :

```sql
'sequence_order_1'
```

Si la valeur de la colonne `auto_increment` est *1234*, l’ordre suivant placé dans le magasin avec *ID=1* aura le *ID \#100001234*.

### Documentation connexe

* [Configurez une connexion à base de données MySQL distante](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/mysql_remote.html) dans notre documentation destinée aux développeurs.

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

la commande suivante placée dans le magasin avec *ID=1* aura le *ID \#100002000*.

## Autres étapes recommandées dans l’environnement de production (Cloud)

Avant d’exécuter la requête `ALTER TABLE` sur l’environnement de production d’Adobe Commerce sur l’infrastructure cloud, nous vous recommandons vivement d’effectuer les étapes suivantes :

* Testez l’ensemble de la procédure de modification de l’identifiant d’incrément dans votre environnement d’évaluation.
* [Créez](/help/how-to/general/create-database-dump-on-cloud.md) une sauvegarde de base de données pour restaurer la base de données de production en cas d’échec

## Documentation connexe

* [Créer un vidage de base de données sur Cloud](/help/how-to/general/create-database-dump-on-cloud.md) dans notre base de connaissances de support
* [SSH à votre environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) dans notre documentation destinée aux développeurs
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
