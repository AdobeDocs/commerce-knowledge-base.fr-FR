---
title: Nouveau domaine redirigé vers le domaine par défaut
description: Cet article fournit un correctif pour le problème où le nouveau domaine redirige vers le domaine par défaut dans l’environnement existant ou dans un autre environnement.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%
---
# Nouveau domaine redirigé vers le domaine par défaut

Cet article fournit un correctif pour le problème où le nouveau domaine redirige vers le domaine par défaut dans l’environnement existant ou dans un autre environnement.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud pro (toutes versions)

## Problème

Le nouveau domaine est redirigé vers le domaine par défaut dans l’environnement actuel ou le domaine par défaut d’un autre environnement.

## Cause

Cela se produit lorsque les variables ne sont pas mises à jour après l’ajout d’un nouveau domaine ou que le mauvais service [!DNL Fastly] a été configuré dans l’environnement.

## Solution

1. Si le domaine est redirigé dans le même environnement, assurez-vous d’avoir configuré le [Variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=fr#modify-variables).
1. Si le domaine redirige vers un autre environnement, vérifiez si vous avez configuré le service [!DNL Fastly] approprié en exécutant la commande suivante : `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Vous pouvez trouver les informations d’identification de l’API [!DNL Fastly] en vous connectant à chaque environnement (évaluation/production) et en vérifiant le fichier `/mnt/shared/fastly_tokens.txt`. Pour plus d’informations, voir [configure [!DNL Fastly] services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr) dans le guide Commerce sur les infrastructures cloud.

Si les deux configurations ci-dessus sont correctes, envoyez un ticket d’assistance.

## Lecture connexe

* [Liste de contrôle pour la configuration d’un nouveau domaine](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html?lang=fr) dans notre base de connaissances d’assistance.
