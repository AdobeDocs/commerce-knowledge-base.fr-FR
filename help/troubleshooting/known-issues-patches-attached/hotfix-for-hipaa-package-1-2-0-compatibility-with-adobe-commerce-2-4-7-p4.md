---
title: Correctif du package de compatibilité Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0
description: Cet article fournit un correctif permettant d’ajouter la compatibilité du nouveau package 1.2.0 avec Adobe Commerce sur  [!DNL HIPAA] ’infrastructure cloud 2.4.7-p4
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Correctif du package de compatibilité Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0

Cet article fournit un correctif permettant d’ajouter la compatibilité du nouveau package **[!DNL HIPAA]1.2.0** avec Adobe Commerce sur l’infrastructure cloud 2.4.7-p4.

Le problème sera corrigé dans la version 2.4.7-p5.

## Versions et produits concernés

Adobe Commerce sur les infrastructures cloud 2.4.7-p4 et versions antérieures

## Conditions préalables

* Adobe a configuré votre compte Adobe Commerce pour accéder à l’extension **[!DNL HIPAA Ready]**. Voir [[!DNL HIPAA] Préparation sur Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) pour plus d’informations dans notre **Guide de prise en main d’Adobe Commerce**.
* Accédez à [repo.magento.com](https://repo.magento.com) pour installer l’extension. Pour la génération des clés et l’obtention des droits nécessaires, voir [Obtenir vos clés d’authentification](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) dans notre **Guide d’installation d’Adobe Commerce**.

## Problème

Le package [!DNL HIPAA] 1.1.0 n’est pas compatible avec la ligne de version 2.4.7x d’Adobe Commerce.

## Solution

Grâce à ce correctif, les commerçants qui exécutent Adobe Commerce sur Cloud Infrastructure 2.4.7-p4 pourront utiliser le package [!DNL HIPAA] 1.2.0.

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0 est compatible avec Adobe Commerce 2.4.7-p5 uniquement. Si vous souhaitez ajouter la compatibilité avec [!DNL HIPAA] 1.2.0 à Adobe Commerce 2.4.7-p4, installez le correctif fourni.<br><u>Si vous n’utilisez pas Adobe Commerce 2.4.7-p4, vous devez d’abord effectuer la mise à niveau vers Adobe Commerce 2.4.7-p4 pour utiliser ce correctif</u>.**

Pour résoudre le problème d’Adobe Commerce sur Cloud Infrastructure 2.4.7-p4, appliquez le correctif suivant :

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## Application du correctif

Décompressez le fichier et consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) dans notre base de connaissances d’assistance pour obtenir des instructions.

## Pour Adobe Commerce sur les commerçants Cloud uniquement : comment déterminer si le correctif a été appliqué

Comme il n’est pas possible de vérifier facilement si le problème a été corrigé, vous pouvez vérifier si le correctif a bien été appliqué.

>[!NOTE]
>
><u>Pour ce faire, procédez comme suit, en utilisant le fichier `VULN-27015-2.4.7_COMPOSER.patch` **à titre d’exemple**</u> :

1. [Installation de l’outil de correctifs de qualité](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Exécutez la commande : <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Vous devriez voir une sortie similaire à celle-ci, **<u>où l’exemple utilisé ici, VULN-27015</u>**, renvoie le statut *Appliqué* :

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
