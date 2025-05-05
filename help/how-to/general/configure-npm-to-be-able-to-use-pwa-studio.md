---
title: Configurer NPM pour pouvoir utiliser PWA Studio
description: '''[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) est un nouveau projet disponible pour Adobe Commerce sur l’infrastructure cloud 2.3.x ou version ultérieure. Pour pouvoir utiliser et installer PWA Studio, vous devez définir la version 5.x ou ultérieure du gestionnaire de modules NPM pour obtenir la prise en charge de Node.js 8.x. Cela est effectué dans la section "hooks:build" du fichier de configuration &grave;.magento.app.yaml&grave;."'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 37ac9cca1f876a48092467aa38f2f2f013c83dd9
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Configurer NPM pour pouvoir utiliser PWA Studio

[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) est un nouveau projet disponible pour Adobe Commerce sur l’infrastructure cloud 2.3.x ou version ultérieure. Pour pouvoir utiliser et installer PWA Studio, vous devez définir la version 5.x ou ultérieure du gestionnaire de modules NPM pour obtenir la prise en charge de Node.js 8.x. Cette opération est effectuée dans la section `hooks:build` du fichier de configuration `.magento.app.yaml`.

## Environnement et technologies

* Adobe Commerce sur l’infrastructure cloud 2.3.X
* PWA pour Adobe Commerce

## Définir la version NPM : étapes

Pour définir la version NPM requise, spécifiez-la dans le fichier de configuration `.magento.app.yaml`. Procédez comme suit :

1. Dans votre environnement de développement local, recherchez le fichier de configuration `.magento.app.yaml`.
1. Ouvrez le fichier à modifier à l’aide de votre éditeur de texte brut ou de votre IDE.
1. Définissez la version requise dans la section `hooks:build`. Dans l&#39;exemple suivant, la configuration est paramétrée pour installer NPM v9.5.0, le plus élevé disponible actuellement (4 février 2019) :

   ```yaml
   hooks:
       build: |
           unset NPM_CONFIG_PREFIX
           curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
           export NVM_DIR="$HOME/.nvm"
           [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
           nvm install 9.5.0
   ```

   >[!NOTE]
   >
   >Si vous souhaitez exécuter Node.JS dans votre application et pas seulement dans votre version, ajoutez les commandes suivantes pour modifier le crochet de la version :
   > 
   > ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Enregistrez les modifications dans le fichier.
1. Git push le fichier modifié dans votre [environnement d&#39;intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md).

Les modifications prennent effet une fois que vous avez envoyé le fichier YAML mis à jour vers l’environnement Git.

## Documentation connexe

* [Configuration de l’application : hooks](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html?lang=fr) dans notre guide d’infrastructure Adobe Commerce on Cloud.
