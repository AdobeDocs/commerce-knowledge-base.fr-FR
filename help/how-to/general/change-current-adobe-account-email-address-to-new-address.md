---
title: Modifier l’adresse e-mail du compte Adobe actuel
description: Découvrez comment modifier l’adresse e-mail actuelle enregistrée dans le compte Adobe en une nouvelle adresse qui n’est actuellement pas enregistrée dans le compte Adobe ou le compte Magento.
exl-id: ca549d38-0d62-4206-9727-0ed85b733dc3
feature: Communications
source-git-commit: 8d91d4c21dc981accf25537cdb61e1271e17b78c
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Modifier l’adresse e-mail du compte Adobe actuel

Cet article explique comment modifier l’adresse e-mail actuelle enregistrée dans le compte [&#128279;](https://account.adobe.com/) en une nouvelle adresse qui n’est actuellement pas enregistrée dans le compte [Adobe](https://account.adobe.com/) ou le compte [Magento](https://account.magento.com/).

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes et versions de déploiement)

## Conditions préalables

Le propriétaire de la nouvelle adresse e-mail doit avoir accès à l’adresse e-mail actuelle.

Si vous n’avez pas accès à l’adresse e-mail actuelle, configurez le transfert d’e-mail de l’adresse e-mail du propriétaire actuel vers une nouvelle adresse e-mail à l’aide de la configuration du serveur de messagerie de l’entreprise.

## Étapes de modification de l’adresse e-mail

Pour modifier l’adresse e-mail, procédez comme suit :

1. Réinitialisez le mot de passe utilisé avec l’ancienne adresse e-mail. Suivez les instructions fournies dans [Réinitialiser le mot de passe oublié](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html) dans l’aide d’Adobe.
1. Le lien de réinitialisation du mot de passe est envoyé à la boîte aux lettres du propriétaire actuel avec des instructions.
1. Accédez à la page [Compte &#x200B;](https://account.adobe.com) pour vous connecter avec le nouvel e-mail et configurer le mot de passe.

## Important : le nom d’utilisateur du compte cloud n’est pas mis à jour automatiquement

Si vous utilisez Adobe Commerce sur des infrastructures cloud, la modification de l’adresse e-mail sur votre compte Adobe ou de votre MAGE ID ne met pas automatiquement à jour le nom d’utilisateur affiché dans votre [compte cloud](https://accounts.magento.cloud).

Après avoir suivi les étapes décrites dans cet article pour modifier l’adresse e-mail de votre compte Adobe :

1. Connectez-vous à votre compte Cloud à l’adresse [&#128279;](https://accounts.magento.cloud).
1. Mettez à jour manuellement le profil de compte cloud (nom d’utilisateur) en suivant les étapes de la section [Comment mettre à jour le profil de compte cloud](/help/how-to/general/how-to-update-the-cloud-account-profile.md) de notre base de connaissances d’assistance.

Cela garantit que le nom d’utilisateur de votre compte Cloud reste aligné sur l’e-mail Adobe ou MAGE ID mis à jour et évite toute confusion lors de l’accès aux projets Cloud ou de la réception de notifications système.

## Vérifier l’accès au Marketplace et au support après le changement d’e-mail

Après avoir modifié l’adresse e-mail de votre ID MAGE, vous devez également effectuer les étapes suivantes pour vous assurer que le Marketplace et le support Adobe Commerce reconnaissent correctement votre nouvel e-mail :

### Vérifier l’adresse e-mail Commerce Marketplace

1. Connectez-vous à votre compte Commerce Marketplace et vérifiez que l’adresse e-mail associée à votre compte a été mise à jour vers la nouvelle adresse.
1. Si l’e-mail n’a pas été mis à jour, envoyez un [ticket d’assistance](https://experienceleague.adobe.com/en/support#home) pour demander que l’e-mail du compte Commerce Marketplace soit corrigé.

### Demander à l’assistance technique de finaliser les mises à jour des comptes internes

1. Envoyez un [ticket d’assistance](https://experienceleague.adobe.com/en/support#home) nous demandant d’effectuer toutes les mises à jour internes requises (par exemple, la mise à jour du lien entre vos anciens et nouveaux Adobe ID et votre MAGE ID).
1. Si vous avez déjà ouvert un ticket d’assistance parce que l’e-mail Commerce Marketplace n’a pas été mis à jour dans la section précédente, vous pouvez utiliser le même ticket pour demander ces mises à jour internes supplémentaires.
