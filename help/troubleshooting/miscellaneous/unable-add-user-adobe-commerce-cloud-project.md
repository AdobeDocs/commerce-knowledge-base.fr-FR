---
title: Impossible d’ajouter un utilisateur au projet cloud Adobe Commerce
description: Cet article fournit une solution pour les cas où vous ne pouvez pas ajouter un utilisateur à un projet cloud Adobe Commerce.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Impossible d’ajouter un utilisateur au projet cloud Adobe Commerce

Cet article fournit une solution pour lorsque vous essayez d’ajouter un utilisateur à un projet cloud, mais qu’il échoue avec une erreur : *L’utilisateur XXX n’existe pas*.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Cet article fournit une solution pour les cas où vous ne pouvez pas ajouter un utilisateur à un projet cloud Adobe Commerce.

## Cause

Il s’agit du comportement attendu. Le compte de l’utilisateur doit d’abord être créé à l’adresse https://accounts.magento.cloud et lié à l’authentification unique de son Adobe pour qu’il soit ajouté en tant qu’utilisateur au projet.

## Solution

1. Demandez à l’utilisateur de se connecter à son compte à l’adresse https://accounts.magento.cloud (il doit avoir déjà ouvert un compte à l’adresse adobe.com sous cette adresse électronique. La création/la présence d’un compte à l’adresse https://account.adobe.com ne signifie pas automatiquement que l’utilisateur aurait un compte à l’adresse https://accounts.magento.cloud) Remarque : Si l’utilisateur a un compte sur account.magento.com ou comptes.magento.cloud avant août 2022, il se peut qu’il n’ait pas de compte avec/sur adobe.com à moins de l’avoir créé en août 2022 ou une version ultérieure. Si l’utilisateur dispose d’un compte d’Adobe et ne parvient pas à se connecter, envoyez un e-mail à [Grp-Magento-HelpCenterLoginIssues@adobe.com](mailto:Grp-Magento-HelpCenterLoginIssues@adobe.com) avec les détails.
1. L’utilisateur doit ensuite se rendre sur https://accounts.magento.cloud.
1. Une fois qu’ils ont effectué cette opération, vous devriez être en mesure d’ajouter l’utilisateur au projet. Pour connaître les étapes, voir [Ajout d’utilisateurs et gestion des accès](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) dans notre guide Commerce on Cloud Infrastructure.

## Lecture connexe :

* [Gestion de l’accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) dans notre guide Commerce on Cloud Infrastructure.
* [Impossible de se connecter au support Adobe Commerce ou au compte cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
