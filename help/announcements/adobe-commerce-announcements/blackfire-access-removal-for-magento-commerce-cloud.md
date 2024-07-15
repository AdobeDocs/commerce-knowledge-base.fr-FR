---
title: Suppression de l’accès des Blackfire pour Adobe Commerce sur l’infrastructure cloud
description: À compter du 11 avril 2020, le libre accès à la surveillance des performances des Blackfire ne sera plus inclus avec l’architecture du plan Adobe Commerce sur l’infrastructure cloud Pro ou avec les abonnements à l’architecture du plan de démarrage de l’infrastructure cloud.  Vous ne pourrez plus vous connecter à votre compte de Blackfire. Il est possible de continuer à utiliser Blackfire au-delà du 11 avril en achetant une licence directement via Blackfire.io. Les marchands Adobe Commerce qui n’ont pas acheté de licences directement auprès de Blackfire à cette date verront leurs licences Blackfire gratuites, fournies par Adobe, désactivées. De plus, la fonctionnalité de création de rapports à l’aide de l’outil de profileur sera désactivée. Il est toujours possible pour les clients utilisant l’architecture Pro hébergés sur l’infrastructure cloud de recevoir une surveillance gratuite des performances de l’infrastructure via l’infrastructure New Relic.
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Suppression de l’accès des Blackfire pour Adobe Commerce sur l’infrastructure cloud

À compter du 11 avril 2020, le libre accès à la surveillance des performances des Blackfire ne sera plus inclus avec l’architecture du plan Adobe Commerce sur l’infrastructure cloud Pro ou avec les abonnements à l’architecture du plan de démarrage de l’infrastructure cloud.  Vous ne pourrez plus vous connecter à votre compte de Blackfire. Il est possible de continuer à utiliser Blackfire au-delà du 11 avril en achetant une licence directement via Blackfire.io. Les marchands Adobe Commerce qui n’ont pas acheté de licences directement auprès de Blackfire à cette date verront leurs licences Blackfire gratuites, fournies par Adobe, désactivées. De plus, la fonctionnalité de création de rapports à l’aide de l’outil de profileur sera désactivée. Il est toujours possible pour les clients utilisant l’architecture Pro hébergés sur l’infrastructure cloud de recevoir une surveillance gratuite des performances de l’infrastructure via l’infrastructure New Relic.

**Si vous souhaitez continuer à utiliser Blackfire** :

1. Vous devez acheter directement une licence avec Blackfire.
1. Ensuite, configurez Blackfire à l’aide de ces [étapes](https://blackfire.io/docs/integrations/paas/magentocloud).
1. Si vous rencontrez des difficultés lors de l&#39;installation, vous pouvez [envoyer un ticket d&#39;assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) pour demander de l&#39;aide. Pour toute question spécifique au Blackfire, contactez l’assistance Blackfire directement à l’adresse [support@blackfire.io](mailto:support@blackfire.io).

## Si vous rencontrez des erreurs lors de l’exécution d’un déploiement :

Si, lors de l’exécution d’un déploiement, vous obtenez des erreurs liées à Blackfire, procédez comme suit :

1. Supprimez le Blackfire de votre configuration. Modifiez le fichier `.magento.app.yaml` et supprimez le Blackfire de la section runtime :

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. Effectuez cette opération dans l’environnement de développement local et remontez jusqu’au cloud.

Seul [soumettez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) si l’erreur suivante s’affiche après l’exécution d’un déploiement :

*Avertissement PHP : Démarrage de PHP : impossible de charger la bibliothèque dynamique &#39;blackfire.so&#39; (tentative : /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so : impossible d’ouvrir le fichier d’objet partagé : pas de fichier ou de répertoire de ce type), /usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so : impossible d’ouvrir le fichier d’objet partagé : pas de fichier ou de répertoire de ce type) dans Inconnu sur la ligne 0*

Cette erreur signifie que le module Blackfire doit être mis à jour et qu’il ne doit pas être chargé.

**Si vous souhaitez utiliser l’infrastructure New Relic** :

Pour savoir comment accéder à l’infrastructure New Relic, reportez-vous à la section [Accès à New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) de notre base de connaissances d’assistance.
