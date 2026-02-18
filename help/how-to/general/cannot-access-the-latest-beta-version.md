---
title: Impossible d’accéder à la dernière version de Beta
description: Cet article fournit des solutions aux problèmes rencontrés lors de l’utilisation des dernières versions Beta du code pour Adobe Commerce. Le code Beta est uniquement disponible pour les partenaires Adobe officiels qui ont suivi le processus décrit dans [Programme Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Impossible d’accéder à la dernière version de Beta

Cet article fournit des solutions aux problèmes rencontrés lors de l’utilisation des dernières versions Beta du code pour Adobe Commerce. Le code Beta n’est disponible que pour les partenaires Adobe officiels qui ont suivi le processus décrit dans [Programme Adobe Commerce Beta](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## Problème

Cet article couvre les problèmes suivants liés à l’accès au code d’accès anticipé :

* La version d’Adobe Commerce Beta ne peut pas être téléchargée sous **Mon compte** > **Téléchargements** sur [magento.com](https://account.magento.com/customer/account/login).
* Échec du téléchargement de la version d’Adobe Commerce à accès anticipé à partir de [magento.com](https://account.magento.com/customer/account/login) à l’aide du compositeur.

## Cause

Il s’agit des causes les plus courantes de problèmes :

* Vous recherchez le code d’accès anticipé au mauvais emplacement.
* Vous n’utilisez pas le bon MageID.
* Le développeur a besoin de clés d’accès provenant de l’ID d’image correct.
* Votre compte ne fait pas partie du programme Beta.

## Solution

### Emplacement du code d’accès anticipé

Pendant les périodes d’accès à la version bêta, les packages de version ne sont disponibles que via le compositeur sur [repo.magento.com](https://repo.magento.com/). Les packages de version ne sont pas disponibles sur les portails GitHub et Adobe Commerce pendant cette période. Nous les publierons sur ces emplacements à la date de disponibilité générale. Pour plus d&#39;informations sur l&#39;utilisation du compositeur, cliquez [ici](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer).

### MageID à utiliser

Vous devez utiliser l’ID d’image principal associé à votre compte partenaire. Le programme Beta n&#39;est lié à aucun contact ayant un accès partagé. Un accès anticipé n&#39;est accessible que via Composer ou [repo.magento.com](https://repo.magento.com/) par le MageID associé à votre licence partenaire.

#### Comment puis-je savoir si mon MageID est le principal ?

Pour déterminer si votre MageID est principal, essayez les méthodes suivantes :

1. Connectez-vous à [magento.com](https://account.magento.com/customer/account/login) et accédez à l’onglet **Mes produits et services**. Dans la sous-section Partenaires , vérifiez si les informations de licence du partenaire actif s’affichent :
   * Si les informations de licence du partenaire actif s’affichent, votre ID d’image est principal. La licence Partenaire est active si la valeur END DATE correspond à une date ultérieure.
   * Si vous ne voyez pas les informations de licence du partenaire actif, votre MageID dispose uniquement d’un accès partagé. Pour savoir qui est le titulaire de l’ID principal, accédez au **Partagé avec moi** Notez le NOM DE PARTAGE qui y est spécifié. Cliquez sur **Changer de compte** et sélectionnez la valeur que vous avez notée dans SHARENAME. Sur la page de bienvenue, vous verrez l’e-mail du titulaire de l’ID principal.
1. Si, pour une raison quelconque, vous ne trouvez pas ces informations sur [magento.com](https://account.magento.com/customer/account/login), veuillez contacter votre responsable partenaire.
1. Si aucun des problèmes ci-dessus ne fonctionne, [contactez l’assistance technique](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide).

#### Le développeur ne dispose pas d’un accès correct aux clés

Si vous êtes le propriétaire principal de MageID et que vous devez donner accès à un développeur de votre équipe, procédez comme suit :

1. Demandez au propriétaire principal de MageID de se connecter à [account.magento.com](https://account.magento.com/customer/account/login).
1. Sélectionnez l’onglet **Marketplace**, puis cliquez sur **Clés d’accès**.
1. Sélectionnez **Créer une clé d’accès** et nommez-la.
1. Envoyez les clés à votre développeur.

### Ne fait pas partie du programme d&#39;accès anticipé

Notre programme d’accès à Beta n’est disponible que pour nos partenaires solutions et techniques afin qu’ils puissent évaluer notre code de préproduction. Pour être incluse dans le programme d’accès à Beta, votre entreprise doit disposer d’un compte de partenaire Adobe actif et en règle qui a signé l’accord de confidentialité Beta [ici](https://github.com/magento/magento2/wiki/Magento-Beta-Program). Si vous pensez répondre à ces critères et ne pas pouvoir accéder au code bêta, contactez [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
