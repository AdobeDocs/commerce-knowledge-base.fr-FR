---
title: La mise à niveau vers B2B 1.5.2 échoue avec une erreur de syntaxe SQL en raison de l’absence de la fonction REGEXP_LIKE
description: Cet article fournit un correctif pour le problème où une erreur de syntaxe SQL se produit en raison de la fonction REGEXP_LIKE manquante lors de la tentative de mise à jour de la table company_structure.
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: 04e17dfdf143e233eb2767064c1328990c899eda
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# La mise à niveau vers B2B 1.5.2 échoue avec une erreur de syntaxe SQL en raison de l’absence de la fonction REGEXP_LIKE

>[!INFO]
>
>Si vous rencontrez un problème de performances lors de la mise à niveau du module `Magento_Company` après la mise à jour vers B2B 1.5.2, appliquez le [ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip) joint.
>
>Pour plus d’informations, consultez la section [Problème de performance dans la mise à niveau du module Magento_Company après la mise à jour de la version B2B 1.5.2](/help/troubleshooting/installation-and-upgrade/magento-company-module-upgrade-performance-issue.md) dans la base de connaissances Adobe Commerce.

Cet article fournit un correctif pour l’erreur de syntaxe SQL qui se produit en raison de la fonction `REGEXP_LIKE` manquante lors de la tentative de mise à jour de la table `company_structure`.

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-px + B2B 1.5.2 à l’aide de [!DNL MariaDB] 10.6
* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-px + B2B 1.5.2 à l’aide de [!DNL MariaDB] 10.6

## Problème

La mise à niveau vers la version 1.5.2 de B2B échoue avec une erreur de syntaxe SQL en raison de la fonction `REGEXP_LIKE` manquante lors de la tentative de mise à jour de la table `company_structure`.

<u>Conditions préalables</u> :

* MariaDB 10.6
* Adobe Commerce 2.4.6x ou 2.4.7x
* Version 1.5.0 ou 1.5.1 de B2B

<u>Procédure à suivre </u> :

1. Affectez une société à une société parent pour établir une hiérarchie de société. Pour plus d’informations, voir [Gérer la hiérarchie de l’entreprise](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy) dans le guide B2B d’Adobe Commerce.
1. Mettez à niveau B2B vers la version 1.5.2.

<u>Résultats attendus</u> :

La mise à niveau est terminée.

<u>Résultats réels</u> :

`bin/magento setup:upgrade` échoue avec l’erreur suivante :

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## Solution

Pour résoudre ce problème, procédez comme suit :

1. Mettez à jour le module B2B vers la version 1.5.2 :

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. Appliquez le correctif [ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip) joint. Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances d’assistance.
1. Exécutez `bin/magento setup:upgrade`.

### Application d’un correctif à l’aide de correctifs cloud

Pour Adobe Commerce sur les infrastructures cloud, procédez comme suit :

1. Mettez à jour la version du module `cloud-patches` vers la version 1.1.5 :

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. Validez et envoyez les modifications pour lancer le redéploiement. Pour obtenir des instructions, reportez-vous à la section [Application de correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) de notre guide Adobe Commerce sur Cloud .
