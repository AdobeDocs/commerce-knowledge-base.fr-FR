---
title: 'Pare-feu d’application web (WAF) optimisé par Fastly : FAQ'
description: Les pare-feu d'applications web (WAF) empêchent le trafic malveillant d'entrer sur les sites et les réseaux en filtrant le trafic par rapport à un ensemble de règles de sécurité. Le trafic qui déclenche l’une des règles est bloqué avant de pouvoir endommager vos sites ou votre réseau.
exl-id: d977ea68-7d8c-4863-b026-acdc25d8c430
feature: Cache
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '1655'
ht-degree: 0%

---

# Pare-feu d’application web (WAF) optimisé par Fastly : FAQ

## Comment Adobe Commerce managed cloud WAF (optimisé par Fastly) fonctionne-t-il ?

Les pare-feu d&#39;applications web (WAF) empêchent [le trafic malveillant](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) d&#39;accéder aux sites et aux réseaux en filtrant le trafic selon un ensemble de règles de sécurité. Le trafic qui déclenche l’une des règles est bloqué avant de pouvoir endommager vos sites ou votre réseau.

Adobe Commerce cloud WAF fournit une politique WAF avec un ensemble de règles conçu pour protéger vos applications web Adobe Commerce contre un large éventail d’attaques.

Le WAF examine le trafic Web et d’administration afin d’identifier toute activité suspecte. Il évalue le trafic GET et POST (appels d’API HTTP) et applique l’ensemble de règles pour déterminer le trafic à bloquer. Le WAF peut bloquer une grande variété d’attaques, notamment les attaques par injection SQL, les attaques de script entre sites, les attaques d’exfiltration de données et les violations de protocole HTTP.

En tant que service basé sur le cloud, le WAF ne nécessite aucun matériel ou logiciel à installer ou à gérer. Fastly, un partenaire technologique existant, fournit le logiciel et l&#39;expertise. Leur WAF hautes performances et toujours activé réside dans chaque nœud de cache du réseau mondial de diffusion de Fastly.

## Le WAF est-il disponible pour tous les clients cloud ?

Oui, le service Cloud WAF est inclus dans votre abonnement Adobe Commerce on cloud infrastructure pour les plans de démarrage de l’architecture Adobe Commerce on cloud infrastructure et Adobe Commerce on cloud infrastructure Pro plan architecture sans frais supplémentaires. Le service WAF est disponible dans les environnements de production et d’évaluation.

## WAF est-il conforme aux exigences PCI DSS 6.6 ?

Oui.

## Si mon compte d’Adobe Commerce sur l’infrastructure cloud gère des sites sur plusieurs domaines, le profil WAF est-il adapté à chaque domaine ou collectivement à tous les domaines ?

Le WAF est optimisé collectivement pour tous les domaines sous un seul compte cloud.

## Quelles sont les règles utilisées pour le WAF ?

L’ensemble de règles du profil WAF appliqué à votre environnement de production Adobe Commerce on cloud infrastructure est basé sur l’ensemble de règles des 10 meilleures menaces de protection OWASP, qui couvre les attaques courantes vers les services web. Il contient également des règles spécifiques à Adobe Commerce développées par TrustWave SpiderLabs. L&#39;équipe de recherche sur la sécurité de Fastly a également ajouté des règles qui protègent votre site et votre réseau contre les attaques courantes : adresses IP incorrectes, agents utilisateurs incorrects et nœuds de commande et de contrôle de réseau de robots connus. Nous activons les règles au niveau OWASP Paranoia 3 ou moins, qui fournit une couverture de haute sécurité.

## Comment puis-je accéder aux journaux ?

Pour que les journaux soient envoyés à votre outil de journalisation, contactez votre gestionnaire de compte technique (TAM) afin d’ajouter un point d’entrée de journalisation dans Fastly.

## À quoi ressemble une demande de blocage ?

Une requête bloquée renvoie une page 403 avec un identifiant de requête.

Vous pouvez personnaliser cette page à condition que la personnalisation inclue l’identifiant de requête. Contactez votre gestionnaire de compte technique pour plus d’informations.

## Comment mettre à jour les ensembles de règles de WAF ? À quelle vitesse une règle WAF peut-elle être modifiée ou mise à jour et appliquée globalement en production ?

Dans le cadre du service cloud WAF, Fastly gère les mises à jour de règles provenant de tiers commerciaux, de recherches Fastly et de sources ouvertes. Elles mettent à jour les règles publiées dans une politique selon les besoins ou lorsque des modifications des règles sont disponibles à partir de leurs sources respectives. De nouvelles règles correspondant aux classes de règles publiées sont également insérées dans l’instance WAF de n’importe quel service une fois qu’il est activé. Cela permet d’assurer une couverture immédiate des exploits nouveaux ou en évolution. Vous pouvez consulter des informations [sur les mises à jour et la maintenance des règles](https://docs.fastly.com/guides/web-application-firewall/fastly-waf-rule-set-updates-maintenance#rule-set-maintenance) sur le site de documentation Fastly .

## En quoi Adobe Commerce cloud WAF diffère-t-il de la solution WAF proposée par Fastly à ses clients directs ?

La solution WAF vendue directement par Fastly est une offre payante qui comprend des ensembles de règles plus larges et des fonctionnalités supplémentaires telles que la personnalisation des règles et la protection contre les programmes malveillants. La solution Adobe Commerce cloud WAF comprend un sous-ensemble de règles ciblant l’application Adobe Commerce et ne comprend qu’un seul ensemble de règles pour l’environnement de production de chaque client.

## Quels types de menaces de sécurité WAF protège-t-il ?

<table class="table-basic" style="width: 649px;">
<tbody>
<tr>
<th style="width: 145.5px; text-align: left;">Menace</th>
<th style="width: 497.5px; text-align: left;">Protection de WAF</th>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attaques par injection SQL</td>
<td style="width: 497.5px;">Le jeu de règles principal ModSecurity d’OWASP et le jeu de règles commerciales TrustWave incluent des filtres spécifiques pour les attaques par injection SQL et ses variantes.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">
<p>Injection transversale</p>
</td>
<td style="width: 497.5px;">L’ensemble de règles OWASP protège contre les attaques par injection intersite. Fastly utilise un mécanisme de notation pour chaque demande recherchant l’injection intersite et les autres menaces qui pèsent sur l’origine. Nous attribuons une note à chaque requête par rapport à l’ensemble des règles de base et nous vérifions que le score de la requête est inférieur à un seuil configurable pour qu’elle réussisse.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attaques par force brute</td>
<td style="width: 497.5px;">Couvert par l’ensemble de règles OWASP. Fastly bloque également l'activité de force brute en utilisant du code VCL qui reconnaît des sources spécifiques, des requêtes ou des tentatives de force brute ou de débordement des contrôles de sécurité avant tout trafic atteignant le centre de données d'origine.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attaques réseau</td>
<td style="width: 497.5px;">Les attaques réseau, ou attaques ciblant les infrastructures réseau, sont gérées automatiquement par Fastly. Fastly ne transmet pas le DNS à l’origine, et le trafic qui ne correspond pas à un profil HTTP, HTTPS ou DNS étroit est ignoré à la périphérie du réseau. Les protocoles de contrôle ciblant les attaques sont défendus par l'authentification des points d'entrée sur le réseau. En outre, les protocoles réseau utilisés au sein du réseau Fastly sont renforcés pour s’assurer qu’ils ne peuvent pas être utilisés comme un moyen d’amplification ou de réflexion. Les clients sont chargés de la protection contre les attaques qui contournent le réseau Fastly en exploitant l’espace d’adresse IP Fastly Cache, publié pour nos clients en tant que composant de notre service CDN. Il est recommandé de ne pas publier l’espace d’adresse IP d’origine dans le DNS public afin de s’assurer que les attaques par contournement ne peuvent pas utiliser ces adresses en tant que cibles.</td>
</tr>
<tr>
<td style="width: 145.5px; vertical-align: top;">Attaques par injection JavaScript</td>
<td style="width: 497.5px;">Les règles de WAF protègent contre l’insertion de code JavaScript malveillant dans les communications client avec les services web. Les modèles ou scores d’exploitation courants sont filtrés dans WAF afin de garantir l’intégrité du service d’origine.</td>
</tr>
</tbody>
</table>

## Des fonctionnalités supplémentaires sont-elles proposées ?

L’offre Adobe Commerce WAF inclut une protection contre les menaces du top 10 d’OWASP dans le cadre des exigences PCI, une prise en charge 24h/24 et 7j/7, y compris le triage des faux positifs et des mises à niveau de version. Les fonctionnalités suivantes ne sont pas prises en charge dans l’offre standard :

* limitation de débit
* personnalisations des règles
* atténuation des robots
* protection contre les programmes malveillants

## Comment les performances de mon site sont-elles affectées par le WAF ?

Une latence estimée entre 1,5 millisecondes (ms) et 20 ms est introduite dans chaque requête non mise en cache.

## Les clients peuvent-ils créer et modifier des listes de blocage IP pour bloquer le trafic ?

Oui, les clients peuvent activer le blocage par pays et par liste de contrôle d’accès (ACL) à partir de l’interface utilisateur d’administration d’Adobe Commerce sur les infrastructures cloud. Utilisez ces fonctionnalités si vous souhaitez bloquer l’accès des visiteurs provenant de pays spécifiques ou de certaines adresses IP ou plages d’adresses IP. Si vous souhaitez que les visiteurs bloqués voient une page personnalisée plutôt qu’un code d’erreur, vous pouvez créer une page d’erreur personnalisée en chargeant HTML dans le menu Configuration rapide . Consultez [Création d’une page d’erreur/de maintenance personnalisée](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans notre documentation destinée aux développeurs.

## Où puis-je vérifier l’état opérationnel de mon service WAF ?

La disponibilité globale du service WAF est indiquée sur la page [Fastly Status](https://status.fastly.com/). Les rapports de disponibilité pour le WAF de chaque client ne sont pas fournis.

## Adobe Commerce fournit-il la gestion des incidents pour le service WAF ?

Actuellement, la gestion des incidents n’est pas proposée.

## Adobe Commerce dispose-t-il d’un centre des opérations de sécurité ?

Bien qu’Adobe Commerce ne dispose pas d’un Centre des opérations de sécurité, nous disposons d’un processus d’opérations de sécurité qui nous permet d’engager les ressources appropriées pour répondre aux incidents de sécurité en temps réel. Nous offrons également un support 24h/24, 7j/7 et 365j/365.

Vous pouvez également obtenir des informations et des mises à jour de sécurité relatives à Adobe Commerce à partir du [Centre de sécurité](https://helpx.adobe.com/security.html).

## Quelle assistance est disponible ?

La prise en charge de WAF propose les ressources suivantes pour vous aider à atténuer l’impact sur les services des requêtes indésirables ou malveillantes :

* Intégration : activation, configuration initiale et surveillance limitée du ou des services Fastly qui prennent en charge le WAF Cloud géré par Adobe Commerce
* Tri faux positif en cours pour traiter les instances où le WAF bloque le trafic légitime
* Configuration de toutes les nouvelles règles standard introduites dans le cadre des mises à niveau de la version de WAF

Consultez les termes [Cloud SLA](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Magento-Support-Services-Terms-and-Conditions.pdf) pour obtenir plus d’informations sur l’assistance, notamment les définitions de gravité, les délais de réponse, les canaux et la disponibilité.

## Si le WAF bloque le trafic légitime ou provoque d’autres problèmes, comment puis-je obtenir de l’aide ?

[Envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) au [Centre d’aide Adobe Commerce](https://support.magento.com). Veuillez indiquer que le ticket est lié au service WAF et inclure l’identifiant de la requête bloquée (ID).

Le système de ticket d’assistance Adobe Commerce effectue le suivi de la communication entre nos ingénieurs d’assistance et le personnel d’un client. Ce système fournit une transcription horodatée des communications et envoie des e-mails au client et au personnel d’Adobe Commerce lorsque les tickets sont mis à jour.

Pour tous les incidents soumis en ligne, la réception des incidents sera confirmée via le système de ticket du Centre d&#39;aide clientèle d&#39;Adobe Commerce. À la réception d&#39;un incident correctement soumis, les services d&#39;assistance seront prioritaires conformément aux niveaux de priorité énoncés ci-dessus.

Le tableau suivant résume les canaux de prise en charge et la disponibilité pour la prise en charge de WAF :

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
<td>Disponibilité des rapports d'incident</td>
<td>24/7</td>
</tr>
<tr>
<td>Portail Web</td>
<td>Disponible via Zendesk</td>
</tr>
<tr>
<td>Escalade en cas d’urgence*</td>
<td>Reportez-vous à l’article <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/adobe-commerce-p1-notification-hotline.html">Hotline de notification P1 Adobe Commerce</a> pour obtenir des numéros américains et internationaux.</td>
</tr>
</tbody>
</table>

*\* La ligne téléphonique d’assistance sans frais d’Adobe Commerce est réservée aux incidents de priorité 1 uniquement. Les appels non prioritaires 1 ralentiront la réponse globale aux problèmes*

## Comment les faux positifs sont-ils triés ?

Nous disposons d’un processus de triage faux positif (disponible 24h/24, 7j/7) pour traiter et résoudre rapidement les instances où des requêtes légitimes ont déclenché une règle WAF. Les événements faux positifs sont traités comme des problèmes de priorité 1. Par défaut, notre équipe d’assistance peut mettre à jour immédiatement la politique de WAF pour désactiver la règle qui a déclenché l’événement de blocage et permettre à la demande légitime de transiter par WAF.

## Que se passe-t-il si le trafic vers la section administrateur d’Adobe Commerce sur le site de l’infrastructure cloud déclenche des règles WAF ? L’assistance Adobe Commerce résoudra-t-elle les problèmes de trafic d’administration bloqué ?

Oui, le trafic d’administration bloqué est traité comme un problème de priorité 1.
