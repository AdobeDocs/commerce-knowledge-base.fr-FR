---
title: Mise à jour de sécurité disponible pour Adobe Commerce - [!DNL APSB25-50]
promoted: true
description: Application d’un correctif isolé pour corriger  [!DNL critical and important vulnerabilities] ’Adobe Commerce 2.4.8, 2.4.7-p5, 2.4.6-p10, 2.4.5-p12, 2.4.4-p13 et les versions antérieures.
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 1%

---

# Mise à jour de sécurité disponible pour Adobe Commerce - [!DNL APSB25-50]

Le 10 juin 2025, Adobe a publié une mise à jour de sécurité régulièrement programmée pour Adobe Commerce et Magento Open Source. Cette mise à jour résout les vulnérabilités [[!DNL critical] et [!DNL important]](https://helpx.adobe.com/fr/security/severity-ratings.html). L’exploitation réussie de ces vulnérabilités peut entraîner le contournement des fonctionnalités de sécurité, la réaffectation des privilèges et l’exécution arbitraire du code.

Vous trouverez plus d’informations dans le [Bulletin de sécurité Adobe ([!DNL APSB25-50]) ici](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

>[!NOTE]
>
>**Afin de garantir que la correction des [!DNL CVE-2025-47110] répertoriées dans le bulletin de sécurité ci-dessus puisse être appliquée aussi rapidement que possible, Adobe a également publié un correctif isolé qui résout les [!DNL CVE-2025-47110]. Cela permet aux commerçants d&#39;appliquer le correctif de manière isolée avec moins de risques de retard en raison de problèmes d&#39;intégration potentiels.**

**Veuillez appliquer les dernières mises à jour de sécurité dès que possible. Si vous ne le faites pas, vous serez vulnérable à ces problèmes de sécurité et Adobe disposera de moyens limités pour résoudre le problème davantage.**

Vous pouvez en savoir plus sur [notre processus de déploiement de correctifs isolés ici.](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>Pour les clients Adobe Commerce on Managed Services, votre ingénieur du succès client peut fournir des conseils supplémentaires sur l’application du correctif.

>[!NOTE]
>
>Contactez les services d’assistance si vous rencontrez des problèmes lors de l’application du correctif de sécurité/du correctif isolé.

Pour rappel, vous trouverez [les dernières mises à jour de sécurité disponibles pour Adobe Commerce ici.](https://helpx.adobe.com/fr/security/products/magento.html)

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) :

* 2.4.8
* 2.4.7-p5 et versions antérieures
* 2.4.6-p10 et versions antérieures
* 2.4.5-p12 et versions antérieures
* 2.4.4-p13 et versions antérieures

## Événements

### I. CVE-2025-47110 : XSS stocké via l’injection de modèle côté serveur dans Adobe Commerce 2.4.7-p4

<u>Produits et versions concernés </u> :

Adobe Commerce (toutes les méthodes de déploiement) :

* 2.4.8
* 2.4.7-p5 et versions antérieures
* 2.4.6-p10 et versions antérieures
* 2.4.5-p12 et versions antérieures
* 2.4.4-p13 et versions antérieures

<u>Solution</u> :

Pour les versions d’Adobe Commerce :

* 2.4.8
* 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4, 2.4.7-p5
* 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p10
* 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11, 2.4.5-p12
* 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12, 2.4.4-p13

**Appliquez le correctif isolé suivant ou effectuez une mise à niveau vers le dernier correctif de sécurité.**

* **[VULN-31609_2.4.X.patch](assets/VULN-31609_2.4.X_patch.zip)**

### II. VULN-31547 : XSS reflété dans marketplace.magento.com + problème ATO en un clic affectant les instances IMS

<u>Produits et versions concernés </u> :

Adobe Commerce (toutes les méthodes de déploiement) :

* 2.4.8

<u>Solution</u> :

Pour les versions d’Adobe Commerce :

* 2.4.8

**Appliquez le correctif isolé suivant ou effectuez une mise à niveau vers le dernier correctif de sécurité.**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## Comment appliquer le patch isolé

Décompressez le fichier et consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=fr) dans notre base de connaissances d’assistance pour obtenir des instructions.

## Pour Adobe Commerce sur les commerçants Cloud uniquement : comment déterminer si les correctifs isolés ont été appliqués

Comme il n’est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif isolé [!DNL CVE-2025-47110] a bien été appliqué.

>[!NOTE]
>
><u>Pour ce faire, procédez comme suit, en utilisant le fichier `VULN-27015-2.4.7_COMPOSER.patch` **à titre d’EXEMPLE**</u> :

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

* [Bulletin de sécurité Adobe ([!DNL APSB25-50])](https://helpx.adobe.com/security/products/magento/apsb25-50.html)
* [Dernières mises à jour de sécurité disponibles pour Adobe Commerce](https://helpx.adobe.com/fr/security/products/magento.html)
