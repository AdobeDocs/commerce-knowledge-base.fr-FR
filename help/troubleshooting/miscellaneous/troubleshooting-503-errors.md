---
title: Dépannage de l’erreur 503 provoquée par la nécessité de modifier les paramètres de vernis par défaut
description: Cet article fournit des solutions pour le dépannage de l’erreur 503 provoquée par certaines valeurs par défaut du cache de vernis qui ne sont pas suffisantes pour votre magasin.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Dépannage de l’erreur 503 provoquée par la nécessité de modifier les paramètres de vernis par défaut

Cet article fournit des solutions pour le dépannage de l’erreur 503 provoquée par certaines valeurs par défaut du cache de vernis qui ne sont pas suffisantes pour votre magasin.

## Problème

Si la longueur des balises de cache utilisées par Adobe Commerce dépasse la valeur par défaut de 8 192 octets de Varnish, vous pouvez voir des erreurs HTTP 503 (Échec de la récupération du serveur principal) dans le navigateur. Les erreurs peuvent se présenter comme suit : *&quot;Erreur 503 - Échec de la récupération du serveur principal. Échec de la récupération du serveur principal&quot;*

## Solution

Pour résoudre ce problème, augmentez la valeur par défaut du paramètre `http_resp_hdr_len` dans votre fichier de configuration de vernis. Le paramètre `http_resp_hdr_len` spécifie la longueur maximale de l’en-tête *dans* la taille totale de réponse par défaut de 3 2768 octets.

>[!NOTE]
>
>Si la valeur `http_resp_hdr_len` dépasse 32 Ko, vous devez également augmenter la taille de réponse par défaut à l’aide du paramètre `http_resp_size` .

1. En tant qu’utilisateur disposant des privilèges `root`, ouvrez votre fichier de configuration de l’annulation dans un éditeur de texte :
   * CentOS 6 : `/etc/sysconfig/varnish`
   * CentOS 7 : `/etc/varnish/varnish.params`
   * Debian : `/etc/default/varnish`
   * Ubuntu : `/etc/default/varnish`
1. Recherchez le paramètre `http_resp_hdr_len` .
1. Si le paramètre n’existe pas, ajoutez-le après `thread_pool_max` .
1. Définissez `http_resp_hdr_len` sur une valeur égale au nombre de produits de votre catégorie la plus grande multipliée par 21. (Chaque balise de produit comporte environ 21 caractères.)    Par exemple, la définition de la valeur sur 6 536 octets doit fonctionner si votre catégorie la plus grande comporte 3 000 produits.    Par exemple :    ```conf    -p http_resp_hdr_len=65536 \    ```
1. Définissez `http_resp_size` sur une valeur qui prend en charge la longueur d’en-tête de réponse accrue.    Par exemple, l’utilisation de la somme de la longueur d’en-tête augmentée et de la taille de réponse par défaut est un bon point de départ (par exemple, 65536 + 32768 = 98304) : `-p http_resp_size=98304`. Voici un extrait de code :

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## Délais d’expiration des contrôles de l’intégrité {#health-check-timeouts}

Si vous désactivez le cache alors que Varnish est configuré comme application de mise en cache et qu’Adobe Commerce est en mode développeur, il peut devenir impossible de se connecter à l’administrateur.

Cette situation peut se produire, car le contrôle de l’intégrité par défaut a une valeur `timeout` de 2 secondes. Cela peut prendre plus de 2 secondes pour que le contrôle de l’intégrité collecte et fusionne les informations sur chaque demande de contrôle de l’intégrité. Si cela se produit dans 6 contrôles de l’intégrité sur 10, le serveur Adobe Commerce est considéré comme non sain. Le vernis diffuse du contenu obsolète lorsque le serveur n’est pas sain.

Comme l’accès à l’administrateur s’effectue par le biais du vernis, vous ne pouvez pas vous connecter à l’administrateur pour activer la mise en cache (sauf si Adobe Commerce est à nouveau en bonne santé). Cependant, vous pouvez utiliser la commande suivante pour activer le cache :

```bash
$ bin/magento cache:enable
```

Pour plus d&#39;informations sur l&#39;utilisation de la ligne de commande, voir [Prise en main de la configuration de ligne de commande](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli).
