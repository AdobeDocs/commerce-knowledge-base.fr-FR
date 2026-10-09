---
title: Problèmes de déploiement liés aux autorisations de compte et aux clés d’accès
description: Cet article fournit une solution aux problèmes de déploiement d’Adobe Commerce sur l’infrastructure cloud causés par un conflit de propriété de la clé d’accès.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%
---
# Problèmes de déploiement liés aux autorisations de compte et aux clés d’accès

Cet article fournit une solution aux problèmes de déploiement d’Adobe Commerce sur l’infrastructure cloud causés par un conflit de propriété de la clé d’accès.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les versions prises en charge

## Problème

<u>Conditions préalables</u> :

La licence Cloud est associée au contact A (adresse e-mail : *<u></u>*)

<u>Procédure à suivre </u> :

1. Contact A créé les clés d&#39;accès Adobe Commerce sur son compte (Clé X) et les a installées sur le Cloud.
1. Le contact B (adresse e-mail : *<u></u>*) a acheté une extension à l’aide de son compte et a créé les clés d’accès pour installer l’extension (clé Y).
1. Le contact A a ensuite quitté l&#39;entreprise, et la licence (propriété) a ensuite été transférée au contact B.
1. L’intégrateur système tente d’installer l’extension dans l’environnement cloud à l’aide de la clé X.

<u>Résultat attendu </u> :

Extension installée avec succès.

<u>Résultat réel</u> :

L’extension n’est pas installée, car le déploiement échoue.

## Cause

Les deux clés sont affectées au rôle de contact, ce qui entraîne un conflit.

## Solution

Si un déploiement a échoué après une modification apportée au contact de Principal sur le compte (le compte d’origine et le nouveau compte disposant chacun de leurs propres clés d’accès) et si les clés ont été transférées du compte d’origine vers le nouveau compte, vous devez désactiver les clés du compte d’origine. Dans l’exemple ci-dessus, la clé X doit être désactivée.

### Comment désactiver la clé d’accès

Si vous n&#39;avez pas accès au compte [&#128279;](https://marketplace.magento.com/) associé à l&#39;ancienne clé, [contactez l&#39;assistance Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) pour que la clé soit désactivée.

Si vous avez accès au compte Marketplace associé à l’ancienne clé, procédez comme suit pour désactiver la clé :

1. Connectez-vous à [&#128279;](https://marketplace.magento.com/) à l&#39;aide des informations d&#39;identification de l&#39;ancien compte.
1. Cliquez sur le nom du compte dans le coin supérieur droit de la page et sélectionnez **Mon profil**.
1. Cliquez sur **Clés d’accès** dans l’onglet Marketplace.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Cliquez sur **Désactiver** en regard de la clé d’accès.

## Lecture connexe

* [Obtenez vos clés d’authentification](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) dans notre documentation destinée aux développeurs.
