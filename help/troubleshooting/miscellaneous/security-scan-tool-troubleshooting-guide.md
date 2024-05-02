---
title: Guide de dépannage de l’outil d’analyse de sécurité Adobe Commerce
description: Découvrez comment résoudre les différents problèmes liés à l’outil d’analyse de sécurité pour Adobe Commerce et Magento Open Source.
exl-id: 35e18a11-bda9-47eb-924a-1095f4f01017
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Guide de dépannage de l’outil d’analyse de sécurité Adobe Commerce

Découvrez comment résoudre les différents problèmes liés à l’outil d’analyse de sécurité pour Adobe Commerce et Magento Open Source.

## Problème : impossible d’envoyer le site

L’outil d’analyse de sécurité requiert que vous prouviez la propriété de votre site avant que le domaine ne puisse être ajouté à l’outil d’analyse de sécurité. Pour ce faire, ajoutez un code de confirmation à votre site à l’aide d’un commentaire de HTML ou de la variable `<meta>` balise . Le commentaire de HTML doit être placé dans le `<body>` , par exemple, dans la section de pied de page. La variable `<meta>` doit être placée à l’intérieur du `<head>` .

Un problème courant rencontré par les commerçants se produit lorsque l’outil d’analyse de sécurité ne parvient pas à confirmer la propriété du site du commerçant.

Si vous obtenez une erreur et que vous ne pouvez pas envoyer votre site pour l’analyse, reportez-vous à la section [Message d’erreur lors de l’ajout de sites à l’analyse de sécurité](/help/troubleshooting/miscellaneous/error-message-adding-site-into-security-scan.md) article de dépannage dans notre base de connaissances de l’assistance.

## Problème : rapports vides générés par l’outil Analyse de sécurité

Vous obtenez des rapports d’analyse vides à partir de l’outil d’analyse de sécurité ou des rapports contenant une seule erreur, comme *L’outil de sécurité n’a pas pu atteindre l’URL de base.* ou *Installation du Magento introuvable sur l’URL fournie*.

### Solution

1. Vérifiez que les adresses IP 52.87.98.44, 34.196.167.176 et 3.218.25.102 ne sont pas bloquées à 80 et 443 ports.
1. Vérifiez l’URL envoyée pour les redirections (par exemple, `https://mystore.com` redirige vers `https://www.mystore.com` ou vice versa ou redirige vers d’autres noms de domaine).
1. Recherchez les journaux d’accès au serveur web/WAF pour les demandes rejetées/non satisfaites. HTTP 403 `Forbidden` et HTTP 500 `Internal server error` sont les réponses de serveur courantes qui provoquent une génération de rapports vide. Voici un exemple du code de confirmation qui bloque les demandes par les agents utilisateur :

```code block
if(req.http.user-agent ~ "(Chrome|Firefox)/[1-7][0-9]" && client.ip !~ useragent_allowlist)

{   error 403;   }
```

Vous pouvez également voir [Le rapport de l’outil d’analyse de sécurité est vide](/help/troubleshooting/miscellaneous/the-security-scan-tool-report-is-blank.md) pour plus d’informations.

## Problème : problème de sécurité résolu, mais toujours visible comme vulnérable lors de l’analyse.

Vous avez résolu un problème de sécurité et vous vous attendez à ce que l’ analyse de sécurité indique que vous n’êtes plus vulnérable au problème nouvellement résolu. Au lieu de cela, vous constatez que le rapport généré par l’analyse de sécurité vous signale toujours comme vulnérable au problème de sécurité.

### Cause

Les métadonnées d’instance de cloud ne sont collectées que pour `active` et `live` Projets cloud et n’est PAS un processus en temps réel.

Le script de collecte des statistiques est exécuté une fois par jour, puis l’outil d’analyse de sécurité doit récupérer les nouvelles données ultérieurement.

La latence attendue du cycle de synchronisation peut aller jusqu’à une semaine et dure au moins 24 heures.

Les états suivants peuvent apparaître à partir des vérifications :

1. **Pass**: l’outil d’analyse de sécurité a analysé vos données mises à jour et approuvé les modifications.
1. **Inconnu**: l’outil d’analyse de sécurité ne contient pas encore de données sur votre domaine ; attendez le prochain cycle de synchronisation.
1. **Échec**: si l’état indique un échec, vous devrez résoudre le problème (activer 2FA, modifier l’URL d’administration, etc.) et attendez le cycle de synchronisation suivant.

Si 24 heures se sont écoulées depuis que les modifications ont été apportées à l’instance et qu’elles ne sont pas répercutées dans le rapport Analyse de sécurité, vous pouvez [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Indiquez l’URL du magasin lors de l’envoi du ticket.

## Échec de BotNet Suspect

Vous recevez une notification concernant l’échec de &quot;Suspect BotNet&quot;.

### Cause

1. Le nom de domaine du magasin est entré dans une &quot;liste de participants potentiels de BotNet&quot; en 2019, et a eu la fonction Admin panel, downloader, ou RSS publiquement exposée, et/ou son URL a été mentionnée dans les forums de skimming CC.
1. L’alerte peut être provoquée par les signes de compromis et/ou de malware du magasin, comme JavaScript trouvé sur la page.
1. Il ne s&#39;agit pas nécessairement d&#39;une question en cours. Si le magasin a été compromis précédemment, son nom d&#39;hôte peut toujours flotter autour du web noir comme nom de &#39;victime&#39;.
1. Il se peut également qu’il soit dû non pas à Adobe Commerce, mais à un compromis système (au niveau du système d’exploitation).

### Solution

1. Recherchez les comptes SSH nouvellement créés, les modifications de système de fichiers, etc.
1. Effectuez une vérification de sécurité.
1. Vérifiez la version et la mise à niveau d’Adobe Commerce, en particulier si le Magento 1 est toujours en cours d’exécution, qui n’est plus pris en charge.
1. Si le problème persiste, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et indiquez l’URL du magasin.

## Problème : échec de l’injection du compromis

Vous recevez une erreur concernant un échec de type &quot;Injection de compromis&quot;.

### Solution

1. Examinez les scripts indiqués dans le rapport de l’outil d’analyse de sécurité.
1. Examinez le corps de la source de la page d’accueil pour les injections de script intégrées.
1. Révision des modifications de configuration du système, en particulier personnalisées `HTML head` et `Miscellaneous HTML` in `footer` valeurs de section.
1. Effectuez une révision du code et de la base de données pour détecter les modifications inconnues et les signes de malware injectés.

Si aucun des éléments ci-dessus ne vous aide, [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et indiquez l’URL de stockage et le message d’erreur du rapport.

## Questions fréquentes

### L’analyse de sécurité va-t-elle affecter les performances de mon site web ?

Non. L’analyse de sécurité effectue toutes les requêtes une par une, comme un utilisateur unique. Pour cette raison, l’analyse de sécurité ne doit pas affecter les performances du site web.

### Combien de temps Adobe Commerce conserve-t-il les rapports d’analyse de sécurité ?

Vous pouvez générer les 10 rapports précédents à partir de votre fin. Si des rapports plus anciens sont requis, contactez l’assistance d’Adobe Commerce. Vous pouvez obtenir jusqu’à un an de rapports d’analyse de sécurité antérieurs.

### Quelles informations sont requises lors de l’envoi d’un ticket d’assistance ?

Veillez à indiquer le nom de domaine.
