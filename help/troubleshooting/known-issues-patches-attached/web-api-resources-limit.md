---
title: API Web ne pouvant pas traiter les demandes comportant plus de 20 éléments dans le tableau
description: Cet article fournit une solution au problème de l’impossibilité pour l’API Web de traiter un message contenant plus de 20 éléments dans le tableau pour Adobe Commerce 2.4.3.
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# API Web ne pouvant pas traiter les demandes comportant plus de 20 éléments dans le tableau

Cet article fournit une solution au problème de l’impossibilité pour l’API Web de traiter un message contenant plus de 20 éléments dans le tableau pour Adobe Commerce 2.4.3.

## Produits et versions concernés :

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 et 2.3.7-p1
* Magento Open Source 2.4.3 et 2.3.7-p1

## Problème

L’API Web ne peut pas traiter le message (par exemple, la mise à jour du stock) qui contient plus de 20 éléments dans le tableau .

## Cause

Dans Adobe Commerce 2.4.3, la limitation de débit intégrée a été ajoutée aux API du Magento pour empêcher les attaques par déni de service (DoS).

Par défaut, la limitation de débit de l’API intégrée suivante est disponible :

* Les demandes REST contenant des entrées représentant une liste d’entités sont limitées à 20 entités au maximum par défaut.
* Les requêtes REST et GraphQL qui autorisent les résultats paginés sont limitées à 300 éléments par défaut par page.

## Solution

Pour désactiver les limites d’entrée sur la requête de l’API REST, appliquez l’un des correctifs suivants (en fonction de votre version) :

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### Versions Adobe Commerce compatibles

Les correctifs ont été créés pour :

* Adobe Commerce sur l’infrastructure cloud 2.4.3 et 2.3.7-p1
* Adobe Commerce on-premise 2.4.3 et 2.3.7-p1

Les correctifs ne sont compatibles avec aucune autre version d’Adobe Commerce.

### Comment appliquer le correctif

Décompressez le fichier téléchargé. `.zip` et appliquez le correctif comme décrit dans la section [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

>[!WARNING]
>
>Si vous pensez que votre boutique est victime d’une attaque par déni de service, Adobe recommande de réduire les limites d’entrée par défaut à une valeur inférieure afin d’imposer des restrictions sur le nombre de ressources pouvant être demandées.  Vous pouvez personnaliser les limites par défaut par programmation à l’aide de [arguments du constructeur de classe](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)
>comme décrit dans notre documentation destinée aux développeurs : [Sécurité de l’API > Limitation de débit > Entrées maximales du paramètre](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting).

## Lecture connexe

[Sécurité des API > Limitation de débit](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting) dans notre documentation destinée aux développeurs.
