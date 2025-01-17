---
title: Certificats SSL (TLS) pour Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit des réponses rapides aux questions sur l’obtention de certificats SSL (TLS) pour votre site Adobe Commerce sur notre infrastructure cloud.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Certificats SSL (TLS) pour Adobe Commerce sur l’infrastructure cloud

Cet article fournit des réponses rapides aux questions sur l’obtention de certificats SSL (TLS) pour votre site Adobe Commerce sur notre infrastructure cloud.

## Quel certificat SSL/TLS Adobe fournit-il ?

Adobe fournit un [certificat SSL/TLS ](https://letsencrypt.org/) validé par le domaine pour diffuser le trafic HTTPS sécurisé depuis [!DNL Fastly]. Adobe fournit un certificat pour chaque environnement d’architecture de plan, d’évaluation et d’Adobe Commerce sur l’infrastructure cloud d’Adobe Commerce sur l’infrastructure cloud de Starter pour sécuriser tous les domaines de cet environnement.

## Que couvre un certificat ?

Pour l’architecture de plan Pro, un certificat SSL est créé pour les environnements dédiés d’évaluation et de production. Chaque environnement dédié en dehors des environnements d’intégration Platform as a Service (PaaS) disposera de ce certificat pour les URL affectées à cet environnement.

Pour l’architecture du plan de démarrage et les environnements d’intégration PaaS, un domaine technique par défaut est fourni avec l’environnement et sécurisé par un certificat distinct.

## Comment ajouter un nouveau domaine pour le certificat existant ?

Pour ajouter le domaine au service dans [!DNL Fastly] :

1. Pointez votre domaine dans DNS sur prod.magentocloud.map.fastly.net et patientez jusqu’à 6 heures.
1. [Envoyez un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant d’ajouter ce domaine dans la configuration Nginx (si vous ne l’avez pas fait auparavant).

## Comment demander un certificat ?

Cas 1

Si vous n’avez pas encore lancé de site web, vous avez peut-être reçu le CNAME de défi ACME de votre conseiller technique client (CTA). Vous avez uniquement besoin d’un défi ACME si vous ne pouvez pas immédiatement pointer votre DNS vers votre URL de production et si vous devez obtenir les certificats SSL créés à l’avance.

Cas 2

Si votre site est déjà actif et/ou que vous pouvez pointer immédiatement les URL qui seront utilisées pour votre site actif, vous n’avez pas besoin de demander un CNAME ACME. Une fois que vous avez ajouté les URL nécessaires à votre Adobe Commerce sur le site d’infrastructure cloud et que vous avez pointé votre DNS sur [!DNL Fastly], la validation HTTP fonctionne et créez votre certificat SSL pour la première fois ou mettez à jour votre certificat avec des URL supplémentaires.

## Puis-je utiliser mon propre certificat SSL/TLS ?

Vous pouvez fournir votre propre certificat SSL/TLS au lieu d’utiliser le [Chiffrer le certificat](https://letsencrypt.org/) fourni par Adobe.

Toutefois, ce processus nécessite un travail supplémentaire pour la configuration et la maintenance. Vous devez d’abord générer une demande de signature de certificat (CSR) pour le nom de domaine (ou nom commun) du site web et la fournir à votre fournisseur SSL pour fournir un certificat SSL.

Une fois que vous disposez du certificat SSL, envoyez un [ticket d’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ou travaillez avec votre CTA pour ajouter des certificats hébergés personnalisés à vos environnements cloud.

* Si les domaines ne sont plus utilisés, ils seront automatiquement supprimés de notre système et aucune autre action n’est requise.
* Si vous possédez déjà un certificat, téléchargez-le à l’aide d’un client SFTP (SSH File Transfer Protocol) vers un emplacement de fichier inaccessible sur le web sur votre serveur et [envoyez un ticket de support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) leur indiquant le chemin du fichier.

>[!WARNING]
>
>Il est important de ne pas télécharger directement les fichiers de certificat vers le ticket. Dans le cas contraire, les certificats seront considérés comme compromis et Adobe devra demander un nouveau certificat.
>Les fichiers doivent être chargés sur le serveur via SFTP. N’utilisez aucune autre méthode, comme la validation des fichiers dans votre référentiel (ce qui ne doit être fait que pour les fichiers non modifiables qui ne contiennent pas de données sensibles).

## Nom du certificat

Le nom du certificat SSL n’importe que pour l’URL principale. Il s’agit du nom d’hôte principal nommé par la première URL et doit correspondre pour être validé et créé. Si vous disposez de quelques URL, elles seront ajoutées au certificat en tant qu’entrées de nom alternatif de l’objet. Si vous disposez de plusieurs URL pointant vers un Adobe Commerce sur un site d’infrastructure cloud, vous ne disposerez que d’une seule certification d’URL de nom commun qui aura alors ajouté des noms de domaine alternatifs pour sécuriser votre site avec SSL.

## Quel domaine s’affichera dans le champ Nom commun du certificat ?

Le domaine affiché sur le certificat n’est que le premier domaine ajouté au certificat TLS, il remplit le champ **Nom commun** (**CN**) et les navigateurs affichent d’abord ce nom. Le champ **Subject Alternative Name** (**SAN**) contient tous les noms DNS pour le certificat TLS. Il n’existe aucun moyen de modifier ou de demander le Nom commun affiché.

## Puis-je utiliser des certificats TLS génériques ?

Les certificats TLS génériques ne peuvent être utilisés qu’avec votre certificat personnalisé et non avec les certificats Chiffrement Adobe Commerce. Dans le cadre de notre optimisation TLS, Adobe met fin à la prise en charge des certificats TLS génériques. Nous identifions et contactons les marchands qui utilisent un certificat générique avec les certificats de chiffrement d’Adobe et qui sont configurés dans la console [!DNL Fastly] pour Adobe Commerce. Nous demandons que ces certificats génériques soient remplacés par des domaines exacts pour garantir la couverture TLS. Pour remplacer un certificat TLS générique, consultez la [section de domaine](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) du module externe [!DNL Fastly]. À partir de là, vous pouvez ajouter des domaines exacts et supprimer le caractère générique. Veuillez noter que DNS devra pointer vers [!DNL Fastly] pour que ces nouveaux domaines puissent naviguer à travers le réseau de diffusion de contenu. Une fois les domaines ajoutés et le DNS mis à jour, un certificat [Let&#39;s Encrypt](https://letsencrypt.org/) correspondant sera mis en service. Si vous ne supprimez pas un domaine pointant vers [!DNL Fastly] à l’aide d’un caractère générique, Adobe supprimera le certificat partagé. Cela peut entraîner une panne du site si le nom de domaine complet de l’URL n’est pas configuré et que le même nom de domaine complet de l’URL n’est pas configuré dans votre DNS. Vous devez donc confirmer que les URL configurées ont également une correspondance un-à-un dans leur DNS pointant vers [!DNL Fastly].

## Que dois-je faire si mon domaine ne pointe plus vers Adobe Commerce ?

Si votre domaine ne pointe plus vers Adobe Commerce, supprimez-le du système [!DNL Fastly]/Adobe Commerce. Voir [!DNL Fastly] [Suppression d’un domaine](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) pour en savoir plus. Bien qu’il ne soit pas nécessaire de pointer votre domaine vers Adobe Commerce, vérifiez si un certificat TLS de domaine de niveau supérieur est requis. Si un domaine de niveau supérieur est requis, mettez à jour votre DNS pour qu’il pointe vers Adobe Commerce. S’il pointe déjà vers Adobe Commerce, mettez à jour votre enregistrement CAA pour inclure [lets-encrypt](https://letsencrypt.org/). Si vous effectuez ces étapes, le certificat LE est mis à jour avec les URL secondaires que le certificat couvre. &#x200B;

## Lecture connexe

[Configuration de certificats SSL/TLS](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) dans notre documentation destinée aux développeurs
