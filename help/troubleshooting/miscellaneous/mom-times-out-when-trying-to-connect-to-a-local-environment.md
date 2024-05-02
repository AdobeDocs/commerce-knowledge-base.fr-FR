---
title: Système Magento Order Management (OMS) pour Adobe Commerce expire
description: Cet article fournit une solution au problème où le système de Magento Order Management (OMS) pour Adobe Commerce ne peut pas enregistrer le micro-service installé localement avec MOM en utilisant ngrok, car MOM expire lors de la tentative de rappel.
exl-id: 19149d8c-ea24-46fb-8815-9f637afe46ca
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Système Magento Order Management (OMS) pour Adobe Commerce expire

Cet article fournit une solution au problème où le système de Magento Order Management (OMS) pour Adobe Commerce ne peut pas enregistrer le micro-service installé localement avec MOM en utilisant ngrok, car MOM expire lors de la tentative de rappel.

## Produits et versions concernés

* Adobe Commerce 2.3.1
* OMS
* ngrok

>[!WARNING]
>
>Clause de non-responsabilité : Adobe Commerce ne recommande ni n’approuve aucun outil particulier pour la création de tunnels. Les suggestions ci-dessus ne sont que des suggestions. Pour plus d’informations, consultez la [Documentation sur ngrok](https://ngrok.com/docs).

## Problème

<u>Étapes à reproduire</u>

1. Installez Adobe Commerce sur votre environnement local.
1. Configurez ngrok pour créer un tunnel qui expose votre serveur local.
1. Essayer [connexion à OMS](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).

<u>Résultat attendu</u>

Connexion établie avec succès.

<u>Résultat réel</u>

MCOM semble expirer lors de la tentative de rappel vers l’URL de ngrok.

## Cause

L’une des raisons possibles du délai d’expiration est que les serveurs sont situés trop loin géographiquement et que la connexion prend trop de temps.

## Solution

Ajoutez un paramètre spécifiant votre région lors du démarrage de ngrok. Comme dans l’exemple suivant :

```bash
./ngrok http 80 -region eu
```

La région par défaut est les États-Unis. Voir [toutes les valeurs possibles](https://ngrok.com/docs#config_region).
