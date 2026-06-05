---
title: Limitation des fichiers [!DNL SendGrid] pour Adobe Commerce Cloud
description: Cet article fournit une solution de contournement de la limitation  [!DNL SendGrid]  d’Adobe Commerce sur les infrastructures cloud.
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Limitation de [!DNL SendGrid] pour Adobe Commerce Cloud

Cet article fournit quelques solutions de contournement à la limite de [!DNL SendGrid] d’Adobe Commerce sur les infrastructures cloud.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## Problème

Vous tentez d’envoyer des pièces jointes volumineuses dans les e-mails et vous voyez ces erreurs de journal :

En `/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

En `/var/log/exception.log`

Production :

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Évaluation :

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

Staging2 :

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## Cause

[!DNL SendGrid] présente une limitation du système de 30 Mo pour la taille des e-mails. Il est recommandé de ne pas utiliser de pièces jointes de plus de 10 Mo. Voir [Envoi de pièces jointes](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh) dans la documentation SendGrid pour plus d’informations.

## Solution

* N’utilisez pas de pièces jointes de plus de 6 Mo ou 10 Mo.
* Envisagez l’utilisation d’un serveur SMTP distant sur votre instance Adobe Commerce. Pour connaître les étapes, reportez-vous à [Configurer les communications par e-mail](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html?lang=fr) dans notre Guide des systèmes d’administration.
* Reconfigurez votre serveur afin que les fichiers puissent être enregistrés dans votre module, puis joignez le lien vers les fichiers dans les e-mails.

## Lecture connexe

* [[!DNL SendGrid] service de messagerie électronique](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html?lang=fr) dans notre Guide de Commerce sur les infrastructures cloud.
