---
title: Échec de l’installation ; impossible de créer install.log
description: Cet article fournit un correctif pour une installation qui a échoué en raison de la non-création de "install.log" par l’assistant de configuration lors de l’installation.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Échec de l’installation ; impossible de créer install.log

Cet article fournit un correctif pour une installation qui a échoué en raison de l’assistant de configuration qui n’a pas créé le `install.log` lors de l’installation.

## Problème

L’exécution simultanée de processus Adobe Commerce peut entraîner des problèmes lors de la création du journal d’installation. (Par exemple, deux installations différentes dans des pages à onglets distinctes.)

## Cause

Installation-failed-cannot-create-install.log
Vérifiez votre paramètre pour `open_basedir` dans `php.ini`. L’assistant de configuration utilise l’appel PHP [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) pour obtenir la valeur du répertoire temporaire. Si [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) est défini pour refuser les connexions à un répertoire spécifié par `sys_get_temp_dir`, l’installation échoue.
Vérifiez votre paramètre pour `open_basedir` dans `php.ini`. L’assistant de configuration utilise l’appel PHP [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) pour obtenir la valeur du répertoire temporaire. Si [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) est défini pour refuser les connexions à un répertoire spécifié par `sys_get_temp_dir`, l’installation échoue.


## Solution

Pour résoudre le problème, modifiez la valeur de `open_basedir` et redémarrez le serveur web.

Si vous ne savez pas comment modifier cette valeur, procédez comme suit :

1. Si vous ne l&#39;avez pas déjà fait, créez [phpinfo.php](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo).
1. Saisissez l’URL suivante dans le champ d’adresse ou d’emplacement de votre navigateur : `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Recherchez l’emplacement de `php.ini`.     `php.ini` est généralement spécifié sous la forme **Fichier de configuration chargé** dans les résultats affichés.
1. En tant qu&#39;utilisateur disposant de droits racine, ouvrez `php.ini` dans un éditeur de texte.
1. Recherchez la valeur de `open_basedir` et modifiez-la.
1. Enregistrez vos modifications dans `php.ini`.
1. Redémarrez le serveur web.
