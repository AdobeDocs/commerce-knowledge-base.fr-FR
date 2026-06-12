---
title: Dépannage de l'erreur 503 causée par la nécessité de modifier les paramètres par défaut du vernis
description: Cet article fournit des solutions pour résoudre l’erreur 503 due au fait que certaines valeurs par défaut du cache de vernis ne suffisent pas pour votre magasin.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 40766238a7ea748bff86decf75cddec28fe63bb9
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Dépannage de l&#39;erreur 503 causée par la nécessité de modifier les paramètres par défaut du vernis

Cet article fournit des solutions pour résoudre l’erreur 503 due au fait que certaines valeurs par défaut du cache de vernis ne suffisent pas pour votre magasin.

## Problème

Si la longueur des balises de cache utilisées par Adobe Commerce dépasse la valeur par défaut de 8 192 octets de Varnish, vous pouvez voir les erreurs HTTP 503 (Backend Fetch Failed) dans le navigateur. Les erreurs peuvent se présenter comme suit : *« Erreur 503 Échec de la récupération du serveur principal. Échec de la récupération du serveur principal »*

## Solution

Pour résoudre ce problème, augmentez la valeur par défaut du paramètre `http_resp_hdr_len` dans votre fichier de configuration de vernis. Le paramètre `http_resp_hdr_len` spécifie la longueur maximale de l’en-tête *dans* la taille de réponse totale par défaut de 32768 octets.

>[!NOTE]
>
>Si la valeur `http_resp_hdr_len` dépasse 32 000, vous devez également augmenter la taille de réponse par défaut à l’aide du paramètre `http_resp_size` .

1. En tant qu’utilisateur disposant de droits d’`root`, ouvrez votre fichier de configuration Vanish dans un éditeur de texte :
   * CentOS 6 : `/etc/sysconfig/varnish`
   * CentOS 7 : `/etc/varnish/varnish.params`
   * Debian : `/etc/default/varnish`
   * Ubuntu : `/etc/default/varnish`
1. Recherchez le paramètre `http_resp_hdr_len` .
1. Si le paramètre n’existe pas, ajoutez-le après `thread_pool_max` .
1. Définissez `http_resp_hdr_len` sur une valeur égale au nombre de produits de la catégorie la plus volumineuse multiplié par 21. (Chaque balise de produit comporte environ 21 caractères.) Par exemple, la définition de la valeur sur 65536 octets doit fonctionner si votre catégorie la plus volumineuse comporte 3 000 produits. Par exemple : `-p http_resp_hdr_len=65536 \`
1. Définissez la `http_resp_size` sur une valeur qui prend en charge la longueur accrue de l’en-tête de réponse.    Par exemple, utiliser la somme de la longueur accrue de l’en-tête et de la taille de réponse par défaut est un bon point de départ (par exemple, 65536 + 32768 = 98304) : `-p http_resp_size=98304`. Voici un extrait de code :

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

## Délais d’expiration du contrôle d’intégrité {#health-check-timeouts}

Si vous désactivez le cache alors que Varnish est configuré comme application de mise en cache et qu’Adobe Commerce est en mode Développeur, il peut s’avérer impossible de se connecter à l’administrateur.

Cette situation peut se produire, car le contrôle d’intégrité par défaut a une valeur de `timeout` de 2 secondes. La collecte et la fusion des informations de chaque requête de contrôle d’intégrité peuvent prendre plus de 2 secondes pour le contrôle d’intégrité. Si cela se produit dans 6 contrôles d’intégrité sur 10, le serveur Adobe Commerce est considéré comme défectueux. Le vernis diffuse du contenu obsolète lorsque le serveur n’est pas intègre.

Comme l’accès à Admin s’effectue via Vernis, vous ne pouvez pas vous connecter à Admin pour activer la mise en cache (à moins qu’Adobe Commerce ne redevienne intègre). Vous pouvez toutefois utiliser la commande suivante pour activer le cache :

```bash
$ bin/magento cache:enable
```

Pour plus d’informations sur l’utilisation de la ligne de commande, voir [Prise en main de la configuration de ligne de commande](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cli/config-cli).
