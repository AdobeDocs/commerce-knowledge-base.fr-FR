---
title: Échec du déploiement avec les clés d’accès correctes dans env:COMPOSER_AUTH ou auth.json
description: 'Cet article fournit une solution au problème en cas d’échec du déploiement avec l’erreur suivante : "Le fichier https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip n’a pas pu être téléchargé (HTTP/1.1 404 Not Found)".'
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 7804e7094fb05d1cce9747c8f96c3cfe6bc6171e
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Échec du déploiement avec les clés d’accès correctes dans env:COMPOSER_AUTH ou auth.json

Cet article fournit une solution au problème lorsque votre déploiement échoue avec une erreur telle que celle ci-dessous, dans la variable [log de déploiement](/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log):

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.4.x

## Problème

<u>Étapes à reproduire</u>:

Tentative de déploiement.

<u>Résultats attendus</u>:

Déploiement réussi.

<u>Résultats réels</u>:

>[!NOTE]
>
>Il s’agit d’un exemple d’erreur. Une erreur peut s’afficher, indiquant un fichier différent (selon la version d’Adobe Commerce que vous déployez).

Vous ne déployez pas correctement. Une erreur telle que *Impossible de télécharger le fichier &quot;https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip&quot; (HTTP/1.1 404 Not Found)* dans le [log de déploiement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).


### Cause

Les clés d’accès au compositeur spécifiées trouvées dans l’un de ces emplacements peuvent ne pas avoir accès au code :

* dans le `env:COMPOSER_AUTH` au niveau du projet.
* dans le `auth.json file`, qui prévaut sur la variable `env:COMPOSER_AUTH` Variable .

### Solution

Mettez à jour le `env:COMPOSER_AUTH` au niveau du projet et assurez-vous qu’il est configuré avec des clés ayant accès au code.

Pour connaître les étapes, voir [Niveaux de variable](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/variable-levels) dans le guide d’infrastructure de Commerce on Cloud.

## Lecture connexe

* [Impossible d’accéder à Adobe Commerce sur le référentiel cloud : erreur 403 Forbidden ou 404 Not Found lors du déploiement](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [Erreur de déploiement : erreur 7 lors du téléchargement ... port 443 : connexion refusée](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce)
