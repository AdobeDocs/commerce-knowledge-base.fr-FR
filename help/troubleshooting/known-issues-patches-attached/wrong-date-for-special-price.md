---
title: Mauvaise date pour le prix spécial
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.2 lié à la date "from" (prix spécial à partir de) du produit qui est incorrect si sa valeur est modifiée par l’administrateur dont le paramètre régional de l’interface est différent.
exl-id: fc109550-951e-4900-97e3-4ff3e7e5a395
feature: Orders, Personalization, User Account
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Mauvaise date pour le prix spécial

Cet article fournit un correctif pour le problème connu d’Adobe Commerce 2.2.2 lié à la date &quot;from&quot; (prix spécial à partir de) du produit qui est incorrect si sa valeur est modifiée par l’administrateur dont le paramètre régional de l’interface est différent.

## Problème

Lorsque vous définissez/modifiez le prix spécial d’un produit, la date et l’heure actuelles sont enregistrées dans la base de données en tant que valeur de l’attribut `special_from_date` (invisible lors de la modification d’un produit). Si vous modifiez le prix spécial et que votre compte utilisateur admin est défini sur un autre paramètre régional de l’interface, une valeur incorrecte peut être définie sur `special_from_date` en raison des problèmes liés à l’analyse du format de date pour différents paramètres régionaux.

<u>Étapes à reproduire</u> :

Conditions préalables : le paramètre régional de l’utilisateur administrateur est Anglais (Etats-Unis).

1. Connectez-vous à l’administrateur Commerce.
1. Accédez aux paramètres du compte d’utilisateur administrateur.
1. Définissez Interface Locale sur Ukrainienne.
1. Cliquez sur **Enregistrer le compte**.
1. Accédez à **Catalogue** > **Produit**.
1. Sélectionnez n’importe quel produit.
1. Sur la page du produit, cliquez sur **Advanced Tarification**.
1. Ajoutez un prix spécial.
1. Enregistrez le produit.
1. Répétez les étapes 7 à 9.
1. Accédez à **System** > **Action Logs**.
1. Vérifiez le journal pour la mise à jour du produit.

<u>Résultats attendus</u> :

La date de début du prix spécial doit être la date courante.

<u>Résultats réels</u> :

La date de début du prix spécial est fixée à quelques années dans le futur, ce qui empêche l&#39;activité du prix spécial.

## Solution

L’application du correctif empêchera le problème de se reproduire. Pour corriger les données des produits dont la date a été incorrectement définie, redéfinissez le prix spécial après application du correctif.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant :

[Téléchargez MDVA-11605\_EE\_2.2.2\_COMPOSER\_v1.patch.](assets/MDVA-11605_EE_2.2.2_COMPOSER_v1.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce (toutes les méthodes de déploiement) 2.2.2

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur site 2.1.0-2.1.18, 2.2.0-2.2.5
* Adobe Commerce sur l’infrastructure cloud 2.1.11-2.1.18, 2.2.0-2.2.5

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Fichiers attachés
