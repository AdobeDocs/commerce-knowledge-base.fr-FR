---
title: '[!DNL Live Search] tableau de bord et le classement des résultats de recherche sont incorrects'
description: Cet article fournit des informations de dépannage si les données du tableau de bord [!DNL Live Search] sont incorrectes ou si le classement des résultats de recherche n’est pas celui attendu.
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: d4aea1f1-c2c4-45e5-87c8-73069f7c9ffd
source-git-commit: 9bb839292a120a3dab5151d493f915619dbf5c06
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# [!DNL Live Search] tableau de bord et le classement des résultats de recherche sont incorrects

Si vous constatez que les données affichées dans le tableau de bord de la [!DNL Live Search] sont incorrectes ou si le classement [&#x200B; des résultats de la recherche &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) ne correspond pas à vos attentes, consultez les éléments suivants pour des raisons possibles :

* Le champ `topLevelSku` du contexte du produit dans les événements `productView` est manquant. Cela entraîne des conversions vides et d’autres mesures inattendues.

* Le champ `productContext` n’est pas défini et renseigné pour l’événement `add-to-cart`.

* Le type d’environnement est incorrect. Par exemple, si l’environnement est défini sur *[!UICONTROL Testing]* au lieu de *[!UICONTROL Production]*. Pour plus d’informations, consultez [Contexte Storefront](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md).

* Le contexte des résultats de recherche est absent de l’événement [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md).
