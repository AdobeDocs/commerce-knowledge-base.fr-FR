---
title: La base de connaissances du support Adobe Commerce commence à accepter des contributions
description: À compter du 15 juin, l’équipe de la base de connaissances d’assistance d’Adobe Commerce commencera à accepter les modifications directes et les nouvelles contributions aux articles de la communauté Adobe Commerce externe par le biais du [magento/Knowledge-base](https://github.com/magento/knowledge-base) référentiel GitHub!
exl-id: b5198de0-d6b5-4107-8b74-a12606583596
feature: Support
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# La base de connaissances du support Adobe Commerce commence à accepter des contributions

À compter du 15 juin, l’équipe de la base de connaissances du support Adobe Commerce commencera à accepter les modifications directes et les nouvelles contributions aux articles de la communauté Adobe Commerce externe par le biais de la [magento/base de connaissances](https://github.com/magento/knowledge-base) Référentiel GitHub !

Vous avez remarqué une faute de frappe dans l’un de nos articles ou une procédure de dépannage incomplète ?
Vous pouvez désormais le corriger vous-même et obtenir des points de contribution.

## Contribution

Nous acceptons toutes sortes de contributions, allant des corrections de type mineures aux articles de dépannage complets. Contribuer à ce référentiel vous donne des points de récompense, comme contribuer au code Adobe Commerce et à notre documentation destinée aux développeurs. Voir [Points de récompense des contributions](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) pour plus d’informations.

### Flux de contribution général

1. Branchez ce référentiel.
1. Apportez des modifications au référentiel dupliqué.
1. Envoyez une requête d’extraction (PR) à ce référentiel.
1. Les tests sont exécutés :
   * Adobe CLA : assurez-vous que le contrat de licence du contributeur Open Source de l’Adobe est signé.
   * Test de liaison Markdown : assurez-vous que la syntaxe Markdown est correcte.
   * Test de validation de la structure de fichier : assurez-vous que la validation est effectuée conformément aux [structure de fichier requise](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md#file_structure).
1. Flux d’approbations de relations publiques :
   1. Les rédacteurs de la base de connaissances de support (KB) examinent les relations publiques dans un délai de plusieurs jours et ajoutent des étiquettes.
   1. L’auteur de la base de connaissances peut approuver/refuser/demander des modifications.
   1. S’il est approuvé, l’auteur de la base de connaissances ajoute des étiquettes correspondant au niveau d’entrée fourni dans la communication et l’expert interne en matière de communication (SME) examine la communication.
   1. Les PME peuvent approuver/refuser/demander des modifications.
1. Une fois toutes les corrections effectuées (le cas échéant) et que l’auteur de la base de connaissances et le PME approuvent la communication, l’auteur de la base de connaissances importe le contenu dans le référentiel interne et le fusionne en interne.
1. La variable [magento/base de connaissances](https://github.com/magento/knowledge-base) repo se synchronise avec l’instance interne en 20 minutes.
1. Une fois les repos synchronisés, votre PR est fermé et vous obtenez [points de contribution](#contribution-points).

Pour plus d’informations sur le flux de contribution, reportez-vous à la section [Guide du contributeur](https://github.com/magento/knowledge-base/blob/main/.github/CONTRIBUTING.md).
Pour les modèles, le guide de style et les instructions de mise en forme, reportez-vous à la section [Documentation](https://github.com/magento/knowledge-base/tree/main/docs).

### Recherchez le fichier d’article de la base de connaissances d’assistance sur Github.

Dans la base de connaissances d’assistance, les articles sont organisés en sections qui s’imbriquent dans des catégories.

Par exemple, la variable [Comment s’abonner aux mises à jour d’état d’Adobe Magento](/help/how-to/general/how-to-subscribe-to-adobe-magento-status-updates.md) appartient à la section Général de la catégorie Comment .

Vous pouvez voir le nom de la section et de la catégorie dans le chemin de navigation de la page de l’article, voir l’image ci-dessous :

![chemins de navigation des catégories et des sections](assets/breadcrumbs.png)

Les fichiers d’article sont organisés de la même manière que dans [magento/base de connaissances](https://github.com/magento/knowledge-base) repo.
Tout le contenu est stocké dans la variable `src` avec des dossiers pour les catégories et des dossiers imbriqués pour les sections ; les noms de fichier correspondent aux titres des articles ou sont similaires.

Vous pouvez également utiliser la recherche dans le référentiel à l’aide d’un texte de l’article de la base de connaissances de l’assistance comme chaîne de recherche. Lorsque la recherche renvoie des fichiers, contenant cette chaîne, veillez à choisir le fichier qui appartient à la section et à la catégorie appropriées.

### Points de contribution

La variable [magento/base de connaissances](https://github.com/magento/knowledge-base) Référentiel intégré à l’ingénierie communautaire Magento pour les points de contribution et l’assistance.

Reportez-vous à [Points de contribution](https://github.com/magento/knowledge-base/blob/main/docs/contribution-points.md) pour voir comment les points sont récompensés.
