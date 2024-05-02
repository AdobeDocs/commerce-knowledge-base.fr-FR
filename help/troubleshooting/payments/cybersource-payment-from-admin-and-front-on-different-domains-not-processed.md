---
title: Paiement en cybersource depuis l’administrateur et devant sur différents domaines non traités
description: Cet article fournit un correctif pour la limitation connue d’Adobe Commerce 2.3.0 liée au fait de ne pas pouvoir traiter les paiements Cybersource depuis storefront et Commerce Admin, s’ils se trouvent sur des domaines différents.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Paiement en cybersource depuis l’administrateur et devant sur différents domaines non traités

Cet article fournit un correctif pour la limitation connue d’Adobe Commerce 2.3.0 liée au fait de ne pas pouvoir traiter les paiements Cybersource depuis storefront et Commerce Admin, s’ils se trouvent sur des domaines différents.

>[!NOTE]
>
>L’intégration de paiement Adobe Commerce Cybersource principale est obsolète depuis la version 2.3.3 et sera complètement supprimée de la version 2.4.0. Utilisez la variable [extension officielle](https://marketplace.magento.com/cybersource-global-payment-management.html) à partir de Marketplace.

## Problème

La mise en oeuvre précédente de l’intégration Cybersource autorisait le traitement des paiements à partir d’un seul domaine. Par conséquent, si votre vitrine Adobe Commerce se trouve sur un domaine différent de celui de l’administrateur Commerce, vous obtenez l’erreur suivante lorsque vous essayez de passer une commande à l’aide de Cybersource dans l’administrateur : &quot; *Le chargement refusé par X-Frame-Options : https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ n’autorise pas le cadre d’origine croisée.* ..&quot;

<u>Étapes à reproduire</u>:

1. Configurez l’administrateur sur un autre sous-domaine.
1. Configuration de Cybersource pour le magasin sous **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de paiement** > **CyberSource**.
1. Accédez à **Ventes** > **Commandes**.
1. Créez une nouvelle commande.
1. Créez un client.
1. Renseignez les détails du client.
1. Renseignez les détails de la commande (produits, mode de livraison).
1. Sélectionnez Cybersource comme mode de paiement.
1. Envoyer la commande.

<u>Résultat attendu</u>: la commande est passée sans problème.

<u>Résultat réel</u>: la page Ordre affiche une icône de chargement, mais la commande n’est jamais placée. L&#39;erreur s&#39;affiche dans la console.

## Solution

Le correctif joint fournit l’amélioration de l’intégration à Cybersource. Après avoir appliqué le correctif, vous devez créer un profil supplémentaire avec Cybersource pour traiter les paiements dans l’administrateur, et ajouter les informations d’identification requises dans la configuration Cybersource dans l’administrateur Commerce sous **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de paiement** > **CyberSource**.

>[!NOTE]
>
>L’amélioration est incluse dans les versions 2.2.9 et 2.3.1 d’infrastructure sur site et cloud d’Adobe Commerce.

## Correctif

Il y a plusieurs correctifs joints à cet article, différents correctifs pour différentes versions. Pour télécharger un correctif, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

* [Téléchargez MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch.](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [Téléchargez MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch.](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [Téléchargez MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch.](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [Téléchargez MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch.](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Versions Adobe Commerce compatibles

Les correctifs ont été créés pour une version spécifique indiquée dans le nom du fichier de correctif. Par exemple, MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch a été créé pour Adobe Commerce 2.1.9 et est le meilleur correctif à utiliser pour cette version.

Les correctifs sont également compatibles avec les versions suivantes :

* Adobe Commerce on-premise 2.1.3-2.1.17 ; Adobe Commerce on cloud infrastructure 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce sur site 2.2.0-2.2.3 ; Adobe Commerce sur l’infrastructure cloud 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce sur site 2.2.4-2.2.7 ; Adobe Commerce sur l’infrastructure cloud 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce on-premise 2.2.8, 2.3.0 ; Adobe Commerce on cloud infrastructure 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Comment appliquer un correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

## Fichiers attachés
