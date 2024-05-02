---
title: Impossible de modifier le moteur de recherche dans "app/etc/env.php"
description: Cet article fournit une solution au problème qui se produit lorsque vous essayez de modifier le moteur de recherche dans l’administrateur Commerce, mais que les champs sont verrouillés.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Impossible de modifier le moteur de recherche dans `app/etc/env.php`

Cet article fournit une solution au problème où vous essayez de supprimer la configuration du moteur de recherche de la `app/etc/env.php` mais après le redéploiement, la configuration revient au paramètre précédent ou est remplacée par [!DNL OpenSearch] par défaut.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Vous essayez de modifier le moteur de recherche dans l’administrateur Commerce, mais les champs sont verrouillés.

## Cause

La configuration du moteur de recherche est verrouillée dans la variable `app/etc/env.php` ou le moteur de recherche est explicitement défini dans la variable `.magento.env.yaml` fichier .

## Solution

1. Vérifiez les `.magento.env.yaml` sous l’étape de déploiement et vérifiez si la variable `SEARCH_CONFIGURATION` a été configurée. Exemple :

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. est la variable  `SEARCH_CONFIGURATION` présente ? Si elle n’est pas présente, la configuration du moteur de recherche est verrouillée sur [!DNL OpenSearch] par défaut. Pour modifier la configuration, vous devez ajouter la variable au `.magento.env.yaml` avec la valeur appropriée pour le moteur de recherche. Si la variable `SEARCH_CONFIGURATION` est présente et vous souhaitez modifier le moteur, remplacer la valeur existante du moteur dans `.magento.env.yaml`. Valeurs possibles/connues : [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic], et [!DNL amasty_elastic_opensearch].
1. Redéployez l’instance.
1. Le champ du moteur de recherche dans l’Admin reste verrouillé, mais il doit être mis à jour avec la valeur que vous avez spécifiée.

## Lecture connexe

* [Champs verrouillés dans l’administrateur Commerce](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) dans le guide d’infrastructure de Commerce on Cloud.
