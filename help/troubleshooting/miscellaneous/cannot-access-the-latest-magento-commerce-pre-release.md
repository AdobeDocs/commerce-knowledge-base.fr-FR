---
title: Impossible d’accéder à la dernière version préliminaire d’Adobe Commerce
description: Cet article fournit des solutions pour les problèmes liés à l’utilisation du code de version préliminaire le plus récent d’Adobe Commerce.
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Impossible d’accéder à la dernière version préliminaire d’Adobe Commerce

Cet article fournit des solutions pour les problèmes liés à l’utilisation du code de version préliminaire le plus récent d’Adobe Commerce.

>[!NOTE]
>
>Si vous rencontrez des problèmes d’accès à Beta, reportez-vous à l’article [Impossible d’accéder à la dernière version de Beta](/help/how-to/general/cannot-access-the-latest-beta-version.md) .

## Problème

Cet article traite des problèmes suivants liés à l’accès au code de version préliminaire :

* Vous ne pouvez pas localiser le code de version préliminaire.
* Échec du téléchargement de la version Adobe Commerce d’accès anticipé à partir de [magento.com](https://account.magento.com/customer/account/login) à l’aide du compositeur.

## Cause

Voici les causes les plus courantes des problèmes :

* Vous recherchez le code d’accès anticipé au mauvais emplacement.
* Vous utilisez un MageID incorrect lors de l’accès au code via le compositeur.
* Votre compte ne fait pas partie du programme de pré-version.

## Solution

### Emplacement du code d’accès anticipé

Lors de la version préliminaire, les modules de version sont disponibles à deux emplacements :

1. Par le biais du compositeur sur [magento.com](https://repo.magento.com/) à l’aide de l’ID principal Mage du compte. Pour plus d’informations sur l’utilisation du compositeur, reportez-vous à la section [Installation d’Adobe Commerce à l’aide du compositeur](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer) de notre documentation destinée aux développeurs.
1. **Mon compte** > **Téléchargements** sur [account.magento.com](https://account.magento.com/customer/account/login).

>[!NOTE]
>
>Les packages de version ne sont pas disponibles sur GitHub avant la date de disponibilité générale.

### MageID que vous devez utiliser

Vous devez utiliser le MageID principal associé à votre compte Adobe Commerce ou Partner. Le programme Préversion n&#39;est lié à aucun contact disposant d&#39;un accès partagé. L&#39;accès anticipé est uniquement accessible via le compositeur ou [repo.magento.com](https://repo.magento.com/) par le MageID associé à votre licence Adobe Commerce ou Partner.

#### Comment puis-je savoir si mon MageID est l’ID principal ?

**Pour les commerçants**

Pour savoir si votre MageID est principal, essayez les méthodes suivantes :

1. Connectez-vous à [magento.com](https://account.magento.com/customer/account/login) et accédez à l’onglet **My Product and Services** (Mon produit et services). Vérifiez si les informations de licence Adobe Commerce s’y trouvent :
   * Si les informations de licence Adobe Commerce s’affichent, votre MageID est principal.
   * Si vous ne voyez pas les informations de licence Adobe Commerce, alors votre MageID dispose uniquement d’un accès partagé. Pour savoir qui est le détenteur de l’ID principal, accédez à **Partagé avec moi** Notez le SHARENAME spécifié ici. Cliquez sur **Changer de compte** et sélectionnez la valeur que vous avez notée dans SHARENAME. Sur la page d’accueil, l’adresse électronique du détenteur de l’ID principal s’affiche.
1. Si, pour une raison quelconque, vous ne trouvez pas ces informations sur [magento.com](https://account.magento.com/customer/account/login), contactez votre équipe de compte d’Adobe.
1. Si aucun des éléments ci-dessus ne fonctionne, [contactez l&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

**Pour les partenaires**

Pour savoir si votre MageID est principal, essayez les méthodes suivantes :

1. Connectez-vous à [magento.com](https://account.magento.com/customer/account/login) et accédez à l’onglet **My Product and Services** (Mon produit et services). Dans la sous-section Partenaires , vérifiez si les informations de licence du partenaire actif s’affichent :
   * Si les informations de licence de partenaire actif s’affichent, votre MageID est principal. La licence Partner est active si la valeur DATE DE FIN est une date ultérieure.
   * Si vous ne voyez pas les informations de licence de partenaire actif, alors votre MageID dispose uniquement d’un accès partagé. Pour savoir qui est le détenteur de l’ID principal, accédez à **Partagé avec moi** Notez le SHARENAME spécifié ici. Cliquez sur **Changer de compte** et sélectionnez la valeur que vous avez notée dans SHARENAME. Sur la page d’accueil, l’adresse électronique du détenteur de l’ID principal s’affiche.
1. Si, pour une raison quelconque, vous ne trouvez pas ces informations sur [magento.com](https://account.magento.com/customer/account/login), contactez votre Partner Manager.
1. Si aucun des éléments ci-dessus ne fonctionne, veuillez contacter l&#39;[с assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### Ne fait pas partie du programme de préversion

Pour être inclus dans le programme d’accès anticipé, votre entreprise doit disposer d’un compte Adobe Commerce ou Partner actif en bonne et due forme. Si vous pensez que vous répondez à ces critères et ne pouvez pas accéder au code de version préliminaire, [ contactez le support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) avec votre MageID.
