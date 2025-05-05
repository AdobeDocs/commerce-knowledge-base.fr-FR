---
title: Le tableau de bord et le classement des résultats de recherche "[!DNL Live Search]" sont incorrects.
description: Cet article fournit des informations de dépannage si les données du tableau de bord  [!DNL Live Search] sont incorrectes ou si le classement des résultats de la recherche ne correspond pas à ce que vous attendez.
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 4c1199c31f83d7c2aaf28e259d63473779bf2efe
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Le tableau de bord et le classement des résultats de recherche [!DNL Live Search] sont incorrects

Si vous constatez que les données affichées dans le tableau de bord [!DNL Live Search] sont incorrectes ou si le [classement des résultats de recherche](https://experienceleague.adobe.com/fr/docs/commerce-merchant-services/live-search/live-search-admin/category-merch#ranking-strategies) ne correspond pas à ce que vous attendez, reportez-vous aux sections suivantes pour des raisons possibles :

* Le champ `topLevelSku` du contexte du produit dans les événements `productView` est manquant. Cela entraîne des conversions vides et d’autres mesures inattendues.

* L’événement `add-to-cart` n’a pas le champ `productContext` défini et renseigné.

* Le type d’environnement est incorrect. Par exemple, si l’environnement est défini sur *[!UICONTROL Testing]* au lieu de *[!UICONTROL Production]*. Pour plus d’informations, voir [Contexte Storefront](https://github.com/adobe/commerce-events/blob/main/examples/events/example-contexts/mock-storefront-context.md) .

* Le contexte des résultats de recherche est absent de l’événement [search-product-click](https://github.com/adobe/commerce-events/blob/main/examples/events/search-product-click.md) .
