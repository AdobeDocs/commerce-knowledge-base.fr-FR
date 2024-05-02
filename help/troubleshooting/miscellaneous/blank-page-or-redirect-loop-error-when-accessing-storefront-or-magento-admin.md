---
title: Erreur de page vierge ou de boucle de redirection lors de l’accès à storefront ou à l’administrateur Commerce
description: Cet article fournit une solution au problème lorsque vous accédez au storefront ou au serveur principal Adobe Commerce et que vous obtenez une page vierge ou une boucle de redirection.
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Erreur de page vierge ou de boucle de redirection lors de l’accès à storefront ou à l’administrateur Commerce

Cet article fournit une solution au problème lorsque vous accédez au storefront ou au serveur principal Adobe Commerce et que vous obtenez une page vierge ou une boucle de redirection.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions
* Adobe Commerce sur site, toutes versions
* Magento Open Source, toutes versions

## Problème

<u>Étapes à reproduire</u>

Ouvrez un storefront ou une page d’administration.

<u>Résultat attendu</u>

La page s’ouvre.

<u>Résultat réel</u>

La page est vierge ou affiche la variable *&quot;Cette page web comporte une boucle de redirection&quot;* message d’erreur.

## Cause

L’une des raisons les plus probables du problème est qu’Adobe Commerce est défini pour rediriger d’une URL non sécurisée vers une URL sécurisée, mais qu’une URL non sécurisée est fournie comme valeur pour le paramètre d’URL sécurisée.

Pour résoudre ce problème, vous devez corriger la valeur du lien sécurisé.

## Solution

Pour vous assurer qu’il s’agit de la cause du problème, procédez comme suit :

1. Vérifiez les `web/secure/enable_upgrade_insecure` , `web/secure/use_in_adminhtml` (si vous rencontrez un problème de redirection vide/boucle dans Admin) ou `web/secure/use_in_frontend` (si vous rencontrez le problème de redirection vide/boucle au recto de la boutique) dans la variable `'core_config_data'` Table DB.
   * If `web/secure/enable_upgrade_insecure` est définie sur &quot;1&quot;, puis Adobe Commerce est configuré pour ajouter l’en-tête de réponse. `Content-Security-Policy: upgrade-insecure-requests`, indiquant ainsi aux navigateurs d’utiliser HTTPS, redirigeant toutes les requêtes qui passent par HTTP vers HTTPS, tant pour l’administrateur que pour storefront.
   * If `web/secure/use_in_adminhtml` est définie sur &quot;1&quot;, Adobe Commerce renvoie des redirections HTTPS pour toutes les requêtes HTTP pour les pages d’administration.
   * If `web/secure/use_in_frontend` est définie sur &quot;1&quot;, Adobe Commerce renvoie des redirections HTTPS pour toutes les requêtes HTTP pour les pages frontales du magasin.
1. Vérifiez les `web/secure/base_url` et `web/unsecure/base_url` dans la variable `'core_config_data'` table. Si elles commencent toutes les deux par    `http`, vous devez ensuite corriger la valeur &quot;secure&quot;.

Correction du problème :

1. Définissez la valeur commençant par `https` pour `web/secure/base_url.`
1. Pour que les modifications soient appliquées, nettoyez le cache de configuration en exécutant la commande suivante :

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```
