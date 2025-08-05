---
title: Configurez NPM pour pouvoir utiliser PWA Studio
description: '[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) est un nouveau projet disponible pour Adobe Commerce sur une infrastructure cloud 2.3.x ou ultérieure. Pour pouvoir utiliser et installer PWA Studio, vous devez définir la version du gestionnaire de packages NPM sur 5.x ou une version ultérieure pour obtenir la prise en charge de Node.js 8.x. Cette opération est effectuée dans la section « hooks:build » du fichier de configuration « .magento.app.yaml ».'
exl-id: 3854fc94-e8ad-45d8-bf3e-73462364220d
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Configurez NPM pour pouvoir utiliser PWA Studio

[Progressive Web Apps (PWA) Studio](https://magento.github.io/pwa-studio/) est un nouveau projet disponible pour Adobe Commerce sur une infrastructure cloud 2.3.x ou ultérieure. Pour pouvoir utiliser et installer PWA Studio, vous devez définir la version du gestionnaire de packages NPM sur 5.x ou une version ultérieure pour obtenir la prise en charge de Node.js 8.x. Cette opération est effectuée dans la section `hooks:build` du fichier de configuration `.magento.app.yaml`.

## Environnement et technologies

* Adobe Commerce sur l’infrastructure cloud 2.3.X
* PWA pour Adobe Commerce

## Définir la version du NPM : étapes

Pour définir la version NPM nécessaire, spécifiez-la dans le fichier de configuration `.magento.app.yaml`. Procédez comme suit :

1. Sur votre environnement de développement local, recherchez le fichier de configuration `.magento.app.yaml`.
1. Ouvrez le fichier pour le modifier à l’aide de votre éditeur de texte brut ou IDE.
1. Définissez la version requise dans la section `hooks:build` . Dans l’exemple suivant, la configuration est définie pour installer NPM v9.5.0, la plus élevée disponible pour le moment (4 février 2019) :

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
   >Si vous souhaitez exécuter Node.JS dans votre application et pas seulement dans votre build, ajoutez les commandes suivantes pour modifier votre hook de build :
   > 
   > ```
   > echo 'unset NPM_CONFIG_PREFIX' >> .environment
   > echo 'export NO_UPDATE_NOTIFIER=1' >> .environment
   > echo 'export NVM_DIR="$MAGENTO_CLOUD_DIR/.nvm"' >> .environment
   > echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> .environment
   > ```

1. Enregistrez les modifications dans le fichier .
1. Envoyez le fichier modifié par Git à votre [environnement d’intégration](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27242).

Les modifications prennent effet après que vous avez envoyé le fichier YAML mis à jour dans Git à l’environnement.

## Documentation connexe

* [Configuration de l’application : points d’extension](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/hooks-property.html?lang=fr) dans notre guide Adobe Commerce sur les infrastructures cloud.
