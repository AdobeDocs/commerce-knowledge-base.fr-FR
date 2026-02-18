---
title: Certificats SSL (TLS) pour Adobe Commerce sur les infrastructures cloud
description: Cet article fournit des réponses rapides aux questions sur l’obtention de certificats SSL (TLS) pour votre site Adobe Commerce sur notre infrastructure cloud.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---

# Certificats SSL (TLS) pour Adobe Commerce sur les infrastructures cloud

Cet article fournit des réponses rapides aux questions sur l’obtention de certificats SSL (TLS) pour votre site Adobe Commerce sur notre infrastructure cloud.

## Quel certificat SSL/TLS Adobe fournit-il ?

Adobe fournit un certificat validé par un domaine [chiffrons le certificat SSL/TLS](https://letsencrypt.org/) pour traiter le trafic HTTPS sécurisé provenant de l’adresse [!DNL Fastly]. Adobe fournit un certificat pour chaque environnement d’architecture Adobe Commerce on cloud infrastructure Pro plan, Staging et Adobe Commerce on cloud infrastructure Starter plan pour sécuriser tous les domaines de cet environnement.

## Que couvre un certificat ?

Pour l’architecture Pro plan, un certificat SSL sera créé pour les environnements dédiés d’évaluation et de production. Chaque environnement dédié en dehors des environnements d’intégration Platform-as-a-Service (PaaS) dispose de ce certificat pour les URL affectées à cet environnement.

Pour l’architecture du plan de démarrage et les environnements d’intégration PaaS, il y aura un domaine technique par défaut fourni avec l’environnement et sécurisé par un certificat distinct.

## Comment ajouter un nouveau domaine pour le certificat existant ?

Pour ajouter le domaine au service dans [!DNL Fastly] :

1. Pointez votre domaine dans DNS sur prod.magentocloud.map.fastly.net et patientez jusqu’à 6 heures.
1. [Envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) en demandant l’ajout de ce domaine dans la configuration Nginx (si vous ne l’avez pas déjà fait).

## Comment demander un certificat ?

1er cas

Si vous n’avez pas encore lancé de site web, vous avez peut-être reçu le CNAME du défi ACME de votre conseiller technique client (CTA). Vous n’avez besoin d’un défi ACME que si vous ne pouvez pas immédiatement pointer votre DNS vers votre URL de production et que vous devez obtenir les certificats SSL créés à l’avance.

2e cas

Si votre site est déjà actif et/ou que vous pouvez indiquer les URL qui seront utilisées immédiatement pour votre site actif, vous n’avez pas besoin de demander un CNAME ACME. Une fois que vous avez ajouté les URL nécessaires à votre site d’infrastructure cloud Adobe Commerce sur et que vous avez pointé votre DNS vers [!DNL Fastly], la validation HTTP fonctionne et crée votre certificat SSL pour la première fois ou met à jour votre certificat avec des URL supplémentaires.

## Puis-je utiliser mon propre certificat SSL/TLS ?

Vous pouvez fournir votre propre certificat SSL/TLS au lieu d’utiliser le certificat [Let’s Encrypt](https://letsencrypt.org/) fourni par Adobe.

Toutefois, ce processus nécessite un travail supplémentaire pour sa configuration et sa maintenance. Vous devrez d’abord générer une demande de signature de certificat (CSR) pour le nom de domaine (ou nom commun) du site web et la fournir à votre fournisseur SSL pour fournir un certificat SSL.

Une fois que vous disposez du certificat SSL, envoyez un [ticket d’assistance Adobe Commerce](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) ou utilisez votre CTA pour ajouter des certificats hébergés personnalisés à vos environnements cloud.

* Si les domaines ne sont plus utilisés, ils seront automatiquement purgés de notre système et aucune autre action n’est requise.
* Si vous possédez déjà un certificat, chargez-le à l’aide d’un client SFTP (SSH File Transfer Protocol) vers un emplacement de fichier inaccessible sur votre serveur et [envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) en lui indiquant le chemin d’accès au fichier.

>[!WARNING]
>
>Il est important de ne pas charger les fichiers de certificat directement dans le ticket. Dans le cas contraire, les certificats seront considérés comme compromis et Adobe devra demander un nouveau certificat.
>Les fichiers doivent être chargés vers le serveur via SFTP dans un dossier de votre choix, par exemple `var/ssl`, `/tmp/ssl`, etc. - n’utilisez aucune autre méthode, notamment la validation des fichiers dans votre référentiel (ce qui ne doit être fait que pour les fichiers non modifiables qui ne contiennent pas de données sensibles).

## Nom de votre certificat

Le nom du certificat SSL n’a d’importance que pour l’URL principale. Il s’agit du nom d’hôte principal nommé par la première URL et qui doit correspondre pour être validé et créé. Si vous disposez de quelques URL, elles sont ajoutées au certificat en tant qu’entrées de nom secondaire de l’objet. Si plusieurs URL pointent vers un site d’infrastructure cloud d’Adobe Commerce, vous ne disposez que d’une seule certification d’URL de nom commun à laquelle seront ajoutés des noms secondaires d’objet afin de sécuriser votre site avec SSL.

## Quel domaine s’affichera dans le champ Nom commun du certificat ?

Le domaine affiché sur le certificat n’est que le premier domaine ajouté au certificat TLS. Il renseigne le champ **Nom commun** (**CN**) et les navigateurs affichent d’abord ce nom. Le champ **Autre nom de l’objet** (**SAN**) contient tous les noms DNS du certificat TLS. Il n’existe aucun moyen de modifier ou de demander le nom commun affiché.

## Puis-je utiliser des certificats TLS génériques ?

Les certificats TLS génériques ne peuvent être utilisés qu’avec votre certificat personnalisé et non avec les certificats Let’s Encrypt d’Adobe Commerce. Dans le cadre de notre optimisation du protocole TLS, Adobe met fin à la prise en charge des certificats TLS génériques. Nous identifions et contactons des commerçants qui utilisent un certificat générique avec des certificats Let’s Encrypt d’Adobe et qui sont configurés dans la console [!DNL Fastly] pour Adobe Commerce. Nous demandons que ces certificats génériques soient remplacés par des domaines exacts pour assurer la couverture TLS. Pour remplacer un certificat TLS par un caractère générique, consultez la section [domaine](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) du plug-in [!DNL Fastly]. À partir de là, vous pouvez ajouter les domaines exacts et supprimer le caractère générique. Notez que le DNS doit pointer vers [!DNL Fastly] pour que ces nouveaux domaines soient acheminés via le réseau CDN. Une fois les domaines ajoutés et le DNS mis à jour, un certificat [Chiffrons](https://letsencrypt.org/) correspondant sera fourni. Si vous ne supprimez pas un domaine pointant vers [!DNL Fastly] à l’aide d’un caractère générique, Adobe supprimera le certificat partagé. Cela peut entraîner une panne du site si le nom de domaine complet de l’URL n’est pas configuré et que le même nom de domaine complet d’URL est configuré dans votre DNS. Vous devez donc confirmer que les URL configurées ont également une correspondance un-à-un dans leur DNS pointant vers [!DNL Fastly].

## Que dois-je faire si mon domaine ne pointe plus vers Adobe Commerce ?

Si votre domaine ne pointe plus vers Adobe Commerce, supprimez-le du système [!DNL Fastly]/Adobe Commerce. Voir [!DNL Fastly] [Suppression d’un domaine](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) pour en savoir plus. Bien qu’il ne soit pas nécessaire de pointer votre domaine vers Adobe Commerce, vérifiez si un certificat TLS de domaine de niveau supérieur est requis. Si un domaine de niveau supérieur est requis, mettez à jour votre DNS pour pointer vers Adobe Commerce. S’il pointe déjà vers Adobe Commerce, mettez à jour votre enregistrement CAA pour inclure [lets-encrypt](https://letsencrypt.org/). Si vous effectuez ces étapes, le certificat LE est mis à jour avec les URL secondaires nécessaires couvertes par le certificat&#x200B;

## Lecture connexe

[Fournir des certificats SSL/TLS](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) dans notre documentation destinée aux développeurs
