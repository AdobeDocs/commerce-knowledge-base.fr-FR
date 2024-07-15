---
title: "ACSD-47292 : les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL"
description: Appliquez le correctif ACSD-47292 pour résoudre le problème Adobe Commerce en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL même si l’option "Afficher les produits en rupture de stock" est définie sur Oui.
exl-id: 377dc62f-d1cd-4292-b25d-53c498b772a9
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# ACSD-47292 : les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL

Le correctif ACSD-47292 corrige le problème en raison duquel les produits en rupture de stock ne sont pas disponibles dans la réponse GraphQL même si [!UICONTROL Display Out-of-Stock Products] est défini sur *[!UICONTROL Yes]*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 est installé. L’ID de correctif est ACSD-47292. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les produits groupés en rupture de stock ne sont pas disponibles dans la réponse GraphQL même si [!UICONTROL Display Out-of-Stock Products] est défini sur *[!UICONTROL Yes]*.

<u>Étapes à reproduire</u> :

1. Accédez à l’administrateur Adobe Commerce > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** et définissez [!UICONTROL Display Out-of-Stock Products] sur *[!UICONTROL Yes]*.
1. Créez deux produits simples, s1 et s2.
1. Rendre s1 en rupture de stock et non visible individuellement et s2 en stock et non visible individuellement, et les affecter à une catégorie.
1. Créez un produit fourni avec au moins un produit d’option et affectez s1 et s2 à cette option (type d’entrée &quot;RadioButton&quot;).
1. Enregistrez le produit fourni et affectez-le à une catégorie.
1. Allez sur le storefront et ouvrez ce produit groupé. L’option d’usine s1 est grisée mais visible.
1. Envoyez une requête GraphQL :

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Résultats attendus</u> :

L’option de lot s1 est répertoriée dans la réponse GraphQL, car [!UICONTROL Display Out-of-Stock Products] est défini sur *[!UICONTROL Yes]* et elle est visible sur le storefront.

<u>Résultats réels</u> :

L’option de lot s1 n’est pas répertoriée dans la réponse GraphQL.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
