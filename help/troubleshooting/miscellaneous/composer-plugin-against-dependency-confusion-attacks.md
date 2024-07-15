---
title: Module externe du compositeur contre les attaques de confusion de dépendance
description: Cet article fournit des informations sur le module externe de compositeur publié pour les attaques de confusion de dépendance et des recommandations pour éviter l’erreur. Le module externe Composer a été introduit avec la version Adobe Commerce 2.4.3 pour protéger les marchands Adobe Commerce des attaques de Dependency Confusion.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Module externe du compositeur contre les attaques de confusion de dépendance

Cet article fournit des informations sur le module externe de compositeur publié pour les attaques de confusion de dépendance et des recommandations pour éviter l’erreur. Le module externe Composer a été introduit avec la version Adobe Commerce 2.4.3 pour protéger les marchands Adobe Commerce des attaques de Dependency Confusion.

## Produits et versions concernés

* Adobe Commerce 2.4.3 et versions futures (toutes les méthodes de déploiement)

## Problème

Un cas potentiel d’attaque de confusion de dépendances active est détecté par au moins une des dépendances directes ou indirectes définies dans `composer.json` par le module externe de compositeur `magento/composer-dependency-version-audit-plugin` lors de l’installation/de la mise à jour du compositeur.

<u>Étapes à reproduire</u> :

Lorsque vous installez/mettez à jour le compositeur, le module externe du compositeur arrête le processus s’il détecte une attaque de confusion de dépendance potentielle. Dans ce cas, l’installation/la mise à jour du compositeur échoue avec un message d’erreur similaire à :

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## Cause

L’attaque de confusion de dépendance permet d’exécuter à distance du code arbitraire sur un serveur en dupliquant un gestionnaire de dépendances (par exemple, le compositeur de PHP) pour télécharger un package malveillant à partir d’une source publique au lieu du package d’origine à partir d’un référentiel privé.

Une telle attaque peut même ne pas être détectée si un attaquant est en mesure de maintenir la fonctionnalité du package d&#39;origine.

Les attaquants peuvent exploiter cette vulnérabilité si un package n&#39;est disponible que par le biais de référentiels privés, mais n&#39;est pas enregistré dans le référentiel public. L&#39;attaquant charge ensuite un package portant le même nom dans le référentiel public et lui donne une version supérieure à celle disponible en privé. Le gestionnaire de dépendances comparera ensuite les versions des modules disponibles à la fois publiquement et en privé et choisira la version la plus élevée dans le référentiel public. Le code malveillant téléchargé par le gestionnaire de dépendances est ensuite exécuté avec les mêmes privilèges que le code de l’application.

## Solution

### Recommendations aux marchands

* Prenez le message d’erreur affiché lorsque le module externe arrête l’installation/la mise à jour du compositeur au sérieux, et contactez le développeur de l’extension si vous reconnaissez le module potentiellement compromis.
* Vous pouvez toujours installer Adobe Commerce avec la version sécurisée du module à partir de Marketplace ou d’un autre référentiel privé de confiance.
* Remplacez la version de package requise dans votre fichier compositeur.json par la version exacte trouvée dans le Marketplace afin de poursuivre l’installation/la mise à jour du compositeur.

### Attentes des développeurs d’extensions

* Il n’existe aucun moyen de savoir avec certitude si le package d’un module externe, s’il provient d’un référentiel public, a été compromis ou non. Le module externe détecte lorsqu’une version publique d’un module à l’adresse packagist.org a une version supérieure à celle disponible dans un référentiel privé comme [repo.magento.com](https://repo.magento.com). Nous recommandons fortement aux développeurs d’extensions d’éviter de telles situations et de ne pas publier de versions plus récentes publiquement que celles disponibles via [repo.magento.com](https://repo.magento.com).
* Adobe Commerce sait que le processus de révision de Marketplace peut retarder la disponibilité des extensions, mais le processus est là pour protéger les commerçants et aider les développeurs d’extensions à trouver des erreurs accidentelles qu’ils auraient pu manquer.
