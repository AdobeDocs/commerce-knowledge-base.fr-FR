---
title: Admin - Notifications par email 2FA non reçues
description: Cet article fournit un dépannage lorsque vous ne recevez pas le courrier électronique contenant les instructions de fin de la configuration après avoir configuré l’authentification à deux facteurs (2FA) afin d’améliorer la sécurité de l’accès administrateur dans Adobe Commerce sur l’infrastructure cloud.
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Admin - Notifications par email 2FA non reçues


## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

Vous avez configuré l’authentification à deux facteurs afin d’améliorer la sécurité de l’accès administrateur, mais ne recevez pas l’e-mail contenant les instructions relatives à la configuration.

## Cause

Si vous n&#39;avez pas correctement configuré l&#39;email de l&#39;expéditeur, ou si votre domaine n&#39;a pas été étiqueté en blanc dans SendGrid, l&#39;email aurait probablement fini dans le dossier Spam.

## Dépannage

### Étape 1 : Vérification du dossier Spam

1. Si l&#39;email n&#39;apparaît pas dans votre dossier Spam, exécutez cette requête Mysql pour vérifier que les adresses email ont été configurées :

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * S&#39;il ne renvoie aucun résultat, cela signifie que l&#39;adresse de l&#39;expéditeur n&#39;a pas été configurée.
Puisque vous n&#39;avez pas accès à l&#39;administrateur, vous devrez insérer la configuration dans la base de données. Connectez l’adresse électronique appropriée et exécutez l’instruction MySQL :

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * S’il renvoie un résultat, passez à l’ **étape 2**.

1. Si l&#39;email apparaît dans votre dossier Spam, cliquez sur le lien contenu dans l&#39;email. Si le lien a expiré depuis, essayez de vous reconnecter pour répéter le processus.
1. Une fois que vous avez accès, accédez à **Magasins** > **Configuration** > **Général** > **Stocker les adresses électroniques** et configurez les adresses électroniques.

### Étape 2 : si/une fois que les adresses email ont été correctement configurées, connectez-vous à l&#39;environnement et exécutez la commande suivante :

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

Recherchez l’email dans le dossier Spam . Si l&#39;email s&#39;y affichait, [envoyez un ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#login) pour demander que le domaine soit étiqueté en blanc dans SendGrid.

## Lecture connexe

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) dans notre documentation destinée aux développeurs.
