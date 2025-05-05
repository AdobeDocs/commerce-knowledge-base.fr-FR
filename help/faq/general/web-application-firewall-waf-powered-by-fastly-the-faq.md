---
title: 'Web Application Firewall (WAF) (pare-feu d’applications web) avec technologie Fastly : la FAQ'
description: Les pare-feu d’applications web (WAF) empêchent le trafic malveillant d’entrer sur les sites et les réseaux en filtrant le trafic par rapport à un ensemble de règles de sécurité. Le trafic qui déclenche l’une des règles est bloqué avant qu’il puisse endommager vos sites ou votre réseau.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: f384ff9d5d8a8c5c5da20b582c02a2d783b32d7e
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 0%

---

# Web Application Firewall (WAF) (pare-feu d’applications web) avec technologie Fastly : FAQ

## Comment fonctionne le mode WAF du cloud géré par Adobe Commerce (optimisé de manière Fastly) ?

Les pare-feu d’applications web (WAF) empêchent le [trafic malveillant](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) d’accéder aux sites et aux réseaux en filtrant le trafic par rapport à un ensemble de règles de sécurité. Le trafic qui déclenche l’une des règles est bloqué avant qu’il puisse endommager vos sites ou votre réseau.

Adobe Commerce cloud WAF fournit une stratégie WAF avec un ensemble de règles conçu pour protéger vos applications web Adobe Commerce d’un large éventail d’attaques.

Le WAF examine le trafic Web et administratif pour identifier toute activité suspecte. Il évalue le trafic de GET et de POST (appels API HTTP) et applique l’ensemble de règles pour déterminer le trafic à bloquer. La WAF peut bloquer un large éventail d’attaques, y compris des attaques par injection SQL, des attaques par script intersite, des attaques par exfiltration de données et des violations de protocole HTTP.

En tant que service basé sur le cloud, le WAF ne nécessite aucun matériel ou logiciel à installer ou à gérer. Rapidement, un partenaire technologique existant, fournit le logiciel et l&#39;expertise. Leur WAF haute performance et toujours active réside dans chaque noeud de cache sur le réseau de diffusion global de Fastly.

## Le WAF est-il disponible pour tous les clients cloud ?

Oui, le service cloud WAF est inclus dans votre abonnement à l’infrastructure cloud d’Adobe Commerce pour l’architecture de plan de démarrage de l’infrastructure cloud d’Adobe Commerce et les plans d’architecture de plan d’Adobe Commerce on cloud infrastructure Pro, sans frais supplémentaires. Le service WAF est disponible dans les environnements de production et d’évaluation.

## Le WAF est-il conforme aux exigences de la norme PCI DSS 6.6 ?

Oui.

## Si mon compte Adobe Commerce sur l’infrastructure cloud gère des sites sur plusieurs domaines, le profil WAF est-il réglé pour chaque domaine ou collectivement pour tous les domaines ?

Le fichier WAF est réglé collectivement pour tous les domaines sous un compte cloud unique.

## Quelles règles sont utilisées pour le WAF ?

Le jeu de règles dans le profil WAF appliqué à votre environnement de production Adobe Commerce sur l’infrastructure cloud repose sur le jeu de règles OWASP Top 10 de protection des menaces, qui couvre les exploits courants des services web. Il contient également des règles spécifiques à Adobe Commerce développées par TrustWave SpiderLabs. L’équipe de recherche sur la sécurité de Fastly a également ajouté des règles qui protègent votre site et votre réseau contre les attaques communément connues : les adresses IP erronées, les agents utilisateur défaillants, ainsi que les noeuds de commande et de contrôle botnet connus. Nous activons des règles au niveau de paranoïa 3 OWASP ou moins, ce qui offre une couverture de haute sécurité.

## Comment accéder aux journaux ?

Pour que les journaux soient envoyés à votre outil de journalisation, demandez à votre gestionnaire de compte technique (TAM) d’ajouter un point de terminaison de journalisation dans Fastly.

## À quoi ressemble une requête bloquée ?

Une requête bloquée renvoie une page 403 avec un identifiant de requête.

Vous pouvez personnaliser cette page tant que la personnalisation comprend l’identifiant de requête. Pour plus d’informations, contactez votre gestionnaire de compte technique.

## Comment mettre à jour les ensembles de règles WAF ? À quelle vitesse une règle WAF peut-elle être modifiée ou mise à jour et appliquée globalement en production ?

Dans le cadre du service cloud WAF, gère rapidement les mises à jour des règles provenant de tiers commerciaux, effectue des recherches rapides et opère des sources ouvertes. Ils mettent à jour les règles publiées dans une stratégie selon les besoins ou lorsque des modifications apportées aux règles sont disponibles à partir de leurs sources respectives. Les nouvelles règles correspondant aux classes de règles publiées sont également insérées dans l’instance WAF de tout service une fois qu’elle est activée. Cela permet d’assurer une couverture immédiate des exploits nouveaux ou en évolution. Vous pouvez consulter les informations [ sur les mises à jour et la maintenance des règles ](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) sur le site de documentation Fastly.

## En quoi la solution cloud WAF d’Adobe Commerce diffère-t-elle des offres Fastly de la solution WAF à ses clients directs ?

La solution WAF vendue directement par Fastly est une offre payante qui comprend des ensembles de règles plus larges et des fonctionnalités supplémentaires telles que la personnalisation des règles et la protection contre les logiciels malveillants. La solution cloud WAF d’Adobe Commerce comprend un sous-ensemble de règles ciblées sur l’application Adobe Commerce et n’inclut qu’un seul jeu de règles pour l’environnement de production de chaque client.

## Quels types de menaces de sécurité la WAF protège-t-elle ?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">Menace</th>
<th style="width: 497.5px; text-align: left;">Protection WAF</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">attaques par injection SQL ;</td>
<td style="width: 497.5px;">Le jeu de règles principal OWASP ModSecurity et le jeu de règles commerciales TrustWave incluent tous deux des filtres spécifiques pour les attaques par injection SQL et ses variantes.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Injection intersite</p>
</td>
<td style="width: 497.5px;">Le jeu de règles OWASP protège des attaques par injection intersites. tire rapidement parti d’un mécanisme de notation pour chaque requête recherchant une injection intersite et d’autres menaces à l’origine. Nous évaluons chaque requête par rapport à l’ensemble de règles de base et nous vérifions que le score de la requête est inférieur à un seuil configurable pour qu’elle soit satisfaite.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Les attaques de force brutales</td>
<td style="width: 497.5px;">Couvert par le jeu de règles OWASP. De plus, bloque très vite l’activité de force brute en utilisant du code VCL qui reconnaît des sources, des demandes ou des tentatives spécifiques de force brute ou d’écrasement des contrôles de sécurité avant tout trafic atteignant le centre de données d’origine.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attaques réseau</td>
<td style="width: 497.5px;">Les attaques réseau, ou attaques ciblant l’infrastructure réseau, sont gérées automatiquement par Fastly. Fastly ne transmet pas le DNS à l’origine, et le trafic qui ne correspond pas à un profil HTTP, HTTPS ou DNS étroit est ignoré à la périphérie du réseau. Les attaques ciblant les protocoles de contrôle sont défendues par l’authentification des points de terminaison sur tout le réseau. De plus, les protocoles réseau utilisés dans le réseau Fastly sont durcis pour s'assurer qu'ils ne peuvent pas être utilisés comme amplification ou réflexion. Les clients sont chargés de la protection contre les attaques qui contournent le réseau Fastly en exploitant l’espace d’adresse IP Fastly Cache, publié pour nos clients en tant que composant de notre service CDN. Il est recommandé que l’espace d’adresse IP d’origine ne soit pas publié dans le DNS public pour s’assurer que les attaques de contournement ne puissent pas utiliser ces adresses comme cibles.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attaques d’injection JavaScript</td>
<td style="width: 497.5px;">Les règles WAF protègent contre l’insertion de code JavaScript malveillant dans les communications client avec les services web. Les schémas ou scores d’exploitation courants sont filtrés par le biais de la méthode WAF pour garantir l’intégrité du service d’origine.</td>
</tr>
</tbody>
</table>

## Des fonctionnalités supplémentaires sont-elles proposées ?

L’offre WAF d’Adobe Commerce comprend une protection contre les menaces OWASP Top-10 dans le cadre des exigences PCI, une prise en charge 24h/24 et 7j/7, notamment le triage des faux positifs et les mises à niveau de version. Les fonctionnalités suivantes ne sont pas prises en charge dans l’offre standard :

* limitation de débit
* personnalisation des règles
* atténuation des robots
* protection malveillante

## Comment les performances de mon site sont-elles affectées par le WAF ?

Une latence estimée entre 1,5 millisecondes (ms) et 20 ms est introduite pour chaque requête non mise en cache.

## Les clients peuvent-ils créer et modifier des listes noires d’adresses IP pour bloquer le trafic ?

Oui, les clients peuvent activer le blocage par pays et la liste de contrôle d’accès (ACL) à partir d’Adobe Commerce sur l’interface utilisateur d’administration de l’infrastructure cloud. Utilisez ces fonctionnalités lorsque vous souhaitez bloquer l’accès des visiteurs provenant de pays spécifiques ou de certaines adresses IP ou plages d’adresses IP. Si vous souhaitez que les visiteurs bloqués voient une page personnalisée plutôt qu’un code d’erreur, vous pouvez créer une page d’erreur personnalisée en chargeant l’HTML dans le menu Configuration rapide . Voir [Création d’une page d’erreur/de maintenance personnalisée](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr) dans la documentation destinée aux développeurs.

## Où puis-je vérifier le statut opérationnel de mon service WAF ?

La disponibilité générale du service WAF est signalée sur la [page d’état Fastly](https://status.fastly.com/). La création de rapports de disponibilité pour le WAF de chaque client n’est pas fournie.

## Adobe Commerce fournit-il la gestion des incidents pour le service WAF ?

Pour l’instant, la gestion des incidents n’est pas proposée.

## Adobe Commerce possède-t-il un centre des opérations de sécurité ?

Bien qu’Adobe Commerce ne dispose pas d’un Centre des opérations de sécurité, nous disposons d’un processus d’opérations de sécurité qui nous permet de mobiliser les ressources appropriées pour répondre aux incidents de sécurité en temps réel. Nous offrons également 24/7/365 support au soleil.

Vous pouvez également obtenir des informations de sécurité et des mises à jour relatives à Adobe Commerce à partir du [Centre de sécurité](https://helpx.adobe.com/fr/security.html).

## Quelle assistance est disponible ?

L’assistance WAF offre les ressources suivantes pour vous aider à atténuer l’impact des demandes indésirables ou malveillantes sur les services :

* Intégration : activation, configuration initiale et surveillance limitée du ou des services Fastly qui prennent en charge la gestion du cloud géré Adobe Commerce.
* Tirage faux positif continu pour répondre aux instances où le WAF bloque le trafic légitime
* Configuration de toute nouvelle règle standard introduite dans le cadre des mises à niveau de version de WAF

Pour obtenir des informations d’assistance supplémentaires, notamment des définitions de la gravité, des délais de réponse, des canaux et la disponibilité, reportez-vous aux termes [Cloud SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) .

## Si le WAF bloque le trafic légitime ou pose d&#39;autres problèmes, comment puis-je obtenir de l&#39;aide ?

[Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) au [Centre d’aide Adobe Commerce](https://support.magento.com). Veuillez indiquer que le ticket est lié au service WAF et inclure l’identifiant de la demande bloquée (ID).

Le système de tickets d’assistance Adobe Commerce effectue le suivi de la communication entre nos ingénieurs et le personnel d’un client. Ce système fournit une transcription horodatée des communications et envoie des emails au client et au personnel d’Adobe Commerce au fur et à mesure que les tickets sont mis à jour.

Pour tous les incidents envoyés en ligne, la réception des incidents sera confirmée par le système de tickets du Centre d’assistance clientèle d’Adobe Commerce. À la réception d&#39;un incident correctement soumis, les services de soutien doivent être hiérarchisés conformément aux niveaux de priorité décrits ci-dessus.

Le tableau suivant récapitule les canaux d’assistance et la disponibilité de la prise en charge de la fonction WAF :

<table class="table-basic">
<tbody>
<tr>
<th>Offre d’assistance</th>
<th>Détails</th>
</tr>
<tr>
<td>Aide en libre-service en ligne</td>
<td>Accès illimité</td>
</tr>
<tr>
<td>Disponibilité des rapports d’incident</td>
<td>24/7</td>
</tr>
<tr>
<td>Portail web</td>
<td>Disponible via Zendesk</td>
</tr>
<tr>
<td>Réaffectation d’urgence*</td>
<td>Reportez-vous à l'article <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html?lang=fr">hotline de notification Adobe Commerce P1</a> pour les numéros US et internationaux.</td>
</tr>
</tbody>
</table>

*\* La ligne téléphonique d’assistance sans frais d’Adobe Commerce est réservée aux incidents de priorité 1 uniquement. Les appels non prioritaires 1 ralentiront la réponse globale aux problèmes*

## Comment les faux positifs sont-ils triés ?

Nous avons un processus de triage faux positif (disponible 24h/24, 7j/7) pour traiter et résoudre rapidement les instances où les demandes légitimes ont déclenché une règle WAF. Les événements faux positifs sont traités comme des problèmes de priorité 1. Par défaut, notre équipe d’assistance peut mettre à jour la stratégie WAF immédiatement afin de désactiver la règle qui a déclenché l’événement de blocage et permettre à la demande légitime de passer par le WAF.

## Que se passe-t-il si le trafic vers la section d’administration d’Adobe Commerce sur le site de l’infrastructure cloud déclenche des règles WAF ? La prise en charge d’Adobe Commerce résoudra-t-elle les problèmes liés au trafic administrateur bloqué ?

Oui, le trafic d’administration bloqué est traité comme un problème de priorité 1.
