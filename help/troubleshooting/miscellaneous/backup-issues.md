---
title: Problèmes de sauvegarde
description: Cet article répertorie les solutions possibles pour les problèmes de création de sauvegarde.
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Problèmes de sauvegarde

Cet article répertorie les solutions possibles pour les problèmes de création de sauvegarde.

## Produits et versions concernés

* Adobe Commerce On-Premise 2.3.x
* Magento Open Source 2.3.x

## Sauvegarde désactivée {#backup-disabled}

Si la fonctionnalité de sauvegarde d’Adobe Commerce ne démarre pas ou n’affiche pas le message suivant, vous devez activer la fonctionnalité avant de la sauvegarder.

```bash
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

Saisissez la commande d’interface de ligne de commande suivante :

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

Pour plus d’informations sur les sauvegardes, voir [Sauvegarde et restauration du système de fichiers, des médias et de la base de données.](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/tutorials/backup)

## Espace disque insuffisant {#insufficient-disk-space-trouble-backup-space-}

Si la sauvegarde a échoué en raison d’un espace disque insuffisant, vous devez généralement libérer de l’espace disque en déplaçant certains fichiers vers un autre périphérique ou lecteur de stockage. Cependant, il peut y avoir d’autres façons de résoudre le problème. Consultez l’une des ressources suivantes pour obtenir des conseils :

* [8 Conseils pour résoudre les problèmes de disque dur des systèmes Linux et Unix tels que Disque complet ou Impossible d’écrire sur le disque](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [serverfaul: df indique que le disque est plein, mais qu’il ne l’est pas &#x200B;](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com: Tracking de l’emplacement de l’espace disque sous Linux ?](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## Erreur du système d’exploitation {#operating-system-error-trouble-backup-os-}

Malheureusement, nous ne pouvons rien recommander en raison de la variété des erreurs que vous pourriez rencontrer. Nous pouvons toutefois vous suggérer :

* Contactez votre administrateur système.
* Recherchez dans les forums publics tels que [Stack Exchange](https://unix.stackexchange.com) ou [Stack Overflow](https://stackoverflow.com)
* Ouvrez un [problème GitHub](https://github.com/magento/magento2/issues) et nous allons essayer de vous aider.

## Échec de la sauvegarde {#backup-fails-trouble-backup-all-}

Si la sauvegarde échoue ou si tous les tests de sauvegarde échouent, il est possible que le [propriétaire du système de fichiers Adobe Commerce](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/file-system/overview) ne dispose pas des privilèges et de la propriété suffisants du système de fichiers Adobe Commerce. Par exemple, un autre utilisateur peut posséder les fichiers ou les fichiers peuvent être en lecture seule.

Accordez une attention particulière aux autorisations du système de fichiers et à la propriété du répertoire et des sous-répertoires `<magento_root>/var`. Pour plus d’informations, voir [Définition des droits d’accès et de la propriété du système de fichiers](https://experienceleague.adobe.com/fr/docs/commerce-operations/installation-guide/prerequisites/file-system/configure-permissions).
