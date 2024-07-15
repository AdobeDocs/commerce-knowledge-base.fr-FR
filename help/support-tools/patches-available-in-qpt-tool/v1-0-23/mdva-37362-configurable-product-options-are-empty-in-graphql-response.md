---
title: "MDVA-37362 : les options de produit configurables sont vides dans la réponse GraphQL"
description: Le correctif MDVA-37362 résout le problème en raison duquel les valeurs d’option de produit configurables et les valeurs d’attribut de variante sont vides dans la réponse GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.
exl-id: a56db5e3-0841-4764-b430-d5775ebd1fe6
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-37362 : les options de produit configurables sont vides dans la réponse GraphQL.

Le correctif MDVA-37362 résout le problème en raison duquel les valeurs d’option de produit configurables et les valeurs d’attribut de variante sont vides dans la réponse GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.23 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce version 2.4.3.

## Produits et versions concernés

* Le correctif a été conçu pour Adobe Commerce sur l’infrastructure cloud 2.4.2.
* Le correctif est également compatible avec Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.4 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire :</u>

1. Créez une nouvelle source et un nouveau stock affecté à cette nouvelle source.
1. **Magasins** > *Paramètres* > **Configuration** > **Catalogue** > **Inventaire** > *Options Stock de produit* > Gérer le stock : *OUI*.
1. Créez un produit configurable et affectez la quantité du produit au nouveau stock créé à l’étape 1.
1. Réindexation.
1. Effectuez une requête GraphQL.
1. Requête :

```java
{
  products(filter: { sku: { eq: "test-config-product" } }) {
    items {
      id
      attribute_set_id
      name
      sku
      __typename
      price_range{
        minimum_price{
          regular_price{
            value
            currency
          }
        }
      }
      categories {
        id
      }
      ... on ConfigurableProduct {
        configurable_options {
          id
          attribute_id_v2
          label
          position
          use_default
          attribute_code
          values {
            value_index
            label
          }
          product_id
        }
        variants {
          product {
            id
            name
            sku
            attribute_set_id
            ... on PhysicalProductInterface {
              weight
            }
            price_range{
              minimum_price{
                regular_price{
                  value
                  currency
                }
              }
            }
          }
          attributes {
            uid
            label
            code
            value_index
          }
        }
      }
    }
  }
}
```

<u>Résultats attendus :</u>

Les valeurs et attributs d’option doivent être présents dans la réponse.

<u>Résultats réels :</u>

```java
{
  "data": {
    "products": {
      "items": [
        {
          "id": 2048,
          "attribute_set_id": 4,
          "name": "Test Configurable Product",
          "sku": "test-config-product",
          "__typename": "ConfigurableProduct",
          "price_range": {
            "minimum_price": {
              "regular_price": {
                "value": 100,
                "currency": "USD"
              }
            }
          },
          "categories": [
            {
              "id": 3
            }
          ],
          "configurable_options": [
            {
              "id": 296,
              "attribute_id_v2": 93,
              "label": "Color",
              "position": 1,
              "use_default": false,
              "attribute_code": "color",
              "values": [],
              "product_id": 2048
            },
            {
              "id": 297,
              "attribute_id_v2": 186,
              "label": "Size",
              "position": 0,
              "use_default": false,
              "attribute_code": "size",
              "values": [],
              "product_id": 2048
            }
          ],
          "variants": [
            {
              "product": {
                "id": 2051,
                "name": "Test Configurable Product-M-Black",
                "sku": "test-config-product-M-Black",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            },
            {
              "product": {
                "id": 2052,
                "name": "Test Configurable Product-M-Blue",
                "sku": "test-config-product-M-Blue",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            },
            {
              "product": {
                "id": 2049,
                "name": "Test Configurable Product-S-Black",
                "sku": "test-config-product-S-Black",
                "attribute_set_id": 4,
                "weight": null,
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "value": 100,
                      "currency": "USD"
                    }
                  }
                }
              },
              "attributes": []
            }
          ]
        }
      ]
    }
  }
}
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
