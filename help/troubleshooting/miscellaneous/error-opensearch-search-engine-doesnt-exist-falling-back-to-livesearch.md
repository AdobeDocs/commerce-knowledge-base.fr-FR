---
title: Le moteur de recherche Error [!DNL opensearch] n’existe pas. Revenir à [!DNL livesearch].
description: Cet article fournit une solution au problème où l’erreur "Error- [!DNL opensearch] search engine n’existe pas" s’affiche. Revenir à  [!DNL livesearch].&grave; dans Adobe Commerce sur l’infrastructure cloud.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Le moteur de recherche d’ erreur [!DNL opensearch] n’existe pas. Revenir à [!DNL livesearch].

Cet article fournit une solution au problème où l’erreur suivante s’affiche : *Erreur : [!DNL opensearch] le moteur de recherche n’existe pas. Revenir à [!DNL livesearch].* dans Adobe Commerce sur l’infrastructure cloud où [!DNL Live Search] est utilisé.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions
* [!DNL Live Search] est installé et en cours d’utilisation

## Problème

Le message suivant est affiché dans les journaux (et observable dans [!DNL New Relic]) :
*Erreur : le moteur de recherche [!DNL opensearch] n’existe pas. Revenir à [!DNL livesearch].*

## Solution

1. Modifiez le fichier `.magento.env.yaml`.
1. Recherchez les lignes suivantes :

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Si vous ne disposez pas de ces lignes, ajoutez-les au fichier `.magento.env.yaml`.
1. Si ces lignes existent, **modifiez le moteur** de *[!DNL opensearch]* à *[!DNL livesearch]*.
1. Validez la modification, puis redéployez.

## Lecture connexe

* [Installer [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) dans notre guide de recherche en direct
