---
title: "Adobe Commerce sur site 2.4.2 : image du produit manquante"
description: Cet article décrit un problème connu d’Adobe Commerce sur site 2.4.2, en raison duquel l’image du produit n’est pas téléchargée sur la page du produit. Ce problème devrait être résolu dans une version ultérieure à la version 2.4.3. Aucune solution n’est disponible pour l’instant, mais vous pouvez désactiver Nginx pour redimensionner les images.
exl-id: c4d9240e-5df5-4eab-bb4e-1f06f9bd3a1e
feature: Iaas, Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Adobe Commerce sur site 2.4.2 : image du produit manquante

Cet article décrit un problème connu d’Adobe Commerce sur site 2.4.2, en raison duquel l’image du produit n’est pas téléchargée sur la page du produit. Ce problème devrait être résolu dans une version ultérieure à la version 2.4.3. Aucune solution n’est disponible pour l’instant, mais vous pouvez désactiver Nginx pour redimensionner les images.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.2

## Problème

L’image du produit est enregistrée dans le compartiment `s3`, mais elle n’est pas resynchronisée dans le répertoire `pub/media`. Ce problème survient uniquement lors de l’utilisation des deux :

* Nginx activé par le site pour redimensionner les images
* AWS `s3` en tant que stockage multimédia

<u>Conditions préalables</u> :

Adobe Commerce installé avec Nginx.

<u>Étapes à reproduire</u> :

1. Configurez Adobe Commerce pour utiliser AWS `s3` comme stockage multimédia.
1. Configurez Nginx à l’aide du fichier de configuration `nginx.conf.sample` fourni dans le répertoire d’installation d’Adobe Commerce et d’un hôte virtuel Nginx. Voir [Configuration de Nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html#configure-nginx-ubuntu) dans notre documentation destinée aux développeurs.
1. Créez un produit simple avec une image de produit.
1. Nginx possède une configuration non commentée pour le redimensionnement d’image dans `nginx.conf.sample` similaire à celle-ci :

```conf
load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
location /media/ {
    location ~* ^/media/catalog/.* {
        set $width "-";
        set $height "-";
        if ($arg_width != '') {
            set $width $arg_width;
        }
        if ($arg_height != '') {
            set $height $arg_height;
        }
        image_filter resize $width $height;
        image_filter_jpeg_quality 90;
    }
```

<u>Résultats attendus</u> :

L’image du produit est téléchargée sur la page du produit.

<u>Résultats réels</u> :

L’image du produit n’est pas téléchargée sur la page du produit.

## Solution

Désactivez Nginx pour redimensionner les images.
