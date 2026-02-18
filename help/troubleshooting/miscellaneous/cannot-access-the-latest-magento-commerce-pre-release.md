---
title: Impossible d’accéder à la dernière version préliminaire d’Adobe Commerce
description: Cet article fournit des solutions aux problèmes rencontrés lors de l’utilisation du code de version préliminaire le plus récent d’Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Impossible d’accéder à la dernière version préliminaire d’Adobe Commerce

Cet article fournit des solutions aux problèmes rencontrés lors de l’utilisation du code de version préliminaire le plus récent d’Adobe Commerce.

>[!NOTE]
>
>Si vous rencontrez des problèmes avec l’accès à Beta, reportez-vous à l’article [Impossible d’accéder à la dernière version de Beta](/help/how-to/general/cannot-access-the-latest-beta-version.md).

## Problème

Cet article traite des problèmes suivants liés à l’accès au code de version préliminaire :

* Impossible de localiser le code de version préliminaire.
* Échec du téléchargement de la version d’Adobe Commerce à accès anticipé à partir de [magento.com](https://account.magento.com/customer/account/login) à l’aide du compositeur.

## Cause

Il s’agit des causes les plus courantes de problèmes :

* Vous recherchez le code d’accès anticipé au mauvais emplacement.
* Le MageID utilisé n’est pas le bon lors de l’accès au code via le compositeur.
* Votre compte ne fait pas partie du programme de version préliminaire.

## Solution

### Emplacement du code d’accès anticipé

Au cours de la version préliminaire, les packages de version sont disponibles à deux emplacements :

1. Via Composer sur [magento.com](https://repo.magento.com/) en utilisant l’ID d’image principal pour le compte. Pour plus d’informations sur l’utilisation du compositeur, reportez-vous à la section [Installation d’Adobe Commerce à l’aide du compositeur](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/composer) de notre documentation destinée aux développeurs.
1. **Mon compte** > **Téléchargements** sur [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Les packages de version ne sont pas disponibles sur GitHub avant la date de disponibilité générale.

### MageID à utiliser

Vous devez utiliser l’ID d’image principal associé à votre compte Adobe Commerce ou Partner . Le programme de version préliminaire n’est lié à aucun contact ayant un accès partagé. L’accès anticipé n’est accessible que via Composer ou [repo.magento.com](https://repo.magento.com/) par le MageID associé à votre licence Adobe Commerce ou votre licence Partner .

#### Comment puis-je savoir si mon MageID est le principal ?

**Pour les commerçants**

Pour déterminer si votre MageID est principal, essayez les méthodes suivantes :

1. Connectez-vous à [magento.com](https://account.magento.com/customer/account/login) et accédez à l’onglet **Mes produits et services**. Vérifiez si les informations de licence Adobe Commerce s’affichent à cet endroit :
   * Si les informations de licence Adobe Commerce s’affichent, votre MageID est principal.
   * Si vous ne voyez pas les informations de licence Adobe Commerce, votre MageID dispose uniquement d’un accès partagé. Pour savoir qui est le titulaire de l’ID principal, accédez au **Partagé avec moi** Notez le NOM DE PARTAGE qui y est spécifié. Cliquez sur **Changer de compte** et sélectionnez la valeur que vous avez notée dans SHARENAME. Sur la page de bienvenue, vous verrez l’e-mail du titulaire de l’ID principal.
1. Si, pour une raison quelconque, vous ne trouvez pas ces informations sur [magento.com](https://account.magento.com/customer/account/login), contactez l’équipe chargée de votre compte Adobe.
1. Si aucun des problèmes ci-dessus ne fonctionne, [contactez l’assistance technique](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).

**Pour les partenaires**

Pour déterminer si votre MageID est principal, essayez les méthodes suivantes :

1. Connectez-vous à [magento.com](https://account.magento.com/customer/account/login) et accédez à l’onglet **Mes produits et services**. Dans la sous-section Partenaires , vérifiez si les informations de licence du partenaire actif s’affichent :
   * Si les informations de licence du partenaire actif s’affichent, votre ID d’image est principal. La licence Partenaire est active si la valeur END DATE correspond à une date ultérieure.
   * Si vous ne voyez pas les informations de licence du partenaire actif, votre MageID dispose uniquement d’un accès partagé. Pour savoir qui est le titulaire de l’ID principal, accédez au **Partagé avec moi** Notez le NOM DE PARTAGE qui y est spécifié. Cliquez sur **Changer de compte** et sélectionnez la valeur que vous avez notée dans SHARENAME. Sur la page de bienvenue, vous verrez l’e-mail du titulaire de l’ID principal.
1. Si, pour une raison quelconque, vous ne trouvez pas ces informations sur [magento.com](https://account.magento.com/customer/account/login), veuillez contacter votre responsable partenaire.
1. [&#x200B; Si aucun des problèmes ciсdessus ne fonctionne, contactez l’assistance &#x200B;](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).

### Ne fait pas partie du programme de version préliminaire

Pour être incluse dans le programme d’accès en version préliminaire, votre entreprise doit disposer d’un compte Adobe Commerce ou Partner actif et en règle. Si vous pensez répondre à ces critères et ne pas pouvoir accéder au code de version préliminaire, contactez [l’assistance technique](https://experienceleague.adobe.com/fr/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide) avec votre MageID.
