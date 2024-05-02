---
title: Réorganisation des branches cloud sur Adobe Commerce
description: Cet article décrit les étapes à suivre pour réorganiser les branches cloud sur Adobe Commerce si elles ne sont pas organisées selon la bonne hiérarchie. Si les branches ne sont pas organisées dans la bonne hiérarchie, vous ne pourrez pas effectuer de fusion vers la branche parente correcte ; elle sera dirigée vers la branche parente existante.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Réorganisation des branches cloud sur Adobe Commerce

Cet article décrit les étapes à suivre pour réorganiser les branches cloud sur Adobe Commerce si elles ne sont pas organisées selon la bonne hiérarchie. Si les branches ne sont pas organisées dans la bonne hiérarchie, vous ne pourrez pas effectuer de fusion vers la branche parente correcte ; elle sera dirigée vers la branche parente existante.

## Produits et versions concernés :

* Adobe Commerce sur l’infrastructure cloud, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Organisation des branches du cloud

L’organisation de hiérarchie correcte pour vos branches est la suivante :

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## Solution pour une organisation des branches de cloud incorrecte

Pour réorganiser les branches cloud :

1. Vous devez disposer de la variable [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) rôle.
1. Installation de Magento-cloud [!DNL CLI] (si vous ne l’avez pas fait).
1. Exécutez la commande suivante pour les branches à déplacer :
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Remarque : vous pouvez spécifier la branche parente lors de la création d’une nouvelle branche. Pour connaître les étapes, voir [Prise en main de la création de branches](https://devdocs.magento.com/cloud/env/environments-start.html#getstarted) dans notre documentation destinée aux développeurs.

Vous pouvez créer une branche d’environnement à l’aide de la fonction `branch <environment-name> <parent-environment-ID>` commande d’environnement magento-cloud.

La création et l’activation d’une nouvelle branche d’environnement peuvent prendre du temps.

## Lecture connexe

[Gestion des branches avec [!DNL CLI]](https://devdocs.magento.com/cloud/env/environments-start.html) dans notre documentation destinée aux développeurs.
