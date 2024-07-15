---
title: 404 Erreur au niveau du magasin une fois que la mise à jour des plannings de règles de prix du catalogue est effectuée
description: Cet article fournit un correctif et les étapes requises pour résoudre le problème connu d’Adobe Commerce 2.2.1 lié à l’obtention d’une erreur 404 sur toutes les pages principales du magasin, après la création d’une mise à jour de règle de prix de catalogue et la modification ultérieure de son heure de début. Pour résoudre le problème, vous devez appliquer le correctif.
exl-id: 7ea148a5-56cb-479a-8b2f-fae8b3bd4b22
feature: Cache, Catalog Management, Marketing Tools, Orders, Price Rules
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 404 Erreur au niveau du magasin une fois que la mise à jour des plannings de règles de prix du catalogue est effectuée

Cet article fournit un correctif et les étapes requises pour résoudre le problème connu d’Adobe Commerce 2.2.1 lié à l’obtention d’une erreur 404 sur toutes les pages principales du magasin, après la création d’une mise à jour de règle de prix de catalogue et la modification ultérieure de son heure de début. Pour résoudre le problème, vous devez appliquer le correctif.

## Problème

Les pages Storefront ne sont plus disponibles, renvoyant une erreur 404. Le problème s’affiche une fois que la mise à jour de la règle de prix du catalogue active est arrivée à échéance, à condition que la date de début de cette mise à jour ait été modifiée après la création initiale.

<u>Étapes à reproduire</u> :

1. Dans l’administrateur Commerce, créez une règle de prix de catalogue sous **Marketing** > **Promotions** > **Règle de prix de catalogue**.
1. Dans la grille **Règle de prix du catalogue**, cliquez sur **Modifier,** programmer une nouvelle mise à jour et définissez **État** sur *Actif.*
1. Accédez à **Contenu** > **Évaluation du contenu** > **Tableau de bord.**
1. Sélectionnez la mise à jour récemment créée et modifiez son heure de début.
1. Enregistrez les modifications.

<u>Résultat attendu</u> :

Lorsque la date de début de la mise à jour prend effet, la règle de prix du catalogue est appliquée avec succès.

<u>Résultat réel</u> :

Lorsque la date de début de la mise à jour prend effet, tous les catalogues et produits du storefront ne sont plus disponibles, renvoyant l’erreur 404.

## Solution

Pour restaurer les pages du catalogue et pouvoir utiliser pleinement la fonctionnalité de mise à jour des règles de prix du catalogue, vous devez installer le correctif, supprimer la règle manuellement et dans l’administrateur et corriger les liens non valides dans la base de données. Vous devrez également recréer la règle de prix du catalogue.

Vous trouverez ci-dessous une description détaillée des étapes requises :

1. [Appliquez le correctif](#patch).
1. Dans l’administrateur Commerce, supprimez la règle de prix du catalogue liée au problème (où l’heure de début a été mise à jour). Pour ce faire, ouvrez la page des règles sous **Marketing** > **Promotions** > **Règle de prix du catalogue**, puis cliquez sur **Supprimer la règle**.
1. L&#39;accès à la base de données supprime manuellement l&#39;enregistrement associé de la table `catalogrule`.
1. Corrigez les liens non valides dans la base de données. Pour plus d’informations, voir le [paragraphe associé](#fix_links) .
1. Dans l’administrateur Commerce sous **Marketing**, accédez à **Promotions** > **Règle de prix du catalogue**, puis créez la nouvelle règle avec la configuration requise.
1. Effacez le cache du navigateur sous **Système** > **Gestion du cache**.
1. Assurez-vous que les tâches cron sont correctement configurées et peuvent être exécutées avec succès.

## Correctif {#patch}

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-7392\_EE\_2.2.1\_COMPOSER\_v2.patch.](assets/MDVA-7392_EE_2.2.1_COMPOSER_v2.patch.zip)

## Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce 2.2.1

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.2.0 - 2.2.4
* Adobe Commerce on-premise 2.2.0 et 2.2.2 - 2.2.4

## Comment appliquer le correctif

Pour plus d&#39;informations, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Correction des liens non valides pour l’évaluation dans DB {#fix_links}

>[!WARNING]
>
>Il est vivement recommandé de créer une sauvegarde de base de données avant toute manipulation de base de données. Nous vous recommandons également de tester d’abord les requêtes sur l’environnement de développement.

Procédez comme suit pour corriger les lignes contenant des liens non valides vers la table `staging_update`.

1. Vérifiez si les liens non valides vers la table `staging_update` existent dans la table `flag`. Il s’agit d’enregistrements où `flag_code=staging`.
1. Identifiez la version non valide de la table `flag` à l’aide de la requête suivante :

   ```sql
   SELECT flag_data FROM flag WHERE flag_code = 'staging';
   ```

1. Dans la table `staging_update`, sélectionnez la version existante inférieure à la version actuelle (non valide) et récupérez la valeur de version qui est de deux nombres. Vous l’utilisez, et non la version précédente, pour éviter la situation où la version précédente est la version maximale dans la table `staging_update` qui peut être appliquée et nous devons toujours l’appliquer à nouveau.

   ```sql
   SELECT id FROM staging_update WHERE id < %current_id% ORDER BY id DESC LIMIT 1, 1
   ```

   La version que vous obtenez en réponse est votre version valide `id`.

1. Pour les lignes comportant des liens non valides dans la table `flag`, définissez les valeurs `flag_data` sur les données qui contiendront un ID de version valide. Cela permet d’économiser les performances à l’étape de réindexation et d’éviter de réindexer toutes les entités.

   ```sql
   UPDATE flag SET flag_data=REPLACE(flag_data, '%invalid_id%', '%new_valid_id%') WHERE flag_code='staging';
   ```

<u>Exemple :</u>

```sql
SELECT flag_data FROM flag WHERE flag_code = 'staging'; <code class="language-bash">Response < 2.2 version</code>
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| a:1:{s:15:"current_version";s:10:"1490005140";} |
```

```bash
+-------------------------------------------------+
```

```bash
Response from 2.2 version
```

```bash
+-------------------------------------------------+
```

```bash
| flag_data                                       |
```

```bash
+-------------------------------------------------+
```

```bash
| {"current_version":"1490005140"} |
```

```bash
+-------------------------------------------------+
```

```sql
SELECT id FROM staging_update WHERE id < 1490005140 <code class="language-sql">ORDER BY id DESC LIMIT 1, 1</code>;
```

```bash
Response:
```

```bash
1490005138
```

```sql
UPDATE flag SET flag_data=REPLACE(flag_data, '1490005140', '1490005138') WHERE flag_code='staging';
```

## Fichiers attachés
