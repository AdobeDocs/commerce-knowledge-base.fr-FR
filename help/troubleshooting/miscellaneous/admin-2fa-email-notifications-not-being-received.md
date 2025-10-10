---
title: Les notifications par e-mail de l’administrateur 2FA ne sont pas reçues
description: Cet article propose une résolution des problèmes lorsque vous ne recevez pas l’e-mail contenant les instructions d’achèvement de la configuration après avoir configuré l’authentification à deux facteurs (2FA) afin d’améliorer la sécurité de l’accès administrateur dans Adobe Commerce sur l’infrastructure cloud.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 9eaea028886e74fc06c9516801919cd7f650f98c
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Les notifications par e-mail de l’administrateur 2FA ne sont pas reçues


## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes versions confondues

## Problème

Vous avez configuré l’authentification à deux facteurs afin d’améliorer la sécurité d’accès de l’administrateur, mais vous ne recevez pas l’e-mail contenant les instructions pour terminer la configuration.

## Cause

Si vous n&#39;avez pas correctement configuré l&#39;e-mail de l&#39;expéditeur ou si votre domaine n&#39;a pas été marqué en blanc dans SendGrid, l&#39;e-mail se serait probablement retrouvé dans le dossier Spam.

## Dépannage

### Étape 1 : vérifier votre dossier Spam

1. Si l&#39;e-mail n&#39;apparaît pas dans votre dossier Spam, exécutez cette requête Mysql pour vérifier que les adresses e-mail ont été configurées :

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * Si elle ne renvoie aucun résultat, cela signifie que l’adresse de l’expéditeur n’a pas été configurée.
Puisque vous n’avez pas accès à l’administrateur, vous devez insérer la configuration dans la base de données. Saisissez l’adresse e-mail appropriée et exécutez l’instruction MySQL :

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * S’il renvoie un résultat, passez à **étape 2**.

1. Si l&#39;email s&#39;est affiché dans votre dossier Spam, cliquez sur le lien contenu dans l&#39;email. Si le lien a expiré depuis, essayez de vous reconnecter pour répéter le processus.
1. Une fois que vous avez obtenu l’accès, accédez à **Magasins** > **Configuration** > **Général** > **Stocker les adresses e-mail** et configurez les adresses e-mail.

### Étape 2 : si/une fois les adresses e-mail correctement configurées, insérez SSH dans l’environnement et exécutez cette commande :

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Recherchez l&#39;e-mail dans votre dossier Spam.

Si l’e-mail s’est affiché dans votre dossier Spam, l’authentification d’e-mail de votre domaine n’est peut-être pas entièrement configurée pour la diffusion sortante via SendGrid.

Si vous utilisez le service SendGrid géré par Adobe :

[Envoyez un ticket d’assistance](https://experienceleague.adobe.com/home?lang=fr&support-tab=home#support) demandant que votre domaine d’envoi soit authentifié (parfois appelé *marque blanche*) avec SendGrid.
Ce processus implique l’ajout d’enregistrements DNS (DKIM et SPF) pour autoriser SendGrid à envoyer des e-mails au nom de votre domaine, ce qui augmente la probabilité que vos e-mails soient envoyés à la boîte de réception plutôt qu’au dossier Spam.

Si vous utilisez votre propre compte SendGrid :

Vous êtes responsable de la gestion des paramètres d’authentification de votre domaine directement dans le tableau de bord de votre compte SendGrid. Pour plus d’informations, voir [Configuration de l’authentification de domaine](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/how-to-set-up-domain-authentication) dans la documentation SendGrid.

>[!NOTE]
>
>Certains clients peuvent choisir d’utiliser un service SendGrid configuré séparément pour un contrôle total de la délivrabilité et de la conformité des e-mails (par exemple, les exigences HIPAA). Assurez-vous de suivre les étapes de dépannage appropriées en fonction du type de service SendGrid (géré par Adobe ou autogéré) que vous utilisez.


## Lecture connexe

* [SendGrid](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/project/sendgrid) dans notre documentation destinée aux développeurs.
