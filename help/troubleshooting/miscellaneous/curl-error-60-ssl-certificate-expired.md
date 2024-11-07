---
title: 'Erreur cURL 60 : certificat SSL expiré'
description: "Cet article explique comment vérifier quand la dernière fois qu’une branche a été déployée après avoir reçu une erreur cURL 60 : le certificat SSL a expiré dans les branches de Principal ou d’intégration sur Adobe Commerce sur l’infrastructure cloud."
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# cURL erreur 60 : certificat SSL expiré

Cet article explique comment vérifier quand la dernière fois qu’une branche a été déployée après avoir reçu un `cURL error 60` : [!DNL SSL certificate] a expiré dans les branches [!DNL Master] ou [!DNL Integration] sur Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Cause

Les [!DNL SSL certificates] de ces branches sont valides uniquement pendant 30 jours et la branche n’a peut-être pas été redéployée dans plus de 30 jours.

L’erreur se présentera comme suit :

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

## Solution

Vérifiez quand la dernière fois que la branche a été déployée. Si le seuil est supérieur à 30 jours, redéployez la branche.

Deux méthodes à vérifier lorsque le dernier déploiement a été effectué :

* [Méthode 1 : utilisez [!DNL magento-cloud] CLI](#meth2).
* [Méthode 2 : ouvrez le  [!DNL Project URL]](#meth3).

Si le déploiement est terminé avec succès, [!DNL SSL certificate] sera automatiquement renouvelé.

Si le déploiement échoue et que vous avez besoin d’aide pour le résoudre, [ envoyez un ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### Méthode 1 : utiliser [!DNL magento-cloud] CLI {#meth2}

Exécutez la commande suivante : `magento-cloud activity:list`

### Méthode 2 : ouvrez le [!DNL Project URL] {#meth3}

Accédez à, par exemple : `https://demo.magento.cloud/#/projects/<project>/environments/<environment>` et vérifiez quand le dernier déploiement a été effectué.

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [API Cloud Manager : SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [ Configuration rapide : fourniture de certificats SSL/TLS](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

Dans notre base de connaissances de soutien :

* [Informations d’expiration de certificat SSL personnalisées](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [Certificats SSL (TLS) pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
