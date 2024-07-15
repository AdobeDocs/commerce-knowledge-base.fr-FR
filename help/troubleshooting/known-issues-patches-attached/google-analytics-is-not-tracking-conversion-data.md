---
title: Les Google Analytics ne suivent pas les données de conversion
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.4 lié aux Google Analytics qui ne suivent pas les données de conversion.
exl-id: b9012fd1-4f90-41e9-9559-0343ee052ec6
feature: Configuration, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Les Google Analytics ne suivent pas les données de conversion

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.4 lié aux Google Analytics qui ne suivent pas les données de conversion.

>[!NOTE]
>
>Le problème a été corrigé dans Adobe Commerce 2.2.6.

## Problème

Les données de conversion n’ont pas été suivies par les Google Analytics en raison d’une erreur dans le code du composant Google Analytics.

<u>Étapes à reproduire</u> :

1. Activez et configurez la fonctionnalité Google Analytics dans l’administrateur Commerce sous **Magasins** > **Paramètres** > **Configuration** > **Ventes** > **API Google** > **Google Analytics**.
1. Cliquez sur **Enregistrer la configuration**.
1. Passer une commande sur la vitrine.
1. Accédez à **Tableau de bord des Google Analytics** > **Conversions** > **Aperçu**.
1. Définissez la période sur la date actuelle.

<u>Résultat attendu</u> :

L’ordre apparaît dans les données de conversion.

<u>Résultat réel</u> :

L’ordre n’apparaît pas dans les données de conversion.

## Solution

Le correctif corrige l’erreur dans le code du composant Google Analytics. Après l’application des correctifs, les données de conversion sont suivies par les Google Analytics.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[Téléchargez MDVA-11263\_EE\_2.2.4\_v1.compositeur.patch.](assets/MDVA-11263_EE_2.2.4_v1.composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce on-premise 2.2.4

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce On-Premise 2.2.5
* Adobe Commerce sur l’infrastructure cloud 2.2.4, 2.2.5

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
