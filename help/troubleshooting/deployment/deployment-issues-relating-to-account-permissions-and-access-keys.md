---
title: Problèmes de déploiement liés aux autorisations de compte et aux clés d’accès
description: Cet article fournit une solution aux problèmes liés au déploiement d’Adobe Commerce sur l’infrastructure cloud causés par un conflit de propriété de clé d’accès.
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Problèmes de déploiement liés aux autorisations de compte et aux clés d’accès

Cet article fournit une solution aux problèmes liés au déploiement d’Adobe Commerce sur l’infrastructure cloud causés par un conflit de propriété de clé d’accès.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions prises en charge

## Problème

<u>Conditions préalables</u> :

La licence Cloud est associée au contact A (adresse email : *<u>first@e.mail</u>*)

<u>Étapes à reproduire</u> :

1. Contactez les clés d’accès Adobe Commerce créées sur leur compte (clé X) et installées sur le cloud.
1. Le contact B (adresse email : *<u>second@e.mail</u>*) a acheté une extension à l’aide de son compte et a créé les clés d’accès pour installer l’extension (clé Y).
1. Contact A a ensuite quitté la société, et la licence (propriété) a été transférée au contact B.
1. L’intégrateur système tente d’installer l’extension sur l’environnement cloud à l’aide de la clé X.

<u>Résultat attendu</u> :

L’extension a été installée avec succès.

<u>Résultat réel</u> :

L’extension n’est pas installée, car le déploiement échoue.

## Cause

Les deux clés sont affectées au rôle de contact, ce qui provoque un conflit.

## Solution

Si un déploiement a échoué après qu’une modification a été apportée au contact de Principal sur le compte (avec le compte d’origine et le nouveau compte ayant chacun leur propre clé d’accès), et que les clés ont été transférées du compte d’origine au nouveau compte, vous devez désactiver les clés du compte d’origine. Dans l’exemple ci-dessus, la clé X doit être désactivée.

### Comment désactiver la clé d’accès

Si vous n&#39;avez pas accès au compte [Commerce Marketplace](https://marketplace.magento.com/) associé à l&#39;ancienne clé, [contactez le support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour que la clé soit désactivée.

Si vous avez accès au compte Marketplace associé à l’ancienne clé, procédez comme suit pour la désactiver :

1. Connectez-vous au [Commerce Marketplace](https://marketplace.magento.com/) à l’aide des informations d’identification de l’ancien compte.
1. Cliquez sur le nom du compte en haut à droite de la page et sélectionnez **Mon profil**.
1. Cliquez sur **Accéder aux clés** dans l’onglet Marketplace.

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. Cliquez sur **Désactiver** en regard de la clé d’accès.

## Lecture connexe

* [Obtenez vos clés d’authentification](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) dans notre documentation destinée aux développeurs.
