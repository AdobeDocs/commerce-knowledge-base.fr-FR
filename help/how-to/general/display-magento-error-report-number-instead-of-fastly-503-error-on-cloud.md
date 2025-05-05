---
title: Afficher le numéro du rapport d’erreur Adobe Commerce au lieu de l’erreur Fastly 503
description: Par défaut, masque Fastly toutes les erreurs Adobe Commerce derrière l'erreur **503 Service indisponible**. Pour afficher le numéro du rapport du journal des erreurs Adobe Commerce (afin de pouvoir le trouver dans les logs et voir les détails de l’erreur), ouvrez le site web omettant Fastly en procédant comme suit :'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Afficher le numéro du rapport d’erreur Adobe Commerce au lieu de l’erreur Fastly 503

Par défaut, masque Fastly toutes les erreurs Adobe Commerce derrière l&#39;erreur **503 Service Unavailable** . Pour afficher le numéro du rapport du journal des erreurs Adobe Commerce (afin de pouvoir le trouver dans les logs et consulter les détails de l’erreur), ouvrez le site web omettant Fastly en procédant comme suit :

1. Ajoutez le domaine et l’adresse IP de votre application à votre fichier d’hôtes sur votre ordinateur local.
1. Effacez le cache du navigateur et les cookies (ou passez en mode incognito).
1. Ouvrez à nouveau le site web de votre boutique pour afficher l’erreur Adobe Commerce.

Une fois que vous avez identifié l’erreur Adobe Commerce authentique et le numéro du rapport d’erreur, vous pouvez obtenir les détails dans le fichier de rapport d’erreur en procédant comme suit :

1. SSH vers l’environnement concerné. Reportez-vous à la section [SSH to an environment](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/secure-connections) dans notre documentation destinée aux développeurs.
1. Recherchez le fichier `./var/report/{error_number}`.

## Ajoutez le domaine de l’application et l’adresse IP à votre fichier d’hôtes : étapes détaillées

1. Vérifiez l’adresse IP du serveur de votre magasin en exécutant la commande `nslookup` dans la ligne de commande de votre ordinateur local :
   * Pour les utilisateurs d’architecture (environnements d’évaluation et de production) :

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Utilisateurs d’architecture de départ (tous les environnements) ; Utilisateurs d’architecture Pro (environnement d’intégration) :

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Ajoutez le domaine de stockage et l’adresse IP du serveur d’applications au fichier hosts de votre ordinateur local au format suivant :

```
{server_IP} {store_domain}
```
