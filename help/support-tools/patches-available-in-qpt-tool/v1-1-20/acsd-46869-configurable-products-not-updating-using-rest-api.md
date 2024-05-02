---
title: "ACSD-46869 : produits configurables ne se mettant pas à jour à l’aide de l’API REST au passage en caisse"
description: Le correctif ACSD-46869 corrige le problème en raison duquel les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20 est installé. L’ID de correctif est ACSD-46869. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869 : produits configurables ne se mettant pas à jour à l’aide de l’API REST au passage en caisse

Le correctif ACSD-46869 corrige le problème en raison duquel les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.20 est installée. L’ID de correctif est ACSD-46869. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 à 2.4.5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL QPT] landing page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits configurables ne sont pas mis à jour à l’aide de l’API REST lors du passage en caisse.

<u>Étapes à reproduire</u>:

1. Créez un produit configurable avec des attributs de couleur et de taille.
1. Sélectionner **[!UICONTROL Options]** et ajoutez le produit au panier.
1. Accédez à **[!UICONTROL Checkout]**, mettez à jour la taille plusieurs fois, à l’exception de la quantité, et vérifiez la requête et la réponse.
1. Vous obtenez la réponse suivante lorsque vous mettez à jour la taille.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Résultats attendus</u>:

La valeur est mise à jour en fonction des modifications.

<u>Résultats réels</u>:

`option_value` n’est pas mise à jour. Par conséquent, lorsque la commande est placée, elle a la valeur de l’ancienne taille.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tools] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide de l’outil Correctifs de qualité.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans [!DNL QPT], voir [Correctifs disponibles dans [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de l’outil Correctifs de qualité.
