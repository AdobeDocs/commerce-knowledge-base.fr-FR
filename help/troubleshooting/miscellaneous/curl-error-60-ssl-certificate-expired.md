---
title: 'Erreur cURL 60 : certificat SSL expiré'
description: "Cet article explique comment vérifier quand la dernière fois qu’une branche a été déployée après avoir reçu une erreur cURL 60 : le certificat SSL a expiré dans les branches de Principal ou d’intégration sur Adobe Commerce sur l’infrastructure cloud."
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: 6f631ca35b663c386bca9efe6e56db266502c0b1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# cURL erreur 60 : certificat SSL expiré

Cet article explique comment vérifier à quel moment une branche a été déployée pour la dernière fois après avoir reçu une `cURL error 60`: [!DNL SSL certificate] expiré dans le [!DNL Master] ou [!DNL Integration] branches sur Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Cause

La variable [!DNL SSL certificates] dans ces branches sont uniquement valides pendant 30 jours et la branche n’a peut-être pas été redéployée dans plus de 30 jours.

L’erreur se présentera comme suit :

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

## Solution

Vérifiez quand la dernière fois que la branche a été déployée. Si le seuil est supérieur à 30 jours, redéployez la branche.

Deux méthodes à vérifier lorsque le dernier déploiement a été effectué :

* [Méthode 1 : utilisation [!DNL magento-cloud] CLI](#meth2).
* [Méthode 2 : ouvrez la [!DNL Project URL]](#meth3).

Si le déploiement a été terminé avec succès, la variable [!DNL SSL certificate] sera automatiquement renouvelée.

Si le déploiement échoue et que vous avez besoin d’aide pour le résoudre, [envoyer un ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### Méthode 1 : utilisation [!DNL magento-cloud] CLI {#meth2}

Exécutez la commande suivante : `magento-cloud activity:list`

### Méthode 2 : ouvrez la [!DNL Project URL] {#meth3}

Accédez à, par exemple : `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`et vérifiez quand le dernier déploiement a été effectué.

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [API Cloud Manager : SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Configuration rapide : configuration de certificats SSL/TLS](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates)

Dans notre base de connaissances de soutien :

* [Informations d’expiration de certificat SSL personnalisées](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [Certificats SSL (TLS) pour Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
