---
title: Comment inclure un membre de l’équipe dans les notifications d’assistance
description: Cet article explique comment inclure un membre de l’équipe dans les notifications d’assistance.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 6a4c1115aa92663ce12ce848dc583538e155509b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Comment inclure un membre de l’équipe dans les notifications d’assistance

Cet article explique comment inclure un membre de l’équipe pour recevoir automatiquement les mises à jour de l’assistance par e-mail.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Cause

* Le membre d&#39;équipe n&#39;a pas été ajouté à la [!DNL cloud project] avec les privilèges nécessaires.
* Le membre de l’équipe ne dispose pas d’un compte d’assistance.

## Solution

1. Accédez à la **[!DNL Cloud Project URL]** (exemple : `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Vérifiez si le membre de l&#39;équipe a été ajouté au projet et s&#39;il est un [!DNL Super User].

S’ils n’ont pas été ajoutés au projet, vous devrez les ajouter en tant que [!DNL Super User] et accorder la [!DNL Shared Access] :

* [Gérer l’accès utilisateur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr) dans notre guide de l’utilisateur.
* [Impossible d’ajouter un utilisateur ou une utilisatrice au projet cloud Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html?lang=fr) dans notre base de connaissances Commerce.
* [Guide de l&#39;utilisateur du centre d&#39;aide Adobe Commerce : accès partagé](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=fr#shared-access) dans notre base de connaissances Commerce.

S’ils ont été ajoutés à la [!DNL cloud project], mais ne disposent pas du [!DNL Super User role], mettez à jour leur [!DNL role] en conséquence dans [Gérer l’accès utilisateur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=fr).

Si vous souhaitez permettre à un membre de l’équipe d’être observateur sur tous les cas ouverts pour votre organisation, envoyez un ticket [support](https://experienceleague.adobe.com/home?lang=fr&amp;support-tab=home#support).

## Lecture connexe

[Les anciens membres de l’équipe reçoivent des e-mails de notification Adobe Commerce Cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html?lang=fr)
