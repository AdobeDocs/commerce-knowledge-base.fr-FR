---
title: La mise en cache rapide ne fonctionne pas sur Adobe Commerce sur l’infrastructure cloud
description: Cet article fournit un correctif pour une mise en cache rapide qui ne fonctionne pas sur votre site. Un service de réseau de diffusion de contenu et de mise en cache est inclus dans Adobe Commerce pour les plans d’infrastructure et les mises en oeuvre du cloud. Pour vérifier que l’extension Fastly fonctionne ou pour déboguer l’extension Fastly, vous pouvez utiliser la commande curl pour afficher certains en-têtes de réponse. Les valeurs de ces en-têtes de réponse indiquent si l’option Fastly est activée et fonctionne correctement. Vous pouvez examiner plus en détail les problèmes en fonction des valeurs des en-têtes et du comportement de mise en cache.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 586a8c6340bfd2cbf773d1b009d6e106e930117d
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# La mise en cache rapide ne fonctionne pas sur Adobe Commerce sur l’infrastructure cloud

Cet article fournit un correctif pour une mise en cache rapide qui ne fonctionne pas sur votre site. Un service de réseau de diffusion de contenu et de mise en cache est inclus dans Adobe Commerce pour les plans d’infrastructure et les mises en oeuvre du cloud. Pour vérifier que l’extension Fastly fonctionne ou pour déboguer l’extension Fastly, vous pouvez utiliser la commande curl pour afficher certains en-têtes de réponse. Les valeurs de ces en-têtes de réponse indiquent si l’option Fastly est activée et fonctionne correctement. Vous pouvez examiner plus en détail les problèmes en fonction des valeurs des en-têtes et du comportement de mise en cache.

Ces informations vous aident à vérifier et à tester rapidement les en-têtes de votre site actif et de vos serveurs d’origine.

## Versions affectées

* Adobe Commerce sur l’infrastructure cloud
* Fastly 1.2.27 et versions ultérieures

## Problème

La mise en cache peut ne pas fonctionner pour votre site actif, vos environnements de production ou d’évaluation.

## Cause

En règle générale, les configurations, les informations d’identification incorrectes ou les extensions Adobe Commerce non prises en charge posent problème si la mise en cache rapide ne fonctionne pas. Si vous configurez Fastly de manière incorrecte ou utilisez une extension non prise en charge qui supprime les en-têtes, la mise en cache Fastly ne fonctionnera pas.

## Test à l’aide de commandes et vérification des en-têtes de réponse

### Tester avec la commande dig

Tout d’abord, recherchez les en-têtes avec une commande dig sur l’URL. Dans une application de terminal, saisissez dig `<url>` pour vérifier que les services s’affichent rapidement dans les en-têtes. Pour plus d’informations sur les tests de journalisation, reportez-vous à la section Test Fastly de [avant de modifier le DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

Par exemple :

* Site en direct : `dig http[s]://<your domain>`
* Évaluation : `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Production : `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Tester avec la commande curl

Ensuite, utilisez une commande curl pour vérifier que X-Magento-Tags existe et des informations d’en-tête supplémentaires. Le format de commande diffère pour l’évaluation et la production.

Pour plus d’informations sur ces commandes, vous ignorez Fastly lorsque vous injectez `-H "host:URL"`, remplacez par l’origine par l’emplacement de connexion (informations CNAME de votre feuille de calcul OneDrive), `-k` ignore SSL et `-v` fournit des réponses détaillées. Si les en-têtes s’affichent correctement, vérifiez le site actif et vérifiez à nouveau les en-têtes.

* Si des problèmes d’en-tête se produisent lors d’un accès direct aux serveurs d’origine en contournant Fastly, vous pouvez rencontrer des problèmes dans votre code, avec des extensions ou avec l’infrastructure.
* Si vous ne rencontrez aucune erreur en accédant directement aux serveurs d’origine, mais que des en-têtes sont manquants en accédant au domaine en direct via Fastly, vous pouvez rencontrer des erreurs Fastly.

Tout d’abord, vérifiez les en-têtes de réponse dans votre **site actif**. La commande passe par l’extension Fastly pour recevoir des réponses. Si vous ne recevez pas les en-têtes corrects, vous devez tester directement les serveurs d’origine. Cette commande renvoie les valeurs des en-têtes `Fastly-Magento-VCL-Uploaded` et `X-Cache`.

1. Dans un terminal, saisissez la commande suivante pour tester l’URL de votre site actif :

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Utilisez `--resolve` uniquement si votre URL active n’est pas configurée avec DNS et que vous n’avez pas de routage statique. Par exemple :

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Vérifiez les en-têtes de réponse pour vous assurer qu’ils fonctionnent rapidement. La sortie de cette commande est similaire à curl Staging and Production. Par exemple, vous devriez voir les en-têtes uniques renvoyés par cette commande :

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Pour tester **l&#39;évaluation** :

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Pour tester **l’équilibreur de charge de production** :

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Pour tester le **noeud d’origine de production** :

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Un noeud Origine directe :

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Par exemple, si vous disposez d’une URL publique www.mymagento.biz, saisissez une commande similaire à la suivante pour tester le site de production :

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Vérifier les en-têtes de réponse

* Vérifiez les en-têtes et les valeurs de réponse renvoyés :
* Fastly-Magento-VCL-Uploaded doit être présent
* X-Magento-Tags doit être renvoyé
* La fonction Fastly-Module-Enabled doit être activée ou le numéro de version de l’extension Fastly doit être défini sur Oui.
* X-Cache doit être HIT ou HIT, HIT
* x-cache-hits doit être 1,1
* Cache-Control: l’âge maximal doit être supérieur à 0
* Pragma doit être mis en cache

L’exemple suivant montre les valeurs correctes pour Pragma, X-Magento-Tags et Fastly-Module-Enabled.

La sortie des commandes curl peut être longue. Voici un résumé uniquement :

```
* STATE: INIT => CONNECT handle 0x600057800; line 1402 (connection #-5000)
* Rebuilt URL to: https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud/
* Added connection 0. The cache now contains 1 members
* Trying 192.0.2.31...
* STATE: CONNECT => WAITCONNECT handle 0x600057800; line 1455 (connection #0)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                             Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud (54.229.163.31) port 443 (#0)
* STATE: WAITCONNECT => SENDPROTOCONNECT handle 0x600057800; line 1562 (connection #0)
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* ALPN, offering h2

  ... portion omitted for brevity ...

< Set-Cookie: mage-messages=%5B%5D; expires=Wed, 22-Nov-2017 17:39:58 GMT; Max-Age=31536000; path=/
< Pragma: cache
< Expires: Wed, 23 Nov 2016 17:39:56 GMT
< Cache-Control: max-age=86400, public, s-maxage=86400, stale-if-error=5, stale-while-revalidate=5
< X-Magento-Tags: cb_welcome_popup store cb cb_store_info_mobile cb_header_promotional_bar cb_store_info cb_discount-promo-bar cpg_2 cb_83 cb_81 cb_84 cb_85 cb_86 cb_87 cb_88 cb_89 p5646 catalog_product p5915 p6040 p6197 p6227 p7095 p6109 p6122 p6331 p7592 p7651 p7690
< Fastly-Module-Enabled: yes
< Strict-Transport-Security: max-age=31536000
    < Content-Security-Policy: upgrade-insecure-requests
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< X-Frame-Options: SAMEORIGIN
< X-Platform-Server: i-dff64b52
<
* STATE: PERFORM => DONE handle 0x600057800; line 1955 (connection #0)
* multi_done
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
* Connection #0 to host www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud left intact
```

## Résoudre

### Fastly-Module-Enabled n’est pas présent

Si vous ne recevez pas un &quot;oui&quot; pour l’option Fastly-Module-Enabled dans les en-têtes de réponse, vous devez vérifier que le module Fasty est installé et sélectionné.

Pour vérifier que l’option Rapide est activée dans les environnements d’évaluation et de production, vérifiez la configuration dans l’administrateur Commerce pour chaque environnement :

1. Connectez-vous à Admin Console pour l’évaluation et la production à l’aide de l’URL avec /admin (ou de l’URL d’administration modifiée).
1. Accédez à Magasins > Configuration > Avancé > Système. Faites défiler l’écran et cliquez sur Cache de page complète.
1. Assurez-vous que l’option Fastly CDN est sélectionnée.
1. Cliquez sur Configuration rapide. Assurez-vous que l’identifiant de service Fastly et le jeton d’API Fastly sont renseignés (vos informations d’identification Fastly). Vérifiez que les informations d’identification correctes sont saisies pour l’environnement d’évaluation et de production. Cliquez sur Tester les informations d’identification pour obtenir de l’aide.
1. Modifiez le fichier compositeur.json et assurez-vous que le module Fasty est inclus avec la version. Tous les modules de ce fichier sont répertoriés avec les versions.

   * Dans la section &quot;Requiert&quot;, vous devez disposer de &quot;fast/magento2&quot; : `<version number>`
   * Dans la section &quot;Référentiels&quot;, vous devez disposer des éléments suivants :

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Si vous utilisez Configuration Management, vous devez disposer d’un fichier de configuration. Modifiez le fichier app/etc/config.app.php (2.0, 2.1) ou app/etc/config.php (2.2) et assurez-vous que le paramètre `'Fastly_Cdn' => 1` est correct. Le paramètre ne doit pas être `'Fastly_Cdn' => 0` (c’est-à-dire désactivé). Si vous avez activé Fastly, supprimez le fichier de configuration et exécutez la commande bin/magento magento-cloud:scd-dump à mettre à jour. Pour une présentation détaillée de ce fichier, voir [Exemple de gestion des paramètres spécifiques au système](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html#manage-the-system-specific-configuration) dans le Guide de configuration.

Si le module n’est pas installé, vous devez l’installer dans une branche [Environnement d’intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) et l’installer dans la phase d’évaluation et de production. Voir [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) pour obtenir des instructions dans le guide Commerce on Cloud Infrastructure.

### Fastly-Magento-VCL-Uploaded n’est pas présent

Pendant l’installation et la configuration, vous devez avoir téléchargé le fichier Fastly VCL. Il s’agit des fragments de code VCL de base fournis par le module Fastly, et non des fragments de code VCL personnalisés que vous créez. Pour obtenir des instructions, reportez-vous à la section [Chargement rapide de fragments de code VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upload-vcl-to-fastly) dans le guide Commerce on Cloud Infrastructure.

### X-Cache inclut MISS

Si X-Cache est HIT, MISS ou MISS, MISS, saisissez à nouveau la même commande curl pour vous assurer que la page n’a pas été récemment expulsée du cache.

Si vous obtenez le même résultat, utilisez les commandes curl et vérifiez les en-têtes de réponse :

* Pragma est cache
* X-Magento-Tags existe
* Cache-Control: l’âge maximal est supérieur à 0

Si le problème persiste, une autre extension réinitialise probablement ces en-têtes. Répétez la procédure suivante dans l’évaluation pour désactiver les extensions afin de trouver celle qui cause le problème. Une fois que vous avez localisé la ou les extensions à l’origine du problème, vous devez désactiver la ou les extensions dans Production.

1. Pour désactiver les extensions, suivez les étapes décrites dans la section [Gérer les extensions](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=en#manage-extensions) du guide Commerce on Cloud Infrastructure.
1. Après avoir désactivé les extensions, accédez à **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. Cliquez sur **[!UICONTROL Flush Magento Cache]**.
1. Activez maintenant une extension à la fois, enregistrant la configuration et vidant le cache.
1. Essayez les commandes curl et vérifiez les en-têtes de réponse.
1. Répétez les étapes 4 et 5 pour activer et tester les commandes curl. Lorsque les en-têtes Fastly ne s’affichent plus, vous avez trouvé que l’extension provoquait des problèmes avec Fastly.

Lorsque vous isolez l’extension qui réinitialise les en-têtes Fastly, contactez le développeur de l’extension pour obtenir de l’aide supplémentaire. Nous ne pouvons pas fournir de correctifs ou de mises à jour pour que les développeurs d’extensions tiers puissent travailler avec la mise en cache rapide.

## Pour plus d’informations, consultez la documentation destinée aux développeurs :

* [À propos de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Configurer Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Fragments de code VCL personnalisés Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
