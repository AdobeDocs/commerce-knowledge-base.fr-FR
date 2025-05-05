---
title: Mise à jour de sécurité disponible pour Adobe Commerce - [!DNL APSB24-61]
promoted: true
description: Appliquez un correctif isolé pour corriger  [!DNL CVE-2024-39397] pour Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10, et les instances de versions antérieures s’exécutant uniquement  [!DNL Apache].
feature: Compliance, Security
role: Developer
source-git-commit: 76ff7669a0a57925a176e08031e0789ced0a7f0e
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Mise à jour de sécurité disponible pour Adobe Commerce - [!DNL APSB24-61]

Le 13 août 2024, Adobe a publié une mise à jour de sécurité régulièrement planifiée pour le module externe Adobe Commerce, Magento Open Source et Adobe Commerce Webhooks.
Cette mise à jour corrige les vulnérabilités [[!DNL critical, important] et  [!DNL moderate]](https://helpx.adobe.com/fr/security/severity-ratings.html) . Une exploitation réussie peut entraîner l’exécution arbitraire du code, la lecture arbitraire du système de fichiers, le contournement des fonctionnalités de sécurité et la transmission des privilèges. Le bulletin d&#39;information est le suivant : [Bulletin de sécurité des Adobes ([!DNL APSB24-61])](https://helpx.adobe.com/fr/security/products/magento/apsb24-61.html).

>[!NOTE]
>
>**[!DNL CVE-2024-39397], répertorié dans le bulletin de sécurité ci-dessus, ne s&#39;applique que lors de l&#39;utilisation du serveur web [!DNL Apache].** Pour vous assurer que la correction de cette vulnérabilité peut être appliquée aussi rapidement que possible, Adobe a également publié un correctif isolé qui résout [!DNL CVE-2024-39397].

**Appliquez les dernières mises à jour de sécurité dès que possible. Si vous ne le faites pas, vous serez vulnérable à ces problèmes de sécurité, et l&#39;Adobe aura des moyens limités pour vous aider à y remédier.**

>[!NOTE]
>
>Contactez les services d’assistance si vous rencontrez des problèmes lors de l’application du correctif de sécurité/du correctif isolé.

## Produits et versions concernés

Adobe Commerce on Cloud, Adobe Commerce on-premise et Magento Open Source :

* 2.4.7-p1 et versions antérieures
* 2.4.6-p6 et versions antérieures
* 2.4.5-p8 et versions antérieures
* 2.4.4-p9 et versions antérieures

## Solution pour Adobe Commerce on Cloud, le logiciel Adobe Commerce sur site et le Magento Open Source

Pour résoudre la vulnérabilité des produits et versions concernés, vous devez appliquer le correctif isolé [!DNL CVE-2024-39397].

## Détails du correctif isolé

Utilisez le patch isolé suivant :

* [acsd-60551-composer-patch.zip](assets/acsd-60551-composer-patch.zip)

## Comment appliquer le correctif isolé

Décompressez le fichier et reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=fr) dans notre base de connaissances de support pour obtenir des instructions.

## Pour les marchands Adobe Commerce on Cloud uniquement : comment déterminer si les correctifs isolés ont été appliqués

Étant donné qu&#39;il n&#39;est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif isolé [!DNL CVE-2024-39397] a bien été appliqué.

<u>Pour ce faire, procédez comme suit en utilisant le fichier `VULN-27015-2.4.7_COMPOSER.patch` comme exemple</u> :

1. [Installation de l’outil de correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr).
1. Exécutez la commande :<br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Vous devriez voir une sortie similaire à celle-ci, où VULN-27015 renvoie l’état *Appliqué* :

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

* [Bulletin de sécurité Adobe ([!DNL APSB24-61])](https://helpx.adobe.com/fr/security/products/magento/apsb24-61.html)
