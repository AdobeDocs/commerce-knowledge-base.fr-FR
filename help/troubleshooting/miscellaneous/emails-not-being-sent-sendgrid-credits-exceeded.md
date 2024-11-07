---
title: Emails non envoyés lorsque les crédits SendGrid ont été dépassés sur Adobe Commerce
description: Cet article fournit une solution lorsque vos emails ne sont pas envoyés, car vous avez dépassé la limite de crédits SendGrid pour Adobe Commerce.
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Emails non envoyés lorsque les crédits SendGrid ont été dépassés sur Adobe Commerce

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.3

## Problème

Les crédits SendGrid se rapportent au nombre d’emails autorisés qui peuvent être envoyés. Seuls 12 000 emails peuvent être envoyés par mois à partir des branches d’intégration et d’évaluation. Les crédits sont renouvelés au début du mois, donc si vous êtes à court de crédits, vous devrez attendre le renouvellement.

Il n’existe aucune limite stricte au nombre d’emails pouvant être envoyés en production, à condition que la Réputation de l’expéditeur dépasse 95 %. La réputation est affectée par le nombre d’emails rejetés/rebonds et si les registres de spam basés sur DNS ont marqué votre domaine comme source potentielle de spam. En production, un total de 12 000 emails sont alloués par jour, mais ce nombre peut être étendu en fonction du nombre moyen d’emails envoyés au cours des cinq jours précédents.

## Comment vérifier si vos crédits ont été dépassés :

Architecture de plan d’Adobe Commerce sur l’infrastructure cloud Pro : vérifiez le `/var/log/mail.log`. Un message tel que celui-ci peut s’afficher :

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## Cause

Le nombre d’emails autorisés pouvant être envoyés est limité.

## Solution

* Si ce message s’affiche dans l’environnement de production, [envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket), fournissez le message ci-dessus et demandez l’augmentation des crédits.
* Si ce message ne s’affiche pas ou si vous utilisez l’architecture de plan de démarrage pour l’infrastructure cloud d’Adobe Commerce, [envoyez également un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et indiquez que le fichier `mail.log` n’indique pas que les crédits ont été dépassés.

## Lecture connexe

* [SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid) dans notre documentation destinée aux développeurs.
