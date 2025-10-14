---
title: La mise en cache rapide ne fonctionne pas sur Adobe Commerce dans l’infrastructure cloud
description: Cet article fournit un correctif pour que la mise en cache rapide ne fonctionne pas sur votre site. Fastly est un service de réseau CDN et de mise en cache inclus avec Adobe Commerce sur les plans et implémentations d’infrastructure cloud. Pour vérifier que l’extension Fastly fonctionne ou pour déboguer l’extension Fastly, vous pouvez utiliser la commande curl pour afficher certains en-têtes de réponse. Les valeurs de ces en-têtes de réponse indiquent si Fastly est activé ou non et fonctionne correctement. Vous pouvez examiner plus en détail les problèmes en fonction des valeurs des en-têtes et du comportement de mise en cache.
exl-id: 725949e9-b69b-456f-9c56-e2163143a71e
feature: Cache, Cloud, Console, Paas
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# La mise en cache rapide ne fonctionne pas sur Adobe Commerce dans l’infrastructure cloud

Cet article fournit un correctif pour que la mise en cache rapide ne fonctionne pas sur votre site. Fastly est un service de réseau CDN et de mise en cache inclus avec Adobe Commerce sur les plans et implémentations d’infrastructure cloud. Pour vérifier que l’extension Fastly fonctionne ou pour déboguer l’extension Fastly, vous pouvez utiliser la commande curl pour afficher certains en-têtes de réponse. Les valeurs de ces en-têtes de réponse indiquent si Fastly est activé ou non et fonctionne correctement. Vous pouvez examiner plus en détail les problèmes en fonction des valeurs des en-têtes et du comportement de mise en cache.

Ces informations vous aident à vérifier et à tester les en-têtes Fastly pour votre site actif et vos serveurs d’origine.

## Versions affectées

* Adobe Commerce sur les infrastructures cloud
* Fastly 1.2.27 et versions ultérieures

## Problème

La mise en cache peut ne pas fonctionner pour votre site actif, vos environnements de production ou d’évaluation.

## Cause

En règle générale, les configurations, les informations d’identification incorrectes ou les extensions d’Adobe Commerce non prises en charge constituent un problème lorsque la mise en cache de Fastly ne fonctionne pas. Si vous configurez Fastly de manière incorrecte ou si vous utilisez une extension non prise en charge qui supprime les en-têtes, la mise en cache Fastly ne fonctionnera pas.

## Tester avec des commandes et vérifier les en-têtes de réponse

### Tester avec la commande dig

Tout d’abord, recherchez les en-têtes avec une commande dig vers l’URL. Dans une application de terminal, saisissez dig `<url>` pour vérifier l’affichage des services Fastly dans les en-têtes. Pour des tests de recherche supplémentaires, voir Tests de Fastly [&#x200B; avant de modifier le DNS](https://docs.fastly.com/guides/basic-configuration/testing-setup-before-changing-domains).

Par exemple :

* Site en ligne : `dig http[s]://<your domain>`
* Évaluation : `dig http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud`
* Production : `dig http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud`

### Tester avec la commande curl

Ensuite, utilisez une commande curl pour vérifier l’existence de X-Magento-Tags et des informations d’en-tête supplémentaires. Le format de la commande est différent pour l’évaluation et la production.

Pour plus d’informations sur ces commandes, vous pouvez contourner Fastly lorsque vous injectez du `-H "host:URL"`, remplacer par l’origine de l’emplacement de connexion (informations CNAME de votre feuille de calcul OneDrive), `-k` ignore le SSL et `-v` fournit des réponses détaillées. Si les en-têtes s’affichent correctement, vérifiez le site actif et vérifiez à nouveau les en-têtes.

* Si des problèmes d’en-tête se produisent lors de l’accès direct aux serveurs d’origine en contournant Fastly, vous pouvez avoir des problèmes dans votre code, avec les extensions ou avec l’infrastructure.
* Si vous ne rencontrez aucune erreur qui touche directement les serveurs d’origine, mais que des en-têtes manquent pour atteindre le domaine en direct via Fastly, vous pouvez avoir des erreurs Fastly .

Tout d’abord, vérifiez votre **site actif** pour vérifier les en-têtes de réponse. La commande passe par l’extension Fastly pour recevoir des réponses. Si vous ne recevez pas les en-têtes corrects, vous devez tester directement les serveurs d’origine. Cette commande renvoie les valeurs des en-têtes `Fastly-Magento-VCL-Uploaded` et `X-Cache`.

1. Dans un terminal, saisissez la commande suivante pour tester l’URL de votre site en direct :

   ```
   curl http://<live URL> -vo /dev/null -HFastly-Debug:1 [--resolve]
   ```

   Utilisez `--resolve` uniquement si votre URL active n’est pas configurée avec le DNS et qu’aucune route statique n’est définie. Par exemple :

   ```
   curl http://www.mymagento.biz -vo /dev/null -HFastly-Debug:1
   ```

1. Vérifiez les en-têtes de réponse pour vous assurer que Fastly fonctionne. La sortie de cette commande est similaire à curl Staging and Production. Par exemple, vous devriez voir les en-têtes uniques renvoyés par cette commande :

   ```
   < Fastly-Magento-VCL-Uploaded: yes    < X-Cache: HIT, MISS
   ```

Pour tester **Staging** :

```
curl http[s]://staging.<your domain>.c.<instanceid>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Pour tester l’**équilibreur de charge de production** :

```
curl http[s]://<your domain>.c.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Pour tester le **nœud d’origine de production** :

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Nœud d’origine directe :

```
curl http[s]://<your domain>.{1|2|3}.<project ID>.ent.magento.cloud -H "host: <url>" -k -vo /dev/null -HFastly-Debug:1
```

Par exemple, si vous disposez d’une URL publique www.mymagento.biz, saisissez une commande similaire à la suivante pour tester le site d’exploitation :

```
curl -k https://www.mymagento.biz.c.sv7gVom4qrpek.ent.magento.cloud -H 'Host: www.mymagento.biz' -vo /dev/null -HFastly-Debug:1
```

### Vérifier les en-têtes de réponse

* Vérifiez les en-têtes et les valeurs de réponse renvoyés :
* Fastly-Magento-VCL-Uploaded doit être présent
* X-Magento-Tags doit être renvoyé
* Fastly-Module-Enabled doit être Oui ou le numéro de version de l’extension Fastly
* X-Cache doit être HIT ou HIT, HIT
* x-cache-hits doit être 1,1
* Contrôle de cache : l’âge maximal doit être supérieur à 0.
* Le paramètre doit être mis en cache

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

Si vous ne recevez pas de « oui » pour le Fastly-Module-Enabled dans les en-têtes de réponse, vous devez vérifier que le module Fastly est installé et sélectionné.

Pour vérifier que Fastly est activé dans les environnements d’évaluation et de production, vérifiez la configuration dans l’administration Commerce pour chaque environnement :

1. Connectez-vous à Admin Console pour l’évaluation et la production à l’aide de l’URL avec /admin (ou l’URL d’administration modifiée).
1. Accédez à Magasins > Configuration > Avancé > Système . Faites défiler l’écran et cliquez sur Cache de page complet.
1. Assurez-vous que Fast CDN est sélectionné.
1. Cliquez sur Configuration Fastly . Assurez-vous que l’identifiant du service Fastly et le jeton API Fastly sont saisis (vos informations d’identification Fastly). Vérifiez que vous avez saisi les informations d’identification appropriées pour l’environnement d’évaluation et de production. Cliquez sur Tester les informations d’identification pour obtenir de l’aide.
1. Modifiez votre fichier composer.json et assurez-vous que le module Fasty est inclus dans la version . Ce fichier contient tous les modules répertoriés avec les versions.

   * Dans la section « exiger », vous devriez avoir « fastly/magento2 » : `<version number>`
   * Dans la section « référentiels », vous devriez avoir :

   ```
   "fastly-magento2": {    "type": "vcs",    "url": "https://github.com/fastly/fastly-magento2.git"    }
   ```

1. Si vous utilisez Configuration Management, vous devez disposer d’un fichier de configuration. Modifiez le fichier app/etc/config.app.php (2.0, 2.1) ou app/etc/config.php (2.2) et assurez-vous que le paramètre `'Fastly_Cdn' => 1` est correct. Le paramètre ne doit pas être `'Fastly_Cdn' => 0` (c’est-à-dire désactivé). Si vous avez activé Fastly, supprimez le fichier de configuration et exécutez la commande bin/magento-cloud:scd-dump pour mettre à jour. Pour une présentation de ce fichier, consultez [Exemple de gestion des paramètres spécifiques au système](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=fr#manage-the-system-specific-configuration) dans le guide de configuration.

Si le module n’est pas installé, vous devez l’installer dans une branche [Environnement d’intégration](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27242) et la déployer dans les environnements d’évaluation et de production. Voir [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr) pour obtenir des instructions dans le guide Commerce sur les infrastructures cloud.

### Fastly-Magento-VCL-Uploaded est absent

Lors de l’installation et de la configuration, vous devez avoir téléchargé le Fastly VCL. Il s’agit des fragments de code VCL de base fournis par le module Fastly , et non des fragments de code VCL personnalisés que vous créez. Pour obtenir des instructions, consultez [Chargement rapide de fragments de code VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr#upload-vcl-to-fastly) dans le Guide de Commerce sur les infrastructures cloud.

### X-Cache inclut MISS

Si X-Cache est HIT, MISS ou MISS, MISS, saisissez à nouveau la même commande curl pour vous assurer que la page n&#39;a pas été récemment expulsée du cache.

Si vous obtenez le même résultat, utilisez les commandes curl et vérifiez les en-têtes de réponse :

* Le paramètre est le cache
* X-Magento-Tags existe
* Contrôle de cache : l’âge maximal est supérieur à 0

Si le problème persiste, une autre extension réinitialise probablement ces en-têtes. Répétez la procédure suivante dans Évaluation pour désactiver les extensions afin de trouver celle qui cause le problème. Après avoir localisé la ou les extensions à l’origine du problème, vous devez désactiver la ou les extensions dans Production.

1. Pour désactiver les extensions, suivez les étapes décrites dans la section [Gérer les extensions](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html?lang=fr#manage-extensions) du guide Commerce sur les infrastructures cloud.
1. Après avoir désactivé les extensions, accédez à **[!UICONTROL System]** > **[!UICONTROL Tools]** > **[!UICONTROL Cache Management]**.
1. Cliquez sur **[!UICONTROL Flush Magento Cache]**.
1. Activez maintenant une extension à la fois, ce qui permet d’enregistrer la configuration et de vider le cache.
1. Exécutez les commandes curl et vérifiez les en-têtes de réponse.
1. Répétez les étapes 4 et 5 pour activer et tester les commandes curl. Lorsque les en-têtes Fastly ne s’affichent plus, vous avez trouvé l’extension à l’origine de problèmes avec Fastly.

Lorsque vous isolez l’extension qui réinitialise les en-têtes Fastly, contactez le développeur d’extensions pour obtenir une assistance supplémentaire. Nous ne pouvons pas fournir de correctifs ou de mises à jour pour que les développeurs d’extensions tiers travaillent avec la mise en cache Fastly.

## Pour plus d’informations, consultez notre documentation destinée aux développeurs :

* [À propos de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=fr)
* [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr)
* [Extraits personnalisés Fastly VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=fr)
