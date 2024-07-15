---
title: Déploiement bloqué avec l’erreur "Impossible de charger l’application sur la grappe distante"
description: '"Cet article fournit une solution au problème Adobe Commerce, où le déploiement est bloqué, et le message d’erreur suivant se trouve dans le journal de déploiement : *"Erreur : impossible de charger l’application sur la grappe distante"*."'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Déploiement bloqué avec l’erreur &quot;Impossible de charger l’application sur la grappe distante&quot;

Cet article fournit une solution pour le problème Adobe Commerce, où le déploiement est bloqué, et le message d’erreur suivant se trouve dans le journal de déploiement : *&quot;Error: Impossible de charger l’application sur la grappe distante&quot;*.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

<u>Étapes à reproduire</u> :

Déclenchez le déploiement manuellement ou en effectuant une fusion, une notification push ou une synchronisation de votre environnement.

<u>Résultat attendu</u> :

Le déploiement est terminé avec succès.

<u>Résultat réel</u> :

Le déploiement est bloqué et dans le journal des erreurs de déploiement de l’interface utilisateur cloud, le message d’erreur suivant s’affiche : *&quot;Error: Impossible de charger l’application sur la grappe distante&quot; trouvée dans le journal de déploiement après l’échec du déploiement, le site peut afficher l’erreur &quot;503 first byte timeout&quot;*.

## Cause

Le problème est dû à la panne du stockage disponible.

## Solution

Vous pouvez envisager de nettoyer les répertoires du journal et/ou d’augmenter l’espace disque.

Répertoires à considérer pour le nettoyage :

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Pour plus d’informations sur la façon d’augmenter l’espace disque si vous utilisez l’architecture du plan de démarrage de l’infrastructure cloud d’Adobe Commerce, voir [Augmentation de l’espace disque pour l’environnement d’intégration sur le cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) dans notre base de connaissances de support. Les mêmes instructions peuvent être utilisées pour augmenter l’espace d’Adobe Commerce dans l’environnement d’intégration de l’architecture de plan pour l’infrastructure cloud Pro. Pour Pro Production/Staging, vous devez [déposer un ticket auprès du support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) et demander un espace disque supplémentaire. Mais en règle générale, vous n’aurez pas à traiter ce problème dans le plan d’évaluation/de production de Pro, car Adobe Commerce surveille ces paramètres pour vous et alerte et/ou prend des mesures conformément au contrat.
