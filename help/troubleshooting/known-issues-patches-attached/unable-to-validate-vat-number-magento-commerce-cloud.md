---
title: Impossible de valider le numéro de TVA - Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit un correctif pour le problème en cas d’erreur lors de la vérification du numéro de TVA.
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Impossible de valider le numéro de TVA - Adobe Commerce sur l’infrastructure cloud

Cet article fournit un correctif pour le problème en cas d’erreur lors de la vérification du numéro de TVA.

## Produits et versions concernés

Toutes les versions d’infrastructure cloud d’Adobe Commerce sur site et d’Adobe Commerce jusqu’à la version 2.3.6 (y compris la version 2.3.5-p1) ont été affectées, y compris les versions p1 et p2 déjà publiées. Cela inclut :

* 2.3.5-p1
* 2.3.5
* 2.3.4 - 2.3.4-p2
* 2.3.3 - 2.3.3-p1
* 2.3.2 -2.3.2-p2
* 2.0.0 - 2.3.1

## Problème

<u>Étapes à reproduire :</u>

1. Accédez à **Magasins** > **Configuration** > **Clients** > **Configuration client** > **Créer des options de compte** et défini **Activation de l’affectation automatique** to **Groupe de clients** to *Oui*.
1. Accédez à **Général** > **Informations sur le magasin** > et définissez un Pays et un Numéro de TVA valides.
1. Cliquez sur **Valider le numéro de TVA**.

<u>Résultat attendu :</u>

La validation a réussi.

<u>Résultat réel :</u>

L&#39;erreur suivante s&#39;affiche : &quot;*Erreur lors de la vérification du numéro de TVA.*&quot;

## Solution

Appliquez la variable [correctif](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip) fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
