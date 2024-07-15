---
title: Courrier électronique indiquant que le stockage des exportations est presque complet
description: Cet article fournit une solution au problème où vous recevez un courrier électronique indiquant que le stockage des exportations est presque saturé.
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Courriel indiquant que le stockage des exportations est presque saturé

Cet article fournit une solution au problème où vous recevez un courrier électronique indiquant que le stockage des exportations est presque saturé.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

Vous recevez un courrier électronique avec le contenu suivant, mais vous ne parvenez pas à localiser le dossier *exports* :

*Notre surveillance a détecté que le stockage &quot;exports&quot; de votre cluster XXX est environ &#39;85 %&#39; rempli.*
*Si nécessaire, passez en revue l’utilisation, effectuez un nettoyage ou demandez une modification de la taille.*
*Notez également que nous allons tenter une mise à niveau automatique lorsque le stockage atteint le niveau de seuil critique.*

## Cause

L&#39;email fait référence au stockage **exports**, qui correspond à la quantité de disque allouée aux fichiers/médias, et non à un dossier spécifique nommé *exports*.

## Solution

Vous devez examiner l’utilisation des fichiers dans l’environnement. Exécutez cette commande pour obtenir l’utilisation existante :

`df -h |grep data`

Les emplacements où le stockage des fichiers est susceptible d&#39;être rempli sont les dossiers *pub/media/catalog/product/cache* ou *var/log*. Pour déterminer l’espace disque utilisé par les fichiers, exécutez cette commande avec le chemin d’accès approprié */path/to/folder* :

`du -shc` */path/to/folder*

Si l’utilisation du disque multimédia représente une grande partie de l’espace disque total, vous pouvez envisager d’activer [l’optimisation d’image détaillée rapide](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization), puis de supprimer manuellement les fichiers du dossier *pub/media/catalog/product/cache* sur le serveur.

## Lecture connexe

[Vérifiez les clusters dédiés](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) dans notre base de connaissances d&#39;assistance.
