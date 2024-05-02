---
title: "B2B : les entreprises ne peuvent pas accéder aux pages de profil au niveau du magasin"
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.4 B2B lié aux erreurs des sociétés enregistrées sur leurs pages de compte sur le storefront.
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B : les entreprises ne peuvent pas accéder aux pages de profil au premier plan du magasin

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.4 B2B lié aux erreurs des sociétés enregistrées sur leurs pages de compte sur le storefront.

## Problème

Les clients (entreprises) peuvent créer un compte d’entreprise sur le site, mais obtiennent la variable *&quot;Aucune entité de ce type avec customerId = &quot;* et *&quot;Vous n&#39;avez pas encore de compte d&#39;entreprise&quot;* messages d’erreur. Ils peuvent également obtenir la variable *&quot;Erreur interne 500 du serveur&quot;* lors de la tentative d’accès à la page Profil de l’entreprise.

## Correctif

Pour télécharger l’archive avec un correctif, cliquez sur le lien suivant :

[Téléchargez MDVA-9013\_EE\_2.2.2\_compositeur.patch.](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### Versions Adobe Commerce compatibles

Le correctif a été créé pour :

* Adobe Commerce on-premise 2.2.2

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud de la version 2.2.0 à 2.2.4
* Adobe Commerce sur site de la version 2.2.0 à la version 2.2.1 et de la version 2.2.3 à la version 2.2.4

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.
