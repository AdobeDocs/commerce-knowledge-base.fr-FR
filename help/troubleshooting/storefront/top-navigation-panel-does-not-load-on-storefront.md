---
title: Le panneau de navigation supérieur ne se charge pas sur le storefront
description: Cet article fournit des solutions de configuration aux problèmes ESI (Varnish Edge Side Includes), où le contenu de certaines pages, généralement le panneau de navigation supérieur, n’est pas affiché sur le storefront si Varnish est utilisé pour la mise en cache.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Le panneau de navigation supérieur ne se charge pas sur le storefront

Cet article fournit des solutions de configuration aux problèmes ESI (Varnish Edge Side Includes), où le contenu de certaines pages, généralement le panneau de navigation supérieur, n’est pas affiché sur le storefront si Varnish est utilisé pour la mise en cache.

## Produits et versions concernés

* Adobe Commerce 2.X.X
* Toutes les versions en vernis

## Problème

<u>Conditions préalables</u> :

Installez et configurez le vernis pour votre boutique Adobe Commerce.

<u>Étapes à reproduire</u> :

1. Allez à la vitrine.
1. Parcourez les pages du magasin.

<u>Résultats attendus</u> :

L’ensemble du contenu et tous les blocs de page se chargent correctement.

<u>Résultats réels</u> :

Notez que certains blocs de contenu, comme le panneau de navigation supérieur avec des catégories, ne se chargent pas. L’espace vierge s’affiche à la place.

## Cause

Les raisons possibles du problème sont les suivantes :

* Les balises d’inclusion ESI sont générées avec le protocole d’accès HTTPS, tandis que le vernis ne fonctionne qu’avec le protocole HTTP.
* Le vernis ne traite pas l’ESI dans JSON.
* Les en-têtes de réponse sont trop gros pour le vernis ; il ne peut pas les traiter.

## Solution

Pour résoudre les problèmes, vous devez effectuer une configuration de vernis supplémentaire et redémarrer Varnish.

1. En tant qu’utilisateur disposant de droits `root`, ouvrez votre fichier de configuration de l’espagnol dans un éditeur de texte. Pour plus d’informations sur l’emplacement de ce fichier pour différents systèmes d’exploitation, reportez-vous à la section [Modification de la configuration du système Varnish](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/config-varnish-server) dans la documentation destinée aux développeurs.
1. Dans le `DAEMON_OPTS variable`, ajoutez `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check`. Cela ressemblerait à ceci :

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Dans le fichier de configuration VCL, augmentez les en-têtes de réponse en augmentant les valeurs de ces paramètres : `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. Assurez-vous que les deux dernières ont des valeurs similaires.
1. Lorsque vous modifiez ce paramètre, vous devez exécuter `service varnish restart` pour que les modifications prennent effet.

## Lecture connexe

* [Configurez Varnish et votre serveur web](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/cache/config-varnish-server) dans notre documentation destinée aux développeurs.
* [&#128279;](https://varnish-cache.org/docs/5.1/reference/index.html)
