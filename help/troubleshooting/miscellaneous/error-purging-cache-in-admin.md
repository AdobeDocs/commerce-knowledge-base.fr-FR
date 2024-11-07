---
title: Purge du cache des erreurs dans Commerce Admin
description: 'Cet article explique comment identifier la cause d’un message d’erreur qui se produit lors de la purge du cache dans l’administrateur Commerce. Lorsque vous tentez de purger le cache via l’administrateur, vous recevez le message suivant :'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Purge du cache des erreurs dans Commerce Admin

Cet article explique comment identifier la cause d’un message d’erreur qui se produit lors de la purge du cache dans l’administrateur Commerce. Lorsque vous tentez de purger le cache via l’administrateur, vous recevez le message suivant :
Le fichier */app/project-id/pub/media/catalog/product/cache/directory/filename&quot; ne peut pas être supprimé. Warning!unlink(/app/project id/pub/media/catalog/product/cache/directory/filename) : No such file or directory*

## Produits et versions concernés

Adobe Commerce (toutes les méthodes de déploiement) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## Problème

Lorsque vous tentez de purger le cache par l’intermédiaire de l’administrateur, vous recevez un message d’erreur.

<u>Étapes à reproduire :</u>

1. Dans l’administrateur, accédez à **Système** > **Outils** > **Gestion du cache**.
1. Sélectionnez l’une des options de mise en cache.

<u>Résultat attendu :</u>

Vous avez réussi à vider le cache Adobe Commerce sans erreur.

<u>Résultat réel :</u>

Vous obtenez l’erreur &quot;le fichier ne peut pas être supprimé&quot;.

## Cause

L’erreur est liée à un délai entre le moment où l’opération de nettoyage du cache a été lancée et celui où elle a été signalée comme étant terminée.

## Solution

1. Vérifiez que les fichiers mentionnés dans l’erreur ne sont pas présents sur le serveur (en vérifiant que la purge du cache a réussi) :

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

Si vous voyez la sortie suivante :

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

une tentative d’effacement des fichiers a été effectuée lorsque l’opération était déjà terminée. Il ne s’agit pas d’un bogue ; il s’agit d’un problème de simultanéité des messages qui doit parfois se produire. Il n’y a aucun problème à résoudre.
Cependant, si la sortie indique que les fichiers sont toujours dans le cache, vous devez [envoyer un ticket de support](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lecture connexe

* [Gestion du cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) dans notre documentation destinée aux développeurs.
