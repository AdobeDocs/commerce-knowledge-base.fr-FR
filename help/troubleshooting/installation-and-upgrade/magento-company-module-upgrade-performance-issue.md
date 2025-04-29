---
title: Problème de performance lors de la mise à niveau du module Magento_Company après la mise à jour B2B 1.5.2
description: Cet article fournit un correctif pour le problème de performances dans la mise à niveau du module Magento_Company après la mise à jour B2B 1.5.2, en remédiant au temps de traitement excessivement long pour les jeux de données volumineux dans la table company_structure.
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Problème de performance lors de la mise à niveau du module Magento_Company après la mise à jour B2B 1.5.2

Cet article fournit un correctif pour le problème de performances dans la mise à niveau du module `Magento_Company` après la mise à jour de la version 1.5.2 de B2B, en résolvant le temps de traitement trop long pour les jeux de données volumineux (environ 100 000 enregistrements ou plus) dans le tableau `company_structure`.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-px + B2B 1.5.2
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-px + B2B 1.5.2
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.8 + B2B 1.5.2

## Problème

La mise à niveau du module `Magento_Company` après la mise à jour vers B2B 1.5.2 prend trop de temps lors du traitement d’un grand nombre d’enregistrements (~100 000+) dans la table `company_structure`.

<u>Conditions préalables</u> :

* ACSD-65540_B2B_1.5.2.patch doit être installé.
* Adobe Commerce 2.4.6 - 2.4.8
* Version 1.5.0, 1.5.1 ou 1.5.2 de B2B avec le correctif ACSD-65540 appliqué

<u>Procédure à suivre </u> :

1. Affectez une société à une société parent pour établir une hiérarchie de société. Pour plus d’informations, voir [Gérer la hiérarchie de l’entreprise](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) dans le guide B2B d’Adobe Commerce.
1. Mettez à niveau B2B vers la version 1.5.2.

<u>Résultats attendus</u> :

La mise à niveau est terminée.

<u>Résultats réels</u> :

La mise à niveau du module `Magento_Company` prend beaucoup de temps si la table `company_structure` contient de nombreux enregistrements.

## Solution

Pour résoudre ce problème, procédez comme suit :

1. Mettez à jour le module B2B vers la version 1.5.2 :

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Appliquez le [ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip).

1. Appliquez le [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) joint.
1. Exécutez `bin/magento setup:upgrade` après avoir appliqué le correctif.

### Application du correctif

Décompressez le fichier et consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) dans notre base de connaissances d’assistance pour obtenir des instructions.

### Application d’un correctif à l’aide de correctifs cloud

Pour Adobe Commerce sur les commerçants Cloud, procédez comme suit :

1. Mettez à jour la version du module cloud-patches vers la version 1.1.5 pour installer l’ACSD-65540_B2B_1.5.2.patch distribué sous la forme MCLOUD-13605.

   >[!NOTE]
   >
   >Pour vérifier si le correctif est déjà installé, exécutez :
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Ajoutez l’ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch au répertoire `m2-hotfixes` .
1. Validez et envoyez les modifications pour lancer le redéploiement et la `bin/magento setup:upgrade`. Pour obtenir des instructions, reportez-vous à la section [Application de correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) de notre guide Adobe Commerce sur Cloud .

## Lecture connexe

* [La mise à niveau vers B2B 1.5.2 échoue avec une erreur de syntaxe SQL en raison de l’absence de la fonction REGEXP_LIKE](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)
