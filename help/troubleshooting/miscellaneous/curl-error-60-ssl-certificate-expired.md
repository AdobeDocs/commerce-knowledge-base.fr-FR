---
title: 'Erreur cURL 60 : certificat SSL expiré'
description: 'Cet article montre comment vérifier à quel moment la dernière fois qu’une branche a été déployée après réception d’une erreur cURL 60 : le certificat SSL a expiré dans le Principal ou les branches d’intégration sur Adobe Commerce sur l’infrastructure cloud.'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Erreur cURL 60 : certificat SSL expiré

Cet article montre comment vérifier à quel moment la dernière fois qu’une branche a été déployée après réception d’une `cURL error 60` : [!DNL SSL certificate] a expiré dans les branches [!DNL Master] ou [!DNL Integration] d’Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, [toutes les versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Cause

Les [!DNL SSL certificates] de ces branches ne sont valides que pendant 30 jours et il se peut que la branche n’ait pas été redéployée au-delà de 30 jours.

L’erreur ressemblera à ceci :

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>Ces certificats ne sont pas signés par des autorités de certification externes (CA) connues telles que [!DNL Let's Encrypt] ou [!DNL DigiCert]. Ils sont gérés par la plateforme Adobe à des fins de test et de développement, et ne peuvent pas être approuvés par défaut dans les navigateurs ou les curls, sauf si vous faites explicitement confiance à la racine qui émet le certificat.

## Solution

Vérifiez la date du dernier déploiement de la branche. Si le délai est supérieur à 30 jours, redéployez la branche.

Deux méthodes permettant de vérifier quand le dernier déploiement a été effectué :

* [Méthode 1 : utiliser l [!DNL magento-cloud] interface de ligne de commande](#meth2).
* [Méthode 2 : ouvrez le  [!DNL Project URL]](#meth3).

Si le déploiement est terminé avec succès, la [!DNL SSL certificate] est automatiquement renouvelée.

Si le déploiement échoue et que vous avez besoin d’aide pour le résoudre, [soumettez un ticket d’assistance](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### Méthode 1 : utiliser l’interface de ligne de commande [!DNL magento-cloud] {#meth2}

Exécutez la commande suivante : `magento-cloud activity:list --type=environment.push`

### Méthode 2 : ouvrir le [!DNL Project URL] {#meth3}

Accédez à , par exemple : `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`, et vérifiez la date du dernier déploiement.

## Lecture connexe

Dans notre documentation destinée aux développeurs :

* [API Cloud Manager : certificats SSLC](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [Configuration rapide : attribution de certificats SSL/TLS](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

Dans notre base de connaissances du support :

* [Informations d’expiration du certificat SSL personnalisé](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [Certificats SSL (TLS) pour Adobe Commerce sur les infrastructures cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
