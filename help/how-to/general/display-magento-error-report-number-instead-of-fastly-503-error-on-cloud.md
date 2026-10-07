---
title: Afficher le numéro de rapport d’erreur Adobe Commerce au lieu de l’erreur Fastly 503
description: 'Par défaut, Fastly masque toutes les erreurs Adobe Commerce derrière l’erreur Service **503 indisponible** . Pour afficher le numéro de rapport du journal des erreurs d’Adobe Commerce (pour pouvoir le retrouver dans les journaux et consulter les détails de l’erreur), ouvrez le site web en omettant Fastly et procédez comme suit :'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# Afficher le numéro de rapport d’erreur Adobe Commerce au lieu de l’erreur Fastly 503

Par défaut, Fastly masque toutes les erreurs Adobe Commerce derrière l’erreur Service **503 indisponible** . Pour afficher le numéro de rapport du journal des erreurs d’Adobe Commerce (pour pouvoir le retrouver dans les journaux et consulter les détails de l’erreur), ouvrez le site web en omettant Fastly et procédez comme suit :

1. Ajoutez le domaine et l’adresse IP de votre application à votre fichier d’hôtes sur votre ordinateur local.
1. Effacez le cache et les cookies du navigateur (ou passez en mode navigation privée).
1. Ouvrez à nouveau le site web de votre boutique pour afficher l’erreur Adobe Commerce .

Une fois que l’erreur Adobe Commerce authentique et le numéro du rapport d’erreur s’affichent, vous pouvez obtenir des détails dans le fichier de rapport d’erreur en procédant comme suit :

1. SSH vers l’environnement affecté. Reportez-vous à la section [SSH vers un environnement](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) dans notre documentation destinée aux développeurs.
1. Recherchez le fichier `./var/report/{error_number}`.

## Ajout du domaine d’application et de l’adresse IP à votre fichier d’hôtes : étapes détaillées

1. Vérifiez l’adresse IP du serveur de votre magasin en exécutant la commande `nslookup` dans la ligne de commande sur votre ordinateur local :
   * Utilisateurs de l’architecture pro (environnements d’évaluation et de production) :

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Utilisateurs de l’architecture de démarrage (tous les environnements) ; utilisateurs de l’architecture Pro (environnement d’intégration) :

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Ajoutez le domaine de magasin et l’adresse IP du serveur d’applications au fichier d’hôtes sur votre ordinateur local au format suivant :

```
{server_IP} {store_domain}
```
