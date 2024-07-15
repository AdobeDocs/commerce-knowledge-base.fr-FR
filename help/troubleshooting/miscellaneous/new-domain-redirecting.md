---
title: Le nouveau domaine est redirigé vers le domaine par défaut.
description: Cet article fournit un correctif pour le problème de redirection du nouveau domaine vers le domaine par défaut dans l’environnement existant ou différent.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Le nouveau domaine est redirigé vers le domaine par défaut.

Cet article fournit un correctif pour le problème de redirection du nouveau domaine vers le domaine par défaut dans l’environnement existant ou différent.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud pro (toutes les versions)

## Problème

Le nouveau domaine redirige vers le domaine par défaut de l’environnement actuel ou vers le domaine par défaut d’un autre environnement.

## Cause

Cela se produit lorsque les variables ne sont pas mises à jour après l’ajout d’un nouveau domaine ou que le service [!DNL Fastly] incorrect a été configuré dans l’environnement.

## Solution

1. Si le domaine est redirigé dans le même environnement, assurez-vous d’avoir configuré les [variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Si le domaine redirige vers un autre environnement, vérifiez que vous avez configuré le service [!DNL Fastly] correct en exécutant la commande suivante : `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Vous pouvez trouver les informations d’identification de l’API [!DNL Fastly] en vous connectant à chaque environnement (intermédiaire/production) et en vérifiant le fichier `/mnt/shared/fastly_tokens.txt`. Pour plus d’informations, voir [configure [!DNL Fastly] services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans le guide Commerce on Cloud Infrastructure.

Si les deux configurations ci-dessus sont correctes, envoyez un ticket d’assistance.

## Lecture connexe

* [Liste de contrôle pour la configuration d’un nouveau domaine](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) dans notre base de connaissances d’assistance.
