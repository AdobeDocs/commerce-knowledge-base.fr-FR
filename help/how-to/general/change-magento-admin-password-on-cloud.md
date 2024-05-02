---
title: Modification du mot de passe administrateur sur Adobe Commerce sur l’infrastructure cloud
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Modification du mot de passe administrateur sur Adobe Commerce sur l’infrastructure cloud

## Méthode 1 : votre mot de passe oublié (réinitialisé par courrier électronique)

![login_panel_s.png](assets/login_panel_s.png)

Lisez les étapes de la section [Réinitialiser la section de mot de passe de la connexion administrateur](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in) dans notre guide d’utilisation.

Vous trouverez ci-dessous les notes critiques sur l’utilisation de .

### Activer les emails sortants

Avant d’utiliser la variable **Mot de passe oublié** form, [activer les emails sortants](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) en utilisant la variable [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

### Vérification du dossier de courrier électronique indésirable

Si vous ne trouvez pas le message contenant un lien Réinitialiser le mot de passe , vérifiez votre *Courrier électronique indésirable* dossier. Le nom de l&#39;email est *Confirmation de réinitialisation du mot de passe pour le nom d’utilisateur administrateur.*.

## Méthode 2 : ajout d’un nouvel utilisateur administrateur

Si vous ne pouvez pas restaurer ou réinitialiser le mot de passe de l’utilisateur existant, vous pouvez créer un nouvel utilisateur administrateur et lui définir un mot de passe. Pour ce faire, procédez comme suit :

1. Utilisation [SSH pour se connecter à l’environnement distant](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Exécutez la commande suivante : `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
