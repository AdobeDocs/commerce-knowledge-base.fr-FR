---
title: "Courrier électronique indiquant que le stockage des exportations est presque saturé"
description: Cet article fournit une solution au problème où vous recevez un courrier électronique indiquant que le stockage des exportations est presque saturé.
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Courriel indiquant que le stockage des exportations est presque saturé

Cet article fournit une solution au problème où vous recevez un courrier électronique indiquant que le stockage des exportations est presque saturé.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

Vous recevez un courrier électronique avec le contenu suivant, mais vous ne parvenez pas à localiser la variable *exports* folder:

*Notre surveillance a détecté que le stockage &quot;des exportations&quot; sur votre cluster XXX est environ &#39;85%&#39; plein.*
*Si nécessaire, passez en revue l’utilisation, effectuez un nettoyage ou demandez une modification de la taille.*
*Notez également que nous allons tenter une mise à niveau automatique lorsque le stockage atteint le niveau de seuil critique.*

## Cause

Le courrier électronique fait référence à la variable **exports** le stockage, c’est-à-dire la quantité de disque allouée aux fichiers/supports, et non un dossier spécifique nommé *exports*.

## Solution

Vous devez examiner l’utilisation des fichiers dans l’environnement. Exécutez cette commande pour obtenir l’utilisation existante :

`df -h |grep data`

Les emplacements où le stockage des fichiers est susceptible d’être rempli sont les suivants : *pub/media/catalog/product/cache* ou *var/log* dossiers. Pour déterminer l’espace disque utilisé par les fichiers, exécutez cette commande avec le chemin approprié. */path/to/folder*:

`du -shc` */path/to/folder*

Si l’utilisation du disque multimédia représente une grande partie de l’espace disque total, vous pouvez envisager d’activer [Optimisation des images profondes et rapide](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization), puis supprimez les fichiers dans le *pub/media/catalog/product/cache* sur le serveur manuellement.

## Lecture connexe

[Vérifier les clusters dédiés](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) dans notre base de connaissances de soutien.