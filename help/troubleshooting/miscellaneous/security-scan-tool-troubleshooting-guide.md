---
title: Guide de dépannage de l’outil Adobe Commerce Security Scan
description: Découvrez comment résoudre les différents problèmes liés à l’outil Analyse de la sécurité pour Adobe Commerce et Magento Open Source.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: c6e338fb33477ab107fe4de382b485339b57275a
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 0%

---

# Guide de dépannage de l’outil Adobe Commerce Security Scan

Découvrez comment résoudre les différents problèmes liés à l’outil Analyse de la sécurité pour Adobe Commerce et Magento Open Source.

## Problème : impossible d’envoyer le site

L&#39;outil Analyse de sécurité exige que vous prouviez que vous êtes propriétaire de votre site avant de pouvoir ajouter le domaine à l&#39;outil Analyse de sécurité. Pour ce faire, ajoutez un code de confirmation à votre site à l’aide d’un commentaire HTML ou de la balise `<meta>`. Le commentaire HTML doit être placé à l’intérieur de la balise `<body>`, par exemple dans la section de pied de page. La balise `<meta>` doit être placée dans la section `<head>` de la page.

Un problème courant auquel sont confrontés les commerçants se produit lorsque l’outil de scan de sécurité n’est pas en mesure de confirmer la propriété du site du commerçant.

Si vous obtenez une erreur et que vous ne pouvez pas envoyer votre site pour l’analyse, reportez-vous à l’article [ Message d’erreur lors de l’ajout de sites à l’analyse de sécurité ](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) dépannage dans notre base de connaissances d’assistance.

## Problème : rapports vides générés par l’outil Analyse de sécurité

Vous obtenez des rapports d&#39;analyse vides de l&#39;outil Analyse de sécurité ou des rapports contenant une seule erreur comme *L&#39;outil de sécurité n&#39;a pas pu atteindre l&#39;URL de base* ou l&#39;installation de *Magento est introuvable sur l&#39;URL fournie*.

### Solution

1. Vérifiez que les adresses IP 52.87.98.44, 34.196.167.176 et 3.218.25.102 ne sont pas bloquées sur les ports 80 et 443.
1. Recherchez des redirections dans l’URL envoyée (par exemple, des redirections `https://mystore.com` vers `https://www.mystore.com` ou vice versa ou des redirections vers d’autres noms de domaine).
1. Vérifiez les journaux d’accès WAF/serveur web pour les demandes rejetées/non satisfaites. Les `Forbidden` HTTP 403 et les `Internal server error` HTTP 500 sont les réponses courantes du serveur qui provoquent la génération de rapports vides. Voici un exemple de code de confirmation qui bloque les requêtes des agents utilisateurs :

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

Consultez également l’article [Le rapport de l’outil d’analyse de sécurité est vierge](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) dans notre base de connaissances d’assistance pour plus d’informations.

## Problème : problème de sécurité résolu, mais toujours visible comme vulnérable lors de l’analyse

Vous avez résolu un problème de sécurité et vous attendez que l&#39;analyse de sécurité indique que vous n&#39;êtes plus vulnérable au problème nouvellement résolu. Au lieu de cela, vous constatez que le rapport généré par l’analyse de sécurité vous signale toujours comme vulnérable au problème de sécurité.

### Cause

Les métadonnées des instances cloud sont collectées uniquement pour les projets cloud `active` et `live` et ne constituent PAS un processus en temps réel.

Le script de collecte de statistiques est exécuté une fois par jour, puis l&#39;outil Analyse de sécurité doit récupérer les nouvelles données ultérieurement.

La latence prévue du cycle de synchronisation peut aller jusqu’à une semaine et prend au moins 24 heures.

Les statuts suivants peuvent apparaître à partir des contrôles :

1. **Réussite** : l’outil Analyse de sécurité a analysé vos données mises à jour et approuvé les modifications.
1. **Inconnu** : l’outil Analyse de sécurité ne dispose pas encore de données sur votre domaine ; attendez le prochain cycle de synchronisation.
1. **Échec** : si le statut indique un échec, vous devrez résoudre le problème (activer 2FA, modifier l’URL d’administration, etc.) et attendre le prochain cycle de synchronisation.

Si 24 heures se sont écoulées depuis que les modifications ont été apportées à l’instance et qu’elles ne sont pas reflétées dans le rapport d’analyse de sécurité, vous pouvez [soumettre un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Indiquez l’URL du magasin lors de l’envoi du ticket.

## Échec suspect de BotNet

Vous recevez une notification concernant l’échec de « BotNet Suspect ».

### Cause

1. Le nom de domaine de magasin est entré dans une « Liste de participants potentiels de BotNet » en 2019, et le panneau d&#39;administration, le téléchargeur ou la fonctionnalité RSS ont été publiquement exposés, et/ou son URL a été mentionnée dans les forums d&#39;écumage CC.
1. L’alerte peut être due à des signes de compromission de magasin et/ou à des programmes malveillants, comme JavaScript sur la page.
1. Ce n&#39;est pas nécessairement un problème permanent. Si le magasin a déjà été compromis, son nom d&#39;hôte peut toujours flotter sur le web sombre comme nom de « victime ».
1. Elle peut également être due non pas à Adobe Commerce, mais à une erreur système (au niveau du système d’exploitation).

### Solution

1. Recherchez les comptes SSH nouvellement créés, les modifications apportées au système de fichiers, etc.
1. Effectuez une vérification de la sécurité.
1. Vérifiez la version d’Adobe Commerce et la mise à niveau, en particulier si elle exécute toujours Magento 1, qui n’est plus pris en charge.
1. Si le problème persiste, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et indiquez l’URL du magasin.

## Problème : échec de l’injection de compromis

Vous recevez une erreur concernant un échec d’« injection de compromis ».

### Solution

1. Examinez les scripts indiqués dans le rapport de l’outil Analyse de sécurité .
1. Consultez le corps source de la page d’accueil pour les injections de script en ligne.
1. Passez en revue les modifications apportées à la configuration du système, en particulier les `HTML head` et `Miscellaneous HTML` personnalisés dans les valeurs de section `footer`.
1. Effectuez une révision du code et de la base de données pour détecter les modifications et signes inhabituels de programmes malveillants injectés.

Si rien de ce qui précède ne vous aide, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et indiquez l’URL du magasin et le message d’erreur à partir du rapport.

## Questions fréquentes

### L’analyse de sécurité affectera-t-elle les performances de mon site web ?

Non. L’analyse de sécurité effectue une par une toutes les demandes comme s’il s’agissait d’un seul utilisateur. Pour cette raison, l’analyse de sécurité ne doit pas affecter les performances du site web.

### Pendant combien de temps Adobe Commerce conserve-t-il les rapports d’analyse de sécurité ?

Vous pouvez générer les 10 rapports précédents de votre côté. Si des rapports plus anciens sont requis, contactez l’assistance Adobe Commerce.

### Quelles informations sont nécessaires lors de l’envoi d’un ticket d’assistance ?

Indiquez le nom de domaine tel qu’il est envoyé pour l’[analyse de sécurité](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26357), MAGEID et Cloud Project_ID. Notez que l’ID de projet cloud n’est pas obligatoire pour Adobe Commerce On-premise.

### Que se passe-t-il si je supprime mon magasin de l’analyse des outils de numérisation ?

Si vous supprimez l’envoi du magasin, toutes les données associées, y compris les rapports d’analyse, seront supprimées. Cette opération est irréversible. L’envoi du domaine de magasin après sa suppression crée un NOUVEL envoi.
