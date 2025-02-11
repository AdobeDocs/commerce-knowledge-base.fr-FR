---
title: Mise à jour de sécurité disponible pour Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Appliquez un correctif isolé pour corriger  [!DNL critical, important, and moderate vulnerabilities]  pour Adobe Commerce et Magento Open Source 2.4.7-bêta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 et les versions antérieures.
feature: Compliance, Security
role: Developer
source-git-commit: 45c6486dea10b37aa8114467bbd7be0c7f9f86f6
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Mise à jour de sécurité disponible pour Adobe Commerce - [!DNL APSB25-08]

Le 11 février 2025, Adobe a publié une mise à jour de sécurité régulièrement programmée pour Adobe Commerce et Magento Open Source. Cette mise à jour résout les vulnérabilités [[!DNL critical, important] et  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html). L’exploitation réussie de ces vulnérabilités peut entraîner l’exécution de code arbitraire, le contournement des fonctionnalités de sécurité et la réaffectation des privilèges. Vous trouverez plus d’informations dans le [Bulletin de la sécurité d’Adobe ([!DNL APSB25-08]) ici](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Pour que la correction des [!DNL CVE-2025-24434], répertoriée dans le bulletin de sécurité ci-dessus, puisse être appliquée aussi rapidement que possible, Adobe a également publié un correctif isolé qui résout les [!DNL CVE-2025-24434]. Cela permet aux commerçants d&#39;appliquer le correctif de manière isolée avec moins de risques de retard en raison de problèmes d&#39;intégration potentiels.**

**Veuillez appliquer les dernières mises à jour de sécurité dès que possible. Si vous ne le faites pas, vous serez vulnérable à ces problèmes de sécurité et l’Adobe disposera de moyens limités pour aider à résoudre le problème davantage.**

>[!NOTE]
>
>Contactez les services d’assistance si vous rencontrez des problèmes lors de l’application du correctif de sécurité/du correctif isolé.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud, Adobe Commerce sur site et Magento Open Source :

* 2.4.7-beta1 et versions antérieures
* 2.4.7-p3 et versions antérieures
* 2.4.6-p8 et versions antérieures
* 2.4.5-p10 et versions antérieures
* 2.4.4-p11 et versions antérieures

## Solution pour le logiciel Adobe Commerce on Cloud et le logiciel Adobe Commerce on-premise

Pour aider à résoudre la vulnérabilité des produits et versions affectés, vous devez appliquer le correctif isolé [!DNL CVE-2025-24434].

## Détails du correctif isolé

Utilisez le patch isolé ci-joint suivant :

[vuln-28982-composer-patch.zip](assets/vuln-28982-composer-patch.zip)

## Comment appliquer le patch isolé

Décompressez le fichier et consultez [Comment appliquer un correctif de compositeur fourni par Adobe ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) dans notre base de connaissances du support pour obtenir des instructions.

## Pour Adobe Commerce sur les commerçants Cloud uniquement : comment déterminer si les correctifs isolés ont été appliqués

Comme il n&#39;est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif isolé [!DNL CVE-2025-24434] a bien été appliqué.

>[!NOTE]
>
><u>Pour ce faire, procédez comme suit, en utilisant le fichier `VULN-27015-2.4.7_COMPOSER.patch` **à titre d’exemple**</u> :

1. [Installation de l’outil de correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
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

* [Bulletin de la sécurité des Adobes ([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [Dernières mises à jour de sécurité disponibles pour Adobe Commerce](https://helpx.adobe.com/security/products/magento.html)
