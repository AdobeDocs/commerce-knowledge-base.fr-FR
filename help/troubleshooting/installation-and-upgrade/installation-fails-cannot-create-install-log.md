---
title: Échec de l’installation ; impossible de créer install.log
description: Cet article fournit un correctif pour une installation ayant échoué en raison de l’absence de création du fichier « install.log » par l’assistant d’installation lors de l’installation.
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%
---
# Échec de l’installation ; impossible de créer install.log

Cet article fournit un correctif pour une installation ayant échoué en raison de l&#39;absence de création du `install.log` par l&#39;Assistant Installation lors de l&#39;installation.

## Problème

L’exécution simultanée de processus Adobe Commerce peut entraîner des problèmes lors de la création du journal d’installation. (Par exemple, deux installations différentes dans des pages d’onglet distinctes.)

## Cause

Installation-failed-cannot-create-install.log
Vérifiez votre paramètre pour `open_basedir` dans `php.ini`. L&#39;Assistant Installation utilise l&#39;appel PHP [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) pour obtenir la valeur du répertoire temporaire. Si [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) est défini pour refuser les connexions à un répertoire spécifié par `sys_get_temp_dir`, l&#39;installation échoue.
Vérifiez votre paramètre pour `open_basedir` dans `php.ini`. L&#39;Assistant Installation utilise l&#39;appel PHP [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) pour obtenir la valeur du répertoire temporaire. Si [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) est défini pour refuser les connexions à un répertoire spécifié par `sys_get_temp_dir`, l&#39;installation échoue.


## Solution

Pour résoudre ce problème, modifiez la valeur de `open_basedir` et redémarrez le serveur web.

Si vous ne savez pas comment modifier cette valeur, procédez comme suit :

1. Si ce n&#39;est pas déjà fait, créez [phpinfo.php](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software).
1. Saisissez l’URL suivante dans le champ adresse ou emplacement de votre navigateur : `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. Recherchez l’emplacement de `php.ini`. `php.ini` est généralement spécifié comme **fichier de configuration chargé** dans les résultats affichés.
1. En tant qu’utilisateur disposant des privilèges root, ouvrez `php.ini` dans un éditeur de texte.
1. Recherchez la valeur de `open_basedir` et modifiez-la.
1. Enregistrez vos modifications dans `php.ini`.
1. Redémarrez le serveur web.
