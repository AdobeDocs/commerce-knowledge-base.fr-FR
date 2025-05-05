---
title: Mise à jour de sécurité disponible pour Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Application d’un correctif isolé pour corriger  [!DNL critical, important, and moderate vulnerabilities] ’Adobe Commerce version 2.4.8-bêta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 et les versions antérieures.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: aba9548c0b5a06ffd0cddce630e53e5664bb9aac
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# Mise à jour de sécurité disponible pour Adobe Commerce - [!DNL APSB25-08]

Le 11 février 2025, Adobe a publié une mise à jour de sécurité régulièrement programmée pour Adobe Commerce et Magento Open Source. Cette mise à jour résout les vulnérabilités [[!DNL critical, important] et  [!DNL moderate]](https://helpx.adobe.com/fr/security/severity-ratings.html). L’exploitation réussie de ces vulnérabilités peut entraîner l’exécution de code arbitraire, le contournement des fonctionnalités de sécurité et la réaffectation des privilèges. Vous trouverez plus d’informations dans le [Bulletin de sécurité Adobe ([!DNL APSB25-08]) ici](https://helpx.adobe.com/fr/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Afin de garantir que la correction des [!DNL CVE-2025-24434], répertoriée dans le bulletin de sécurité ci-dessus, puisse être appliquée aussi rapidement que possible, Adobe a également publié un correctif isolé qui résout les [!DNL CVE-2025-24434]. Cela permet aux commerçants d&#39;appliquer le correctif de manière isolée avec moins de risques de retard en raison de problèmes d&#39;intégration potentiels.**

**Veuillez appliquer les dernières mises à jour de sécurité dès que possible. Si vous ne le faites pas, vous serez vulnérable à ces problèmes de sécurité et Adobe disposera de moyens limités pour résoudre le problème davantage.**

>[!NOTE]
>
>Contactez les services d’assistance si vous rencontrez des problèmes lors de l’application du correctif de sécurité/du correctif isolé.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud, Adobe Commerce sur site et Magento Open Source :

* 2.4.8-beta1 et versions antérieures
* 2.4.7-p3 et versions antérieures
* 2.4.6-p8 et versions antérieures
* 2.4.5-p10 et versions antérieures
* 2.4.4-p11 et versions antérieures

## Solution pour Adobe Commerce sur Cloud, Adobe Commerce sur site et les logiciels Magento Open Source

>[!NOTE]
>
>Ce problème est résolu par la [dernière mise à jour des correctifs cloud](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest). Toute tentative d’application du correctif isolé lorsque le correctif est déjà en place à partir de la mise à jour des correctifs cloud peut entraîner des échecs d’installation.

Pour aider à résoudre la vulnérabilité des produits et versions concernés, vous devez appliquer le correctif isolé [!DNL CVE-2025-24434], en fonction de votre version d’Adobe Commerce/Magento Open Source.

## Détails du correctif isolé

Utilisez les correctifs isolés ci-joints suivants, en fonction de votre version d’Adobe Commerce/Magento Open Source :

### Pour la version 2.4.8-beta1 :

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### Pour les versions 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3 :

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### Pour les versions 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8 :

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### Pour les versions 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10 :

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### Pour les versions 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11 :

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## Comment appliquer le patch isolé

Décompressez le fichier et consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=fr) dans notre base de connaissances d’assistance pour obtenir des instructions.

## Pour Adobe Commerce sur les commerçants Cloud uniquement : comment déterminer si les correctifs isolés ont été appliqués

Comme il n&#39;est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif isolé [!DNL CVE-2025-24434] a bien été appliqué.

>[!NOTE]
>
><u>Pour ce faire, procédez comme suit, en utilisant le fichier `VULN-27015-2.4.7_COMPOSER.patch` **à titre d’exemple**</u> :

1. [Installation de l’outil de correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr).
1. Exécutez la commande : <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Vous devriez voir une sortie similaire à celle-ci, où VULN-27015 renvoie le statut *Applied* :

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Mises à jour de sécurité

Mises à jour de sécurité disponibles pour Adobe Commerce :

* [Bulletin de sécurité Adobe ([!DNL APSB25-08])](https://helpx.adobe.com/fr/security/products/magento/apsb25-08.html)
* [Dernières mises à jour de sécurité disponibles pour Adobe Commerce](https://helpx.adobe.com/fr/security/products/magento.html)
