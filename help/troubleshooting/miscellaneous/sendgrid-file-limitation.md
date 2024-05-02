---
title: '[!DNL SendGrid] limitation de fichiers pour Adobe Commerce Cloud'
description: Cet article fournit une solution à la variable  [!DNL SendGrid] limitation d’Adobe Commerce sur l’infrastructure cloud.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# [!DNL SendGrid] limitation de Adobe Commerce Cloud

Cet article fournit quelques solutions de contournement au [!DNL SendGrid] limitation d’Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problème

Vous tentez d’envoyer des pièces jointes volumineuses dans les emails et les erreurs de journal suivantes s’affichent :

Dans `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

Dans `/var/log/exception.log`

Production :

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Évaluation :

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging2 :

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Cause

[!DNL SendGrid] est limitée par le système à une taille de 30 Mo pour les emails. Il est recommandé de ne pas utiliser de pièces jointes dont la taille dépasse 10 Mo. Voir [Envoi de pièces jointes](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) dans la documentation SendGrid pour plus d’informations.

## Solution

* N’utilisez pas de pièces jointes supérieures à 6 Mo ou 10 Mo.
* Envisagez d’utiliser un serveur SMTP distant sur votre instance Adobe Commerce. Pour connaître les étapes, voir [Configuration des communications par courrier électronique](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html) dans notre guide sur les systèmes d’administration.
* Reconfigurez votre serveur afin que les fichiers puissent être enregistrés dans votre module, puis joignez le lien aux fichiers des emails.

## Lecture connexe

* [[!DNL SendGrid] service email](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html) dans notre guide Commerce on Cloud Infrastructure.
