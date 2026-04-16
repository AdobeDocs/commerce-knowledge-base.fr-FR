---
title: Comment mettre à jour le profil de compte cloud
description: Cet article décrit les étapes à suivre pour modifier le profil sur le compte cloud.
feature: Cloud, Support
role: Admin, Developer
exl-id: b0c9dbcf-9745-494d-a662-80c5c6378068
source-git-commit: bc8dbb1b43c3f2ad8f2ac214fd303f6a4d3e3412
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Comment mettre à jour le profil de compte cloud

Cet article décrit la procédure à suivre pour modifier le profil sur le compte cloud.

## Solution

Lors de la modification d’un profil sur le compte cloud, les champs suivants peuvent être modifiés :

1. [!UICONTROL First name]
1. [!UICONTROL Last name]
1. [!UICONTROL Username]

   >[!NOTE]
   >
   >La mise à jour du nom d’utilisateur de la console cloud modifie l’URL du projet de `https://console.adobecommerce.com <old-username>/<project-id>` en `https://console.adobecommerce.com/<new-username>/<project-id>`.
   >
   >Après la mise à jour, les liens qui utilisent l’ancienne URL ne fonctionneront plus. Les membres de l’équipe doivent mettre à jour les signets enregistrés, la documentation interne et toute automatisation pour utiliser la nouvelle URL.
   >
   >Cette modification s’applique uniquement à la nouvelle URL de la console cloud. L’URL de projet héritée (`https://<region>.magento.cloud/projects/<project-id>`) n’utilise pas le nom d’utilisateur et continue de fonctionner sans modification.

Pour modifier ces champs, procédez comme suit :

1. Accédez à votre compte à l’adresse [connexion au compte &#x200B;](https://accounts.magento.cloud).
1. Cliquez sur l’onglet **[!UICONTROL Account Settings]** .
1. Cochez la case *Créer un nouveau mot de passe*.
1. Effectuez les modifications nécessaires et cliquez sur *enregistrer*.

>[!NOTE]
>
>Votre mot de passe ne sera pas modifié.

## Que peut-on modifier ?

1. **[!UICONTROL Password]** :
Pour modifier votre mot de passe, consultez la page [Réinitialisation du mot de passe &#x200B;](https://account.adobe.com/), car ce profil est lié à votre compte ou adresse e-mail.

1. **[!UICONTROL Email Address]** :
La modification de ce champ dépend de votre situation individuelle.

Si vous devez transférer la propriété de votre compte actuel à un nouveau propriétaire ou à une autre adresse e-mail, vous devez mettre à jour l’adresse e-mail de l’utilisateur principal associée au compte.

Voir : [&#128279;](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=fr)
