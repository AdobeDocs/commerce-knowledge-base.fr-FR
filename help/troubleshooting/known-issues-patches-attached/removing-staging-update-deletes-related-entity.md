---
title: La suppression de la mise à jour d’évaluation supprime l’entité associée.
description: Cet article fournit un correctif pour le problème Adobe Commerce 2.2.3 connu lié à l’entité (catégorie, page CMS, etc.) elle-même supprimée lorsque la mise à jour de planning associée est supprimée.
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# La suppression de la mise à jour d’évaluation supprime l’entité associée.

Cet article fournit un correctif pour le problème Adobe Commerce 2.2.3 connu lié à l’entité (catégorie, page CMS, etc.) elle-même supprimée lorsque la mise à jour de planning associée est supprimée.

>[!NOTE]
>
>Le problème a été corrigé dans Adobe Commerce 2.2.6.

## Problème

Lorsque vous supprimez une mise à jour de planning active entre ses dates de début et de fin, l’entité associée (catégorie, sous-catégorie, page CMS) est également supprimée.

<u>Étapes à reproduire (avec catégories)</u> :

1. Connectez-vous à l’administrateur Commerce.
1. Créez une nouvelle sous-catégorie sous **Catalogue** > **Catégories**.
1. Créez une mise à jour d’évaluation avec les heures de début et de fin.
1. Patientez jusqu’à ce que la mise à jour soit appliquée ; c’est l’heure de début qui arrive.
1. Supprimez la mise à jour à l’aide du lien **Afficher/Modifier**.

<u>Résultats attendus</u> :

La mise à jour est supprimée et la sous-catégorie existe toujours dans l’Admin.

<u>Résultats réels</u> :

La mise à jour et la sous-catégorie sont supprimées.

## Solution

Appliquez le correctif fourni dans cet article, puis videz le cache en cours d’exécution.

```bash
bin/magento
  cache:clean
```

## Correctif

Les correctifs sont joints à cet article. Pour télécharger un correctif, faites défiler l&#39;écran jusqu&#39;à la fin de l&#39;article et cliquez sur le nom du fichier ou cliquez sur le lien correspondant :

* [Téléchargez MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch.](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch.](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch.](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### Versions Adobe Commerce compatibles :

Les correctifs ont été créés pour :

* MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch a été créé pour Adobe Commerce (toutes les méthodes de déploiement) 2.2.3
* MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch a été créé pour Adobe Commerce (toutes les méthodes de déploiement) 2.2.4
* MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch a été créé pour Adobe Commerce (toutes les méthodes de déploiement) 2.2.5

Le correctif MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur site 2.2.0-2.2.2
* Adobe Commerce sur l’infrastructure cloud 2.2.0-2.2.3

Le correctif MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur site 2.1.0-2.1.18, 2.2.0-2.2.3
* Adobe Commerce sur l’infrastructure cloud 2.1.0-2.1.18, 2.2.0-2.2.3

Le correctif MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud 2.2.5

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
