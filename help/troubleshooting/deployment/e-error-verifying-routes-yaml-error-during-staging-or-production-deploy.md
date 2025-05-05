---
title: 'E : erreur de vérification des itinéraires.yaml lors du déploiement d’évaluation ou de production'
description: '"Cet article fournit une solution à Adobe Commerce pour le problème d’infrastructure cloud, où vous obtenez le message d’erreur *"E: Error while verifying routes.yaml"* lors de la tentative de déploiement du projet dans l’environnement d’évaluation ou de production."'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E : Erreur lors de la vérification de routes.yaml lors du déploiement d’évaluation ou de production

Cet article fournit une solution pour Adobe Commerce concernant le problème d’infrastructure cloud, où vous obtenez le message d’erreur *&quot;E: Error while verifying routes.yaml&quot;* lors de la tentative de déploiement du projet dans l’environnement d’évaluation ou de production.

## Versions affectées

* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

<u>Étapes à reproduire</u> :

Déclenchez un déploiement en poussant le code dans l’environnement d’évaluation ou de production.

<u>Comportement attendu</u> :

Le déploiement a réussi.

<u>Comportement réel</u> :

Le déploiement est bloqué et le message d&#39;erreur suivant s&#39;affiche dans le journal :

<pre>Déploiement des applications Vérification de la configuration E : erreur lors de la vérification de routes.yaml.
Les domaines suivants sont configurés pour votre grappe, mais aucun itinéraire n’est défini dans votre fichier routes.yaml :

&#x200B;- store1.example.com
&#x200B;- store2.example.com
&#x200B;- test-store.example.com

Avec votre configuration de routes.yaml actuelle,
  ces domaines ne seraient PAS servis !

Pour continuer, reportez-vous ici pour obtenir des instructions de dépannage :
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Cause

Cette erreur se produit si la configuration d’itinéraire pour tout domaine supplémentaire qui a été ajouté à votre projet est manquante dans le fichier `routes.yaml`.

Dans le cadre de la mise à niveau de l’activation en libre-service d’Adobe Commerce pour la configuration de l’itinéraire en libre-service, nous avons ajouté une vérification préalable au déploiement pour nous assurer que tous les domaines de votre projet ont des itinéraires configurés dans le fichier `routes.yaml`. Si la configuration d’itinéraire d’un domaine est manquante, le déploiement est bloqué.

## Solution

Pour résoudre le déploiement bloqué, mettez à jour le fichier `routes.yaml` afin de configurer les itinéraires pour les domaines répertoriés dans le message d’erreur en utilisant l’une des méthodes suivantes :

* Appliquez le correctif fourni par Adobe Commerce lors de la mise à niveau.
* Ajoutez manuellement la configuration d’itinéraire manquante au fichier `routes.yaml`.

### Méthode 1 : appliquez le correctif fourni par Adobe Commerce

1. Recherchez un ticket de support Adobe Commerce récent intitulé &quot;*Activer les fonctionnalités en libre-service pour &lt;project\_ID>&quot;.*
1. Suivez les instructions du ticket pour appliquer le correctif, qui met à jour la configuration de l’itinéraire pour votre environnement cloud.
1. С omettez et poussez les modifications pour redéployer votre projet.

### Méthode 2 : ajout manuel de la configuration d’itinéraire manquante

1. Pour desservir tous les domaines de votre projet en utilisant la même configuration d’itinéraire, mettez à jour le fichier `routes.yaml` en ajoutant des modèles d’itinéraire pour le domaine par défaut et tous les autres domaines de votre projet, comme illustré dans l’exemple suivant :

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. С omettez et poussez vos modifications pour redéployer votre projet.

Pour obtenir des instructions détaillées sur la mise à jour de la configuration de l’itinéraire, voir [Cloud for Adobe Commerce > Configurer les itinéraires](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml) dans notre documentation destinée aux développeurs.

>[!NOTE]
>
>Si votre configuration de projet spécifie les domaines qui ne sont plus utilisés, procédez comme suit pour les supprimer de votre projet dès que possible : 1. Envoyez un ticket d’assistance avec une liste de domaines à supprimer de vos environnements de projet. 2. Une fois que l’équipe d’assistance a supprimé les domaines, mettez à jour le fichier `routes.yaml` pour supprimer toute référence aux domaines obsolètes.
