---
title: FAQ sur la fin de la prise en charge des logiciels Adobe Commerce
description: Le FAQ suivant a pour but d’aider les marchands, les développeurs et les partenaires à comprendre les implications de la date de fin de prise en charge (EOS) publiée par Adobe Commerce pour les versions concernées d’Adobe Commerce.
exl-id: ec147307-46eb-4a3a-8572-a014b091c58a
feature: Best Practices, Compliance, Console
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 0%

---

# FAQ sur la fin de la prise en charge des logiciels Adobe Commerce

Le FAQ suivant a pour but d’aider les marchands, les développeurs et les partenaires à comprendre les implications de la date de fin de prise en charge (EOS) publiée par Adobe Commerce pour les versions concernées d’Adobe Commerce.

## Dispositions générales

### Où puis-je trouver les dates de prise en charge des logiciels pour toutes les versions d’Adobe Commerce ?

Vous trouverez la politique de cycle de vie du logiciel Adobe Commerce et les dates de prise en charge logicielle dans la section [Stratégie de cycle de vie des logiciels Adobe Commerce](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf). Nous publions également des dates de fin de prise en charge (EOS) sur notre [page de documentation destinée aux développeurs](https://devdocs.magento.com/release/released-versions.html).

### Qu’est-ce que cela signifie lorsque l’Adobe met fin à la prise en charge d’une version du logiciel Adobe Commerce ?

Lorsque Adobe met fin à la prise en charge d’une version de son logiciel Adobe Commerce, vous pouvez vous attendre à ce que les conditions suivantes soient remplies :

* Adobe Commerce ne créera plus de modifications de produit supplémentaires pour cette version (y compris les modifications fonctionnelles, de qualité, de sécurité et de conformité PCI).
* Les demandes d’extraction de la communauté ne seront plus acceptées ni fusionnées pour la version d’EOS. Les extensions du Commerce Marketplace qui ne sont compatibles qu’avec les versions non prises en charge d’Adobe Commerce seront supprimées.
* La documentation en ligne des versions non prises en charge sera supprimée (par exemple, les documents de développement).
* Les tickets d’assistance envoyés après la fin de la prise en charge d’une version d’Adobe Commerce ne seront pas résolus (vous trouverez plus d’informations sur l’assistance technique ci-dessous).

### Quelles sont les implications pour les commerçants qui utilisent des logiciels Adobe Commerce non pris en charge ?

Nous vous recommandons vivement de n’utiliser que des logiciels pris en charge.

Si vous décidez de continuer à utiliser un logiciel dont la prise en charge est terminée, vous ne recevrez plus de mises à jour importantes de produits ou de support technique, qui inclut souvent les dernières mises à jour de sécurité. L’utilisation de logiciels non pris en charge peut avoir un impact sur les domaines suivants :

**Offrir des expériences d’achat sécurisées :**

* Vous devrez dépenser des ressources pour évaluer et employer des fournisseurs tiers afin de fournir une assistance en matière de sécurité, des correctifs et des mises à jour.
* Une fois qu’une version du logiciel Adobe Commerce n’est plus prise en charge, cette version n’est plus [Compatibilité PCI](https://www.pcisecuritystandards.org/pci_security/maintaining_payment_security). Dans ce cas, vous risquez d’être soumis à des amendes, de perdre votre capacité de traitement de carte de crédit ou à d’autres pénalités.
* Comme la plupart des exploits ont tendance à cibler les installations qui ne sont pas à jour avec les dernières mises à jour de sécurité, nous recommandons toujours aux commerçants de garder leurs logiciels à jour et d’installer les mises à jour de sécurité dès qu’elles sont disponibles. Il appartient au marchand de préserver la sécurité de sa boutique en ligne grâce à des protections et des contrôles de sécurité adéquats pour protéger son site web et les données personnelles de ses clients. Pour ce faire, l’une des meilleures méthodes consiste à installer les derniers correctifs, correctifs et mises à jour logicielles, et à surveiller continuellement votre site et votre console d’administration pour détecter les activités inhabituelles.

**Fonctionnement efficace**

* En tant que versions non prises en charge de l’ère des logiciels Adobe Commerce, il existe un nombre décroissant de développeurs et de partenaires disponibles, capables de fournir une assistance pour les versions obsolètes lorsqu’elles orientent leurs opérations vers des technologies plus récentes. En règle générale, le nombre et la qualité des talents pour la maintenance des logiciels diminuent, tandis que les coûts de maintenance augmentent.
* Pour les logiciels Adobe Commerce non pris en charge, les technologies périphériques et les dépendances peuvent également atteindre leur propre fin de cycle de vie (par exemple, PHP, MYSQL, REDIS, SOLR). Cela rend de plus en plus difficile la gestion et la maintenance d’un site sécurisé et conforme.
* Les développeurs d’extensions mettent également davantage l’accent sur les technologies les plus récentes et les plateformes compatibles. Par conséquent, ils peuvent ne pas continuer à gérer les extensions pour les versions non prises en charge d’Adobe Commerce.
* L’utilisation de versions non prises en charge des logiciels Adobe Commerce entraîne souvent une augmentation des dépenses et des ressources pour la maintenance d’une ancienne plateforme, au lieu d’appliquer ces ressources à l’innovation et à la croissance continues de l’entreprise.

**Croissance agressive**

* L&#39;Adobe continue d&#39;investir dans de nouvelles technologies et capacités. Grâce à la mise à jour des logiciels, vous pouvez tirer parti des nouvelles technologies et des nouvelles fonctionnalités qui peuvent aider votre entreprise à fonctionner de manière plus stratégique et à croître encore plus rapidement.

### Quels sont quelques exemples de la façon dont les commerçants peuvent tirer parti des nouvelles technologies en restant à jour avec leur logiciel Adobe Commerce ?

Il existe plusieurs façons de rester à jour sur votre logiciel Adobe Commerce :

* Outre la mise à jour de votre plateforme avec les dernières protections de sécurité, notamment la conformité PCI, la mise à niveau vers une version prise en charge peut améliorer les performances et l’évolutivité, ce qui vous permet d’accéder aux dernières innovations.
* Adobe Commerce 2.4.4, qui aura lieu le 12 avril 2022, marque une nouvelle étape en termes de fonctionnalités, de performances et de protection du commerce. Elle pose les bases pour les prochaines années d&#39;innovation Adobe qui aidera à la résilience des entreprises commerciales. Basée sur la version la plus récente de PHP 8.1, la dernière version permet aux marchands de protéger leurs commerces numériques à l’avenir avec :
   * Accès plus rapide aux fonctionnalités innovantes proposées sous la forme de services SaaS, tels que Recommendations de produit, Services de paiement et Recherche en direct
   * Maintenance et mises à niveau plus simples et plus rentables
   * Flexibilité continue pour personnaliser et répondre aux besoins uniques de l’entreprise
   * Augmentation significative des performances et de l’évolutivité
   * Amélioration de l’expérience des développeurs et des outils pour surveiller l’intégrité de la plateforme

### Que dois-je faire pour éviter les problèmes de prise en charge des logiciels ?

Votre plateforme commerciale est un système commercial important pour votre entreprise et rester à jour et à jour est un investissement essentiel dans l’entreprise. Les dernières technologies et mises à jour de sécurité de votre vitrine numérique sont importantes à de nombreux niveaux et peuvent contribuer à améliorer les innovations et la croissance.

Le passage à la dernière version du logiciel Adobe Commerce peut nécessiter du temps et des ressources pour s’exécuter correctement. Il est recommandé de planifier au plus tôt la date de fin de l’assistance afin de vous assurer que vous disposez du temps et des ressources nécessaires pour atteindre vos objectifs stratégiques dans les délais et dans les limites du budget. Pour vous aider à effectuer votre prochaine mise à niveau, Adobe a publié la [2.4 Guide de mise à niveau](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) qui comprend les bonnes pratiques et les étapes techniques à suivre, ainsi que les outils et ressources à utiliser lors de la mise à niveau.

Il est également important de réserver les ressources des développeurs et des partenaires le plus tôt possible. Le temps passé par les partenaires et les ressources sont souvent réservés bien avant la date de fin de l’assistance, ce qui entraîne une diminution significative des ressources destinées à assister les projets de migration. Il est recommandé d’avoir un plan variable de trois ans dont vous discutez chaque année au minimum et de vous assurer que l’année suivante est planifiée et budgétée. Utilisation [Calendrier des versions d’Adobe](https://devdocs.magento.com/release/) pour effectuer le suivi des dates de publication.

### Puis-je utiliser un fournisseur de services tiers pour la prise en charge des logiciels lorsque la prise en charge d’Adobe Commerce cesse ?

Oui, vous pouvez rechercher des entreprises de sécurité, des développeurs ou des partenaires qui prendront en charge les versions non prises en charge d’Adobe Commerce. Il vous appartiendra d’évaluer ces fournisseurs, de certifier à nouveau la conformité si nécessaire, ainsi que d’identifier et de résoudre les menaces de sécurité persistantes susceptibles d’affecter votre entreprise et vos clients.

### J’ai une licence pour Adobe Commerce qui s’étend au-delà de la date de fin de prise en charge indiquée pour cette version. Adobe continuera-t-il à fournir une prise en charge logicielle de ma version non prise en charge tout au long de ma licence si je choisis de ne pas passer à une version prise en charge ?

La licence Adobe Commerce vous donne le droit d’accéder aux versions d’Adobe Commerce disponibles en général et de les utiliser, y compris pour accéder à des versions non prises en charge et les utiliser. Que votre version de logiciel soit prise en charge ou non, vous devez continuer à utiliser les logiciels Adobe Commerce et à être à jour avec les frais de licence actuels. Cela se termine à la fin de votre contrat Adobe Commerce.

Une licence Adobe Commerce ne fournit pas de prise en charge logicielle pour les versions qui ont atteint et dépassé leur date de fin de prise en charge. Surtout, si vous restez sur des logiciels non pris en charge, vous devrez gérer et payer vos propres correctifs de sécurité et la re-certification de conformité PCI et vous assumerez probablement des risques et des responsabilités supplémentaires en matière de sécurité.

### Une version logicielle est-elle &quot;arrêtée&quot; lorsqu’elle atteint et dépasse sa date de fin de prise en charge ?

Non, le logiciel Adobe Commerce n’est pas &quot;arrêté&quot; une fois la date de fin de prise en charge atteinte ou dépassée. Votre licence reste valide même pour les logiciels Adobe Commerce non pris en charge tant que votre compte est en règle, mais vous serez responsable de la certification de conformité PCI et ne pourrez plus déposer de tickets d’assistance. Plus important encore, vous ne recevrez plus de correctifs de sécurité qui permettent de protéger votre storefront numérique.

### Puis-je continuer à utiliser le logiciel Adobe Commerce une fois ma licence expirée ?

Une fois votre licence Adobe Commerce expirée, vous devez cesser d’utiliser le logiciel Adobe Commerce et supprimer toutes les versions de ce logiciel. Tant que votre compte est en règle, la licence Adobe Commerce vous donne le droit d’accéder aux versions d’Adobe Commerce disponibles en général et de les utiliser.

## provisions techniques

### Les tickets de support qui ont été ouverts AVANT la date de fin de prise en charge d’une version logicielle continueront-ils à être résolus même après l’expiration de la date de fin de prise en charge ?

Oui, les tickets d’assistance ouverts avant la date de fin de prise en charge d’une version logicielle continueront à être traités et résolus même si la date de fin de prise en charge de cette version logicielle est dépassée. Cependant, la résolution des tickets de support peut dépendre du fait que la résolution repose sur des composants hors contrôle d’Adobe Commerce (c’est-à-dire PHP, jQuery, etc.). ayant expiré ou atteint la fin de la prise en charge. Dans ces cas, le ticket de support peut être résolu en vous demandant de mettre à niveau vers la dernière version.

### Si j’ouvre un ticket pour une version de logiciel dont la prise en charge logicielle prend bientôt fin, l’Adobe donnera-t-il la priorité à ces tickets afin qu’ils soient résolus avant la date de fin de prise en charge ?

Non, Adobe ne reclasse pas les tickets d’assistance en fonction de la date de fin de prise en charge de ces versions de logiciels. Les tickets d’assistance sont adressés en fonction des algorithmes internes dérivés de la raison de contact, de l’environnement et de l’impact sur l’entreprise du ticket.

### Pour les tickets d’assistance ouverts AVANT la date de fin de la prise en charge, existe-t-il une alerte pour rappeler aux marchands la fin de la prise en charge à venir ?

Non, il n’existe aucune alerte de rappel informant les utilisateurs de tickets d’assistance des dates de fin de prise en charge à venir. Il est de la responsabilité de l’utilisateur de connaître les dates de fin de prise en charge de la version d’Adobe Commerce sur laquelle il se trouve, qui se trouvent sur notre [Stratégie de cycle de vie des logiciels Adobe Commerce](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

### Si un ticket de support pour une version de logiciel est ouvert APRÈS la date de fin de prise en charge pour cette version, sera-t-il toujours résolu ?

Non, Adobe Commerce ne fonctionnera pas pour résoudre les demandes d’assistance qui ont été ouvertes après la date de fin de la prise en charge pour cette version logicielle.
