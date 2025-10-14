---
title: Modifier le mot de passe administrateur sur Adobe Commerce sur l’infrastructure cloud
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 44238f6d57458028cb1e2612d45e1e12b3f39916
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Modifier le mot de passe administrateur sur Adobe Commerce sur l’infrastructure cloud

## Méthode 1 : Mot de passe oublié (réinitialisé par e-mail)

![login_panel_s.png](assets/login_panel_s.png)

Lisez les étapes de la section [&#x200B; Réinitialiser votre mot de passe de l’option Connexion administrateur &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html?lang=fr#admin-sign-in) dans notre guide d’utilisation.

Vous trouverez ci-dessous les notes d’utilisation critiques.

### Activer les emails sortants

Avant d’utiliser le formulaire **Mot de passe oublié**, assurez-vous d’[activer les e-mails sortants](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html?lang=fr) à l’aide de la [console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=fr). Cela s’applique uniquement aux environnements d’intégration et aux projets Sandbox.

Si les e-mails sortants sont réellement désactivés sur Pro Production ou Staging (signifiant que l&#39;e-mail n&#39;a pas été récupéré par SendGrid), vous pouvez vérifier cela en cochant la case [&#x200B; Activer les e-mails dans la console cloud &#x200B;](https://experienceleague.adobe.com/fr/docs/commerce-on-cloud/user-guide/project/outgoing-emails#enable-emails-in-the-cli). Si le problème persiste, vous pouvez envoyer un ticket d’assistance pour Adobe [ticket d’assistance](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).

### Vérifier votre dossier Courrier indésirable

Si vous ne trouvez pas le message avec un lien Réinitialiser le mot de passe , vérifiez votre dossier *Courrier indésirable*. Le nom de l’e-mail est *Confirmation de réinitialisation du mot de passe pour le nom d’utilisateur administrateur*.

## Méthode 2 : ajouter un nouvel utilisateur administrateur

Si vous ne pouvez pas restaurer ou réinitialiser le mot de passe de l’utilisateur existant, vous pouvez créer un utilisateur administrateur et définir un mot de passe pour cet utilisateur. Pour ce faire, procédez comme suit :

1. Utilisez [SSH pour vous connecter à l’environnement distant](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=fr).
1. Exécutez la commande suivante : `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
