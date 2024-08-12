---
title: Comment inclure un membre de l’équipe dans les notifications d’assistance
description: Cet article explique comment inclure un membre de l’équipe dans les notifications d’assistance.
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 771793d45000e65c1bf41137cd984d2977b0a9ff
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Comment inclure un membre de l’équipe dans les notifications d’assistance

Cet article explique comment inclure un membre de l’équipe pour recevoir automatiquement des mises à jour de l’assistance par le biais de notifications par e-mail.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les [versions prises en charge](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Cause

* Le membre de l’équipe n’a pas été ajouté à [!DNL cloud project] avec les privilèges nécessaires.
* Le membre de l’équipe ne dispose pas d’un compte d’assistance.

## Solution

1. Accédez à **[!DNL Cloud Project URL]** (Exemple : `https://us-3.magento.cloud/projects/xxxxxx/edit`).
1. Vérifiez si le membre de l’équipe a été ajouté au projet et est un [!DNL Super User].

S’ils n’ont pas été ajoutés au projet, vous devrez les ajouter en tant que [!DNL Super User] et accorder [!DNL Shared Access] :

* [Gérer l’accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) dans notre guide d’utilisation.
* [Impossible d’ajouter un utilisateur au projet cloud Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) dans notre base de connaissances Commerce.
* [Guide de l’utilisateur du centre d’aide Adobe Commerce : accès partagé](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) dans notre base de connaissances Commerce.

S&#39;ils ont été ajoutés à [!DNL cloud project], mais qu&#39;ils n&#39;ont pas le [!DNL Super User role], mettez leurs [!DNL role] à jour en conséquence dans [Gérer l&#39;accès des utilisateurs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## Lecture connexe

[ Les anciens membres de l’équipe reçoivent des emails de notification cloud Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
