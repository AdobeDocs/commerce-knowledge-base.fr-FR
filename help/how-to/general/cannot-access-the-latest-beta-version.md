---
title: Impossible d’accéder à la dernière version de Beta
description: Cet article fournit des solutions aux problèmes liés à l’utilisation des dernières versions de code Beta pour Adobe Commerce. Le code Beta n’est disponible que pour les partenaires d’Adobe officiels qui ont suivi le processus décrit dans [Programme Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Impossible d’accéder à la dernière version de Beta

Cet article fournit des solutions aux problèmes liés à l’utilisation des dernières versions de code Beta pour Adobe Commerce. Le code Beta n’est disponible que pour les partenaires d’Adobe officiels qui ont suivi le processus décrit dans [Programme Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problème

Cet article traite des problèmes suivants liés à l’accès au code d’accès anticipé :

* La version Beta d’Adobe Commerce n’est pas disponible au téléchargement sous **Mon compte** > **Téléchargements** sur [magento.com](https://account.magento.com/customer/account/login).
* Échec du téléchargement de la version Adobe Commerce d’accès anticipé à partir de [magento.com](https://account.magento.com/customer/account/login) à l’aide du compositeur.

## Cause

Voici les causes les plus courantes des problèmes :

* Vous recherchez le code d’accès anticipé au mauvais emplacement.
* Vous utilisez le MageID incorrect.
* Le développeur a besoin des clés d’accès à partir du MageID correct.
* Votre compte ne fait pas partie du programme Beta.

## Solution

### Emplacement du code d’accès anticipé

Pendant les périodes d’accès bêta, les modules de version ne sont disponibles que via le compositeur sur [repo.magento.com](https://repo.magento.com/). Les packages de version ne sont pas disponibles sur les portails GitHub et Adobe Commerce au cours de cette période, et nous les publierons à ces emplacements à la date de disponibilité générale. Pour plus d’informations sur l’utilisation du compositeur, cliquez [ici](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/composer).

### MageID que vous devez utiliser

Vous devez utiliser le MageID principal associé à votre compte Partner . Le programme Beta n&#39;est lié à aucun contact disposant d&#39;un accès partagé. L&#39;accès anticipé est uniquement accessible via le compositeur ou [repo.magento.com](https://repo.magento.com/) par le MageID associé à votre licence Partner.

#### Comment puis-je savoir si mon MageID est le principal ?

Pour savoir si votre MageID est principal, essayez les méthodes suivantes :

1. Connectez-vous à [magento.com](https://account.magento.com/customer/account/login) et accédez à l’onglet **My Product and Services** (Mon produit et services). Dans la sous-section Partenaires , vérifiez si les informations de licence du partenaire actif s’affichent :
   * Si les informations de licence de partenaire actif s’affichent, votre MageID est principal. La licence Partner est active si la valeur DATE DE FIN est une date ultérieure.
   * Si vous ne voyez pas les informations de licence de partenaire actif, alors votre MageID dispose uniquement d’un accès partagé. Pour savoir qui est le détenteur de l’ID principal, accédez à **Partagé avec moi** Notez le SHARENAME spécifié ici. Cliquez sur **Changer de compte** et sélectionnez la valeur que vous avez notée dans SHARENAME. Sur la page d’accueil, l’adresse électronique du détenteur de l’ID principal s’affiche.
1. Si, pour une raison quelconque, vous ne trouvez pas ces informations sur [magento.com](https://account.magento.com/customer/account/login), contactez votre Partner Manager.
1. Si aucun des éléments ci-dessus ne fonctionne, [contactez l&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### Le développeur ne dispose pas d’un accès correct aux clés

Si vous êtes le propriétaire principal de MageID et que vous devez donner accès à un développeur de votre équipe, procédez comme suit :

1. Connectez-vous au propriétaire MageID principal en [account.magento.com](https://account.magento.com/customer/account/login).
1. Sélectionnez l’onglet **Marketplace** , puis cliquez sur **Accéder aux clés**.
1. Sélectionnez **Créer une clé d’accès** et nommez-la.
1. Envoyez les clés à votre développeur.

### Ne fait pas partie du programme d&#39;accès anticipé

Notre programme d’accès Beta est disponible uniquement pour nos partenaires techniques et solutions afin qu’ils puissent évaluer notre code de pré-production. Pour être inclus dans le programme d’accès Beta, votre organisation doit disposer d’un compte partenaire Adobe actif en bonne état de fonctionnement et avoir signé le NDA Beta [ici](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Si vous pensez que vous remplissez ces critères et ne pouvez pas accéder au code bêta, contactez [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
