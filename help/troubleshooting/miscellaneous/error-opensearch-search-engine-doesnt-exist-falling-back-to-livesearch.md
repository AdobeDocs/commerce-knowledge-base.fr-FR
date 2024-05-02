---
title: Erreur [!DNL opensearch] le moteur de recherche n’existe pas. Revenir à [!DNL livesearch].
description: Cet article fournit une solution au problème où vous voyez l’erreur "Error- [!DNL opensearch] le moteur de recherche n’existe pas. Revenir à [!DNL livesearch].` dans Adobe Commerce sur l’infrastructure cloud.
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Erreur [!DNL opensearch] le moteur de recherche n’existe pas. Revenir à [!DNL livesearch].

Cet article fournit une solution au problème où l’erreur s’affiche : *Erreur : [!DNL opensearch] le moteur de recherche n’existe pas. Revenir à [!DNL livesearch].* dans Adobe Commerce sur l’infrastructure cloud où [!DNL Live Search] est utilisée.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions
* [!DNL Live Search] est installé et utilisé

## Problème

Le message suivant s’affiche dans les journaux (et peut être lu dans la section [!DNL New Relic]) :
*Erreur : [!DNL opensearch] le moteur de recherche n’existe pas. Revenir à [!DNL livesearch].*

## Solution

1. Modifiez la variable `.magento.env.yaml` fichier .
1. Recherchez les lignes suivantes :

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. Si vous ne disposez pas de ces lignes, ajoutez-les au `.magento.env.yaml` fichier .
1. Si ces lignes existent, **modification du moteur** de *[!DNL opensearch]* to *[!DNL livesearch]*.
1. Validez la modification, puis redéployez.

## Lecture connexe

* [Installer [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) dans notre guide de recherche en direct
