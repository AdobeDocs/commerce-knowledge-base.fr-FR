---
title: Impossible d’ajouter un utilisateur au projet cloud Adobe Commerce
description: Cet article fournit une solution pour les cas où vous ne pouvez pas ajouter un utilisateur à un projet cloud Adobe Commerce.
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: af74d944553c34da2ac8343695bca49f971bc4e5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Impossible d’ajouter un utilisateur au projet cloud Adobe Commerce

Cet article fournit une solution pour lorsque vous essayez d’ajouter un utilisateur à un projet cloud, mais il échoue avec une erreur : *L’utilisateur XXX n’existe pas*.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Cet article fournit une solution pour les cas où vous ne pouvez pas ajouter un utilisateur à un projet cloud Adobe Commerce.

## Cause

Il s’agit du comportement attendu. Le compte de l’utilisateur doit d’abord être créé à l’adresse https://accounts.magento.cloud et lié à l’authentification unique de son Adobe pour qu’il soit ajouté en tant qu’utilisateur au projet.

## Solution

1. Demandez à l’utilisateur de se connecter à son compte à l’adresse https://accounts.magento.cloud (il doit avoir déjà ouvert un compte à l’adresse adobe.com sous cette adresse électronique. La création ou le fait d’avoir un compte sur https://account.adobe.com ne signifie pas automatiquement que l’utilisateur aurait un compte sur https://accounts.magento.cloud)
Remarque : Si l’utilisateur dispose d’un compte sur account.magento.com ou accounts.magento.cloud avant août 2022, il se peut qu’il ne dispose pas d’un compte sur adobe.com, sauf s’il l’a créé en août 2022 ou une version ultérieure. Si l’utilisateur dispose d’un compte d’Adobe et ne parvient pas à se connecter, [soumettez une demande d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) à l’adresse https://experienceleague.adobe.com/home#support et fournissez les détails (Raison du problème = Gestion des utilisateurs).
1. L’utilisateur doit ensuite se rendre sur https://accounts.magento.cloud.
1. Une fois qu’ils ont effectué cette opération, vous devriez être en mesure d’ajouter l’utilisateur au projet. Pour les étapes, reportez-vous à la section [Ajout d’utilisateurs et gestion de l’accès](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access) de notre guide Commerce on Cloud Infrastructure.

## Lecture connexe :

* [Gérez l’accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) dans notre guide Commerce on Cloud Infrastructure.
* [Impossible de se connecter au support Adobe Commerce ou au compte cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
