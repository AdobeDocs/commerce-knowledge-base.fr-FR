---
title: Informations d’expiration sur le certificat SSL personnalisé
description: Cet article fournit une solution pour le cas où un certificat SSL personnalisé a été mis à jour avec un certificat SSL fourni par Adobe.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Informations d’expiration sur le certificat SSL personnalisé

Cet article fournit une solution pour le cas où un certificat SSL personnalisé a été mis à jour avec un certificat SSL fourni par Adobe.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Adobe Commerce met automatiquement à jour les certificats SSL 30 jours avant l’expiration. Cette automatisation ne vérifie pas si le certificat remplacé est un SSL interne ou un SSL tiers personnalisé et le remplacera par un SSL interne valide lors de la détection de l’expiration. Cela peut prêter à confusion pour les propriétaires et les opérateurs du site qui s’attendent à ce que le certificat personnalisé soit présent sur le site. Cela peut également entraîner d’autres problèmes de fonctionnalité, notamment, mais pas uniquement, une panne du site.

<u>Procédure à suivre</u>

1. Certificat SSL personnalisé installé pour le site web.
1. Automation détecte que le certificat SSL personnalisé va expirer dans 30 jours.
1. Adobe Commerce remplace automatiquement le certificat personnalisé par notre certificat interne.

<u>Résultats attendus</u>

Adobe Commerce ignore les certificats personnalisés lors de l’exécution de sa mise à jour automatisée de certificat SSL.

<u>Résultats réels</u>

Adobe Commerce met à jour tout certificat dans les 30 jours suivant son expiration.

## Solution

Lorsqu’un commerçant choisit d’utiliser son propre certificat SSL personnalisé, celui-ci doit être mis à jour plus de 30 jours avant l’expiration du certificat pour s’assurer qu’il ne sera pas remplacé par un certificat SSL Adobe Commerce interne.

Si vous vous trouvez dans une situation où votre SSL personnalisé a été remplacé par notre SSL interne et que vous souhaitez le remplacer par votre certificat SSL personnalisé mis à jour, veuillez [soumettre une demande d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) avec l’emplacement où vous avez chargé vos nouveaux fichiers de certificat. Veuillez inclure la date de début du nouveau SSL. Une fois que nous disposons de ces informations, nous pouvons procéder à l’installation du nouveau certificat SSL.

## Lecture connexe

* Certificats [SSL (TLS) pour Magento Commerce Cloud : FAQ](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) dans notre base de connaissances d’assistance.
* [Référence des outils de ligne de commande : certificat magento-cloud:add](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-reference#certificateadd) dans notre documentation destinée aux développeurs.
* [Lancer la liste de contrôle](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/checklist)dans notre documentation destinée aux développeurs.
* [Accédez à l’outil d’analyse à l’échelle du site](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access#step-2-access-site-wide-analysis-tool) dans notre guide de l’utilisateur.
