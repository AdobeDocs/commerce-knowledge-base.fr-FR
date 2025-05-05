---
title: Réorganisation des branches cloud sur Adobe Commerce
description: Cet article décrit les étapes à suivre pour réorganiser les branches cloud sur Adobe Commerce si elles ne sont pas organisées selon la bonne hiérarchie. Si les branches ne sont pas organisées dans la bonne hiérarchie, vous ne pourrez pas effectuer de fusion vers la branche parente correcte ; elle sera dirigée vers la branche parente existante.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

1. Vous devez avoir le rôle [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr) .
1. Installez le cloud magento [!DNL CLI] (si vous ne l’avez pas fait).
1. Exécutez la commande suivante pour les branches à déplacer :
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Remarque : vous pouvez spécifier la branche parente lors de la création d’une nouvelle branche. Pour les étapes, reportez-vous à la section [Prise en main de la création de branches](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/cli-branches) dans notre documentation destinée aux développeurs.

Vous pouvez créer une branche d’environnement à l’aide de la commande d’environnement magento-cloud `branch <environment-name> <parent-environment-ID>`.

La création et l’activation d’une nouvelle branche d’environnement peuvent prendre du temps.

## Lecture connexe

[Gérez les branches avec le  [!DNL CLI]](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/cli-branches) dans notre documentation destinée aux développeurs.
