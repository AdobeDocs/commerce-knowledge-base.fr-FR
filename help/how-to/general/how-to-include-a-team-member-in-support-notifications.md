---
title: Comment inclure un membre de l’équipe dans les notifications d’assistance
description: Cet article explique comment inclure un membre de l’équipe dans les notifications d’assistance.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Comment inclure un membre de l’équipe dans les notifications d’assistance

Cet article explique comment inclure un membre de l’équipe pour recevoir automatiquement des mises à jour de l’assistance par le biais de notifications par e-mail.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, tous [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Cause

* Le membre de l’équipe n’a pas été ajouté au [!DNL cloud project] avec les privilèges nécessaires.
* Le membre de l’équipe ne dispose pas d’un compte d’assistance.

## Solution

1. Accédez au **[!DNL Cloud Project URL]** (Exemple : `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Vérifiez si le membre de l’équipe a été ajouté au projet et s’il est une [!DNL Super User].

S’ils ne nécessitent pas [!DNL cloud project] accès, envoi d’une [Demande d’assistance au Centre d’assistance Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) à automatiquement CC : ils sont sur tous les tickets et fournissent également leurs **[!DNL MAGE ID]** (le cas échéant).

S’ils n’ont pas été ajoutés au projet, vous devez les ajouter en tant que [!DNL Super User] et accorder [!DNL Shared Access]:

* [Gestion de l’accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) dans notre guide d’utilisation.
* [Impossible d’ajouter un utilisateur au projet cloud Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) dans notre base de connaissances Commerce.
* [Guide de l’utilisateur du centre d’aide Adobe Commerce : accès partagé](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) dans notre base de connaissances Commerce.

S’ils ont été ajoutés au [!DNL cloud project], mais n’avez pas la variable [!DNL Super User role], mettez à jour leurs [!DNL role] dans [Gestion de l’accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Lecture connexe

[Les anciens membres de l’équipe reçoivent des e-mails de notification cloud Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
