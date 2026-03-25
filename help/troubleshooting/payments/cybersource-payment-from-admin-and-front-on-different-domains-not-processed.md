---
title: Paiement Cybersource de l'administrateur et front sur différents domaines non traité
description: Cet article fournit un correctif pour la limitation connue d’Adobe Commerce 2.3.0 liée au fait de ne pas avoir la possibilité de traiter les paiements Cybersource à partir de storefront et de l’administrateur Commerce, s’ils se trouvent sur des domaines différents.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Paiement Cybersource de l&#39;administrateur et front sur différents domaines non traité

Cet article fournit un correctif pour la limitation connue d’Adobe Commerce 2.3.0 liée au fait de ne pas avoir la possibilité de traiter les paiements Cybersource à partir de storefront et de l’administrateur Commerce, s’ils se trouvent sur des domaines différents.

>[!NOTE]
>
>L’intégration de base des paiements Adobe Commerce Cybersource est obsolète depuis la version 2.3.3 et sera complètement supprimée dans la version 2.4.0. Utilisez plutôt l’extension [officielle](https://marketplace.magento.com/cybersource-global-payment-management.html) de Marketplace.

## Problème

La mise en œuvre précédente de l&#39;intégration de Cybersource permettait de traiter les paiements d&#39;un seul domaine. Par conséquent, si votre storefront Adobe Commerce se trouve sur un domaine différent de celui de l’administrateur Commerce, vous obtenez l’erreur suivante lors de la tentative de commande à l’aide de Cybersource dans l’administrateur : «  *Chargement refusé par X-Frame-Options: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ n’autorise pas le framing entre origines.* .. »

<u>Procédure à suivre </u> :

1. Configurez l’administrateur sur un autre sous-domaine.
1. Configurez Cybersource pour le magasin sous **Magasins** > Paramètres > **Configuration** > **Ventes** > **Modes de paiement** > **CyberSource**.
1. Accédez à **Ventes** > **Commandes**.
1. Créer une nouvelle commande.
1. Créez un nouveau client.
1. Saisissez les détails du client.
1. Saisissez les détails de la commande (produits, mode d’expédition).
1. Sélectionnez Cybersource comme mode de paiement.
1. Envoyer la commande.

<u>Résultat attendu</u> : la commande est passée sans problème.

<u>Résultat réel</u> : la page Commande affiche une icône de chargement, mais la commande n’est jamais passée. L’erreur s’affiche dans la console.

## Solution

Le correctif ci-joint améliore l’intégration à Cybersource. Après avoir appliqué le correctif, vous devez créer un profil supplémentaire avec Cybersource pour traiter les paiements dans l’administrateur, et ajouter les informations d’identification requises dans la configuration de Cybersource dans l’administrateur Commerce sous **Magasins** > Paramètres > **Configuration** > **Ventes** > **Méthodes de paiement** > **CyberSource**.

>[!NOTE]
>
>L’amélioration est incluse dans les versions 2.2.9 et 2.3.1 de l’infrastructure sur site et cloud d’Adobe Commerce.

## Patch

Plusieurs correctifs sont joints à cet article, différents correctifs pour différentes versions. Pour télécharger un correctif, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

* [Télécharger MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [Télécharger MDVA-8609\_EE\_2.2\_COMPOSER\_v2.patch](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [Télécharger MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [Télécharger MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Versions d’Adobe Commerce compatibles

Les correctifs ont été créés pour une version particulière indiquée dans le nom de fichier de correctif. Par exemple, MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch a été créé pour Adobe Commerce 2.1.9 et est le meilleur correctif à utiliser pour cette version.

Les correctifs sont également compatibles avec les versions suivantes :

* Adobe Commerce On-Premise 2.1.3-2.1.17 ; Adobe Commerce sur l’infrastructure cloud 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce On-Premise 2.2.0 à 2.2.3 ; Adobe Commerce sur l’infrastructure cloud 2.2.0 à 2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce On-Premise 2.2.4-2.2.7 ; Adobe Commerce sur l’infrastructure cloud 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce on-premise 2.2.8, 2.3.0 ; Adobe Commerce on cloud infrastructure 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Application d’un correctif

Pour obtenir des instructions, consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) dans notre base de connaissances d’assistance.

## Fichiers attachés
