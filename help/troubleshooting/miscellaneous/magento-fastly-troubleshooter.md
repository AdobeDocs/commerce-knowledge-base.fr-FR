---
title: Dépannage rapide d’Adobe Commerce
description: Ce dépannage rapide pour les utilisateurs d’Adobe Commerce vous guidera vers les solutions, en fonction de votre réponse sur les symptômes que vous voyez. Cliquez sur les questions pour afficher les options ou réponses suivantes.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Dépannage rapide d’Adobe Commerce

Ce dépannage rapide pour les utilisateurs d’Adobe Commerce vous guidera vers les solutions, en fonction de votre réponse sur les symptômes que vous voyez. Cliquez sur les questions pour afficher les options ou réponses suivantes.

## Étape 1 - Vérifier le service Fastly {#step-1}

+++**Le client signale un problème impliquant Fastly. Le service Fastly est-il en panne ?**

a. OUI - Vérifier [État du service Fastly](https://status.fastly.com/), et [envoi d’un ticket d’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NO - Passez à [Étape 2](#step-2).

+++

## Étape 2 - Vérification du fichier de configuration VCL {#step-2}

+++**Avez-vous des erreurs lorsque vous exécutez Backend Tester ?**

Exécutez l’URL de votre projet via le [Tuteur principal - Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/). Il affiche la version du fichier de configuration VCL, si la page peut être mise en cache, la version du module Fastly et d’autres informations de dépannage utiles. As-tu des erreurs ?

a. OUI - Vous avez le message _La version du module externe VCL est obsolète ! Transférez à nouveau._ Pour la solution à cette erreur, reportez-vous à la section [Erreur Fastly : la version du module externe VCL est obsolète ! Veuillez recharger](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md).\
b. NON - [Étape 3](#step-3).

+++

## Étape 3 - Vérification de l’erreur d’optimisation des images {#step-3}

+++**Erreur d’optimisation des images ?**

a. OUI - [Erreur lors de l’activation de l’optimisation des images](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NO - Vérifiez le DNS en exécutant dans la ligne de commande/le terminal : `dig [your website.com] + short`. Passez à [Étape 4](#step-4).

+++

## Étape 4 - Versions DNS {#step-4}

+++**Que se passe-t-il lorsque vous exécutez `dig`?**

Lorsque vous exécutez `dig` a-t-il renvoyé un enregistrement pointant vers prod.magentocloud.map.fastly.net ou l’une des adresses IP suivantes (voir [Mise à jour de la configuration DNS avec le paramètre de production](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns) dans la documentation destinée aux développeurs) :

* 151.101.1.124
* 151.101.65.124
* 151.101.129.124
* 151.101.193.124

a. OUI - Le problème n’est pas lié au DNS. Passez à [Étape 5](#step-5).\
b. NO - Le problème est probablement lié au DNS. Le client doit [Vérification de la configuration DNS](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns "https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns") ou contactez leur fournisseur DNS pour plus d’informations.

+++

## Étape 5 - Confirmer la connexion {#step-5}

+++**Obtenez-vous un message &quot;Connexion non sécurisée&quot; ou &quot;Non sécurisée&quot; lors de l’exécution `curl -svo /dev/null "https://website.com"` dans l’interface de ligne de commande/le terminal ?**

a. OUI - Il s’agit probablement d’un problème de certificat. Visitez le site web dans un navigateur, sélectionnez l’icône de verrouillage et recherchez une expiration de certificat. Passez à [Étape 6](#step-6).\
b. NO - Visite [http://fastly-debug.com](https://www.fastly-debug.com/) et partager ces informations dans une [ticket de support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Étape 6 - Confirmation que vous disposez d’un certificat TSL valide {#step-6}

+++**Le certificat a-t-il expiré ?**

a. OUI - Vous devez renouveler votre certificat TLS avec l’autorité de certification (CA).\
b. NON - Vous ne disposez peut-être pas du tout d’un certificat. Si vous disposez d’Adobe Commerce, nous vous recommandons d’acheter un certificat TLS. Si vous utilisez Adobe Commerce sur l’infrastructure cloud, vous pouvez disposer d’un certificat SSL/TLS à validation de domaine pour diffuser rapidement le trafic HTTPS sécurisé. Voir [configuration des certificats SSL/TLS](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) dans notre documentation destinée aux développeurs.

+++

[Retour à l’étape 1](#step-1)
