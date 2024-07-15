---
title: 'MDVA-37913 : les liens de téléchargement de produits disparaissent après la mise à jour des attributs d’extension via l’API'
description: Le correctif MDVA-37913 pour résout le problème en raison duquel les liens de produits téléchargeables disparaissent après la mise à jour des attributs d’extension via l’API. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 est installé. L’ID de correctif est MDVA-37913. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913 : les liens de téléchargement de produits disparaissent après la mise à jour des attributs d’extension via l’API

Le correctif MDVA-37913 pour résout le problème en raison duquel les liens de produits téléchargeables disparaissent après la mise à jour des attributs d’extension via l’API. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24 est installé. L’ID de correctif est MDVA-37913. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.


## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**
Adobe Commerce sur l’infrastructure cloud 2.3.6

**Compatible avec les versions d’Adobe Commerce :**
Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.


## Problème

Les liens de produit téléchargeables disparaissent après la mise à jour des attributs d’extension via l’API.

<u>Conditions préalables</u> :
Produit téléchargeable avec liens de téléchargement.

<u>Étapes à reproduire</u> :

1. Mettez à jour les attributs d’extension à l’aide d’une requête comme celle-ci :

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>Résultats attendus</u>:<br>
Le produit est mis à jour, tous les liens de téléchargement ne sont pas supprimés.

<u>Résultats réels</u>:<br>
Mise à jour du produit, mais tous les liens de téléchargement ont été supprimés.


## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de qualité dans notre base de connaissances de support, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) de notre base de connaissances de support.
