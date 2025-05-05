---
title: '"Modifications incompatibles à l’envers pour [!DNL GraphQL] &grave;placeOrder&grave; [!DNL API] dans Adobe Commerce 2.4.6-p8'''
promoted: true
description: Cet article fournit un correctif pour le problème connu Adobe Commerce version 2.4.6-p8 Cloud et On-premise où "placeOrder" [!DNL GraphQL API] ne renvoie pas de réponse d’erreur attendue, comme illustré dans les versions de correctif 2.4.6 précédentes. Cela peut entraîner une expérience de passage en caisse rompue pour les commerçants qui utilisent le storefront de PWA ou tout autre storefront basé sur [!DNL GraphQL API] pour leurs magasins.
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Modifications incompatibles à l’envers pour [!DNL GraphQL] `placeOrder` [!DNL API] dans Adobe Commerce 2.4.6-p8

Cet article fournit un correctif pour le problème cloud Adobe Commerce version 2.4.6-p8 connu et sur site où `placeOrder` [!DNL GraphQL API] ne renvoie pas de réponse d’erreur attendue, comme illustré dans les versions de correctif 2.4.6 précédentes. Cela peut entraîner une expérience de passage en caisse interrompue pour les commerçants utilisant [!DNL PWA] storefront ou tout autre storefront [!DNL GraphQL API] basé sur leurs magasins.

>[!NOTE]
>
>Contactez les services d’assistance si vous rencontrez des problèmes lors de l’application du correctif.

## Produits et versions concernés

* Adobe Commerce on Cloud 2.4.6-p8
* Adobe Commerce on-premise 2.4.6-p8

## Problème

Après la mise à niveau sur le correctif de sécurité uniquement Adobe Commerce 2.4.6-p8, [`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/) ne renvoie pas de réponse d’erreur attendue, comme illustré dans les versions précédentes de correctif 2.4.6. Cela peut entraîner une expérience de passage en caisse interrompue pour les commerçants utilisant [!DNL PWA] storefront ou tout autre storefront [!DNL GraphQL API] basé sur leurs magasins.

<u>Étape à reproduire</u> :

Exécutez la requête `placeOrder` [!DNL GraphQL] dans laquelle vous attendez une réponse d’erreur.

<u>Résultat attendu</u> :

Vous recevez une réponse d’erreur attendue.

<u>Résultat réel</u> :

Au lieu d’une réponse d’erreur attendue, vous recevez une réponse réussie, mais avec une nouvelle clé `errors` qui ressemble à ceci :

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## Solution pour Adobe Commerce sur le cloud et le logiciel Adobe Commerce sur site

Pour résoudre le problème, appliquez le correctif.
Pour le télécharger, cliquez sur le lien suivant :

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## Comment appliquer le correctif

Décompressez le fichier et reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) dans notre base de connaissances de support pour obtenir des instructions.

## Pour les marchands Adobe Commerce on Cloud uniquement : comment déterminer si des correctifs ont été appliqués

Étant donné qu’il n’est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif a bien été appliqué.

<u>Pour ce faire, procédez comme suit en utilisant le fichier d&#39;exemple `VULN-27015-2.4.7_COMPOSER.patch` **comme exemple</u>** :

1. [Installez le  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Exécutez la commande :<br>
   ![ac-13283-say-if-patch-apply-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Vous devriez voir une sortie similaire à celle-ci, où VULN-27015 renvoie l’état *Appliqué* :

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

