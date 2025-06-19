---
title: Impossible de modifier le moteur de recherche dans « app/etc/env.php »
description: Cet article fournit une solution au problème en raison duquel vous tentez de modifier le moteur de recherche dans l’administration Commerce, mais les champs sont verrouillés.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Impossible de modifier le moteur de recherche dans `app/etc/env.php`

Cet article fournit une solution au problème où vous essayez de supprimer la configuration du moteur de recherche du fichier `app/etc/env.php`, mais après redéploiement, la configuration revient au paramètre précédent ou est modifiée en [!DNL OpenSearch] par défaut.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Vous tentez de modifier le moteur de recherche dans l’administration Commerce, mais les champs sont verrouillés.

## Cause

La configuration du moteur de recherche est verrouillée dans le fichier `app/etc/env.php` ou le moteur de recherche est explicitement défini dans le fichier `.magento.env.yaml`.

## Solution

1. Vérifiez le fichier `.magento.env.yaml` sous l’étape de déploiement et vérifiez si la variable `SEARCH_CONFIGURATION` a été configurée. Exemple :

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. La variable `SEARCH_CONFIGURATION` est-elle présente ? S’il n’est pas présent, la configuration du moteur de recherche est verrouillée sur [!DNL OpenSearch] par défaut. Pour modifier la configuration, vous devez ajouter la variable au fichier `.magento.env.yaml` avec la valeur appropriée pour le moteur de recherche. Si la variable `SEARCH_CONFIGURATION` est présente et que vous souhaitez modifier le moteur, remplacez la valeur existante pour le moteur dans `.magento.env.yaml`. Valeurs possibles/connues : [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic] et [!DNL amasty_elastic_opensearch].
1. Redéployez l’instance.
1. Le champ Moteur de recherche dans l’Administration reste verrouillé, mais il doit être mis à jour avec la valeur que vous avez spécifiée.

## Lecture connexe

* Guide sur les [champs verrouillés (grisés) dans Commerce Admin](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26879) dans Commerce sur les infrastructures cloud.
