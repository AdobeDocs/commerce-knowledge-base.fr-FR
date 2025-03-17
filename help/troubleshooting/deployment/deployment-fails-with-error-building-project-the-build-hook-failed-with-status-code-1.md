---
title: 'Échec du déploiement avec « Erreur de création du projet : le hook de création a échoué avec le code d’état 1 »'
description: 'Cet article aborde les causes et les solutions du problème d’infrastructure cloud d’Adobe Commerce, où la phase de création du processus de déploiement échoue et le message d’erreur est résumé avec : *« Erreur de création du projet : le hook de création a échoué avec le code d’état 1 »*.'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 6a880a57c6cafb34fa51706f7bab1e23310bcef7
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# Échec du déploiement avec « Erreur de création du projet : le hook de création a échoué avec le code d’état 1 »

Cet article aborde les causes et les solutions du problème d’infrastructure cloud d’Adobe Commerce, où la phase de création du processus de déploiement échoue et le message d’erreur est résumé avec : *« Erreur de création du projet : le hook de création a échoué avec le code d’état 1 »*.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes versions confondues

## Problème

<u>Procédure à suivre </u> :

Déclenchez le déploiement manuellement ou en exécutant une fusion, une notification push ou une synchronisation de votre environnement.

<u>Résultat attendu </u> :

Le déploiement est terminé.

<u>Résultat réel</u> :

1. La phase de création échoue et l’ensemble du processus de déploiement est bloqué.
1. Dans le journal des erreurs de déploiement, le message d’erreur se termine par : *« Erreur lors de la création du projet : Le hook de build a échoué avec le code d’état 1. Abandon du build ».*

## Cause

Plusieurs raisons expliquent l’échec de la création d’environnements. En règle générale, dans le journal de déploiement, un long message d’erreur s’affiche, où la première partie est plus spécifique en ce qui concerne la raison, et la conclusion est *« Erreur lors de la création du projet : le hook de build a échoué avec le code d’état 1. Abandon du build ».*

Examiner de plus près la première partie spécifique au problème vous aidera à identifier le problème. Voici les plus courantes et la section suivante fournit des solutions pour elles :

* Il n’y a pas d’espace de stockage disponible.
* Configuration CEE-Outils incorrecte.
* Le correctif que vous essayez d’appliquer est incompatible avec votre version d’Adobe Commerce ou est en conflit avec d’autres correctifs appliqués ou avec vos personnalisations.
* Des problèmes liés au code des modules personnalisés empêchent la création réussie.

## Solution

* Vérifiez que l’espace de stockage est suffisant. Pour plus d’informations sur la vérification de l’espace disponible, consultez l’article [Vérification de l’espace disque dans un environnement cloud à l’aide de l’interface de ligne de commande](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md). Vous pouvez envisager de nettoyer les répertoires de journaux et/ou d’augmenter l’espace disque.
* S&#39;assurer que les outils ECE sont correctement configurés.
* Vérifiez si c’est le correctif qui cause le problème. Résolvez le conflit ou contactez l’assistance [Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Voir ci-dessous pour plus de détails.
* Vérifiez si c’est l’extension personnalisée qui cause le problème. Résolvez le conflit ou contactez les développeurs d’extensions pour obtenir la solution.

Les paragraphes suivants apportent des détails supplémentaires.

### Nettoyage des journaux et/ou augmentation de l’espace

Répertoires à prendre en compte pour le nettoyage :

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Pour plus d’informations sur la manière d’augmenter l’espace disque si vous vous trouvez dans l’architecture du plan de démarrage d’Adobe Commerce sur l’infrastructure cloud, consultez le [Augmentation de l’espace disque pour l’environnement d’intégration sur le cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). Les mêmes instructions peuvent être utilisées pour augmenter l’espace d’Adobe Commerce sur l’infrastructure cloud dans l’environnement d’intégration d’architecture Pro. Pour la production/l&#39;évaluation Pro, vous devez déposer un ticket auprès de [l&#39;assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et demander un espace disque plus important. Mais il est surveillé par Platform. Mais en règle générale, vous n’aurez pas à gérer cela dans l’architecture d’évaluation/de production de Pro, car Adobe Commerce surveille ces paramètres pour vous et vous avertit et/ou prend des mesures conformément au contrat.

### S&#39;assurer que les outils CEE sont correctement configurés

1. Assurez-vous que les hooks de build sont correctement définis dans le fichier `magento.app.yaml`. Si vous utilisez Adobe Commerce 2.2.X, les hooks de création doivent être définis comme suit :

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Utilisez l’article [Mise à niveau vers ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) pour référence.

1. Assurez-vous que le package ECE-tools est présent dans le fichier `composer.lock` en exécutant la commande suivante :

   ```bash
   grep '"name": "magento/ece-tools"' composer.lock
   ```

   S’ils sont spécifiés, la réponse ressemble à l’exemple suivant :

   ```bash
   "name": "magento/ece-tools", "version": "2002.0.20",
   ```

Consultez l’article [Mise à niveau vers ece-tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/install-package) pour plus de référence.

### Le correctif est-il à l’origine du problème ?

Si c’est le correctif appliqué qui empêche la création réussie de l’environnement, un élément similaire à ce qui suit s’affiche dans le journal de déploiement :

```bash
%patch_name%.composer.patch
[2019-02-19 18:12:59] CRITICAL:
....
[2019-02-19 18:12:59] CRITICAL: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
...
W:
W: Command git apply --check --reverse /app/m2-hotfixes/%patch_name%.composer.patch returned code 1
W:
W:
W: build
...
E: Error building project: The build hook failed with status code 1. Aborted build.
```

Ces messages d’erreur signifient que le correctif que vous essayez d’appliquer a été créé pour une autre version d’Adobe Commerce ou est en conflit avec vos personnalisations ou les correctifs précédemment appliqués. Essayez de résoudre le conflit ou contactez [l’assistance Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### L’extension est-elle à l’origine du problème ?

Si c’est l’extension personnalisée qui empêche la création réussie de l’environnement, le ou les noms des modules personnalisés mentionnés dans le journal de déploiement, ainsi que le conflit particulier causé par ce module, s’affichent. Résolvez le conflit ou contactez les développeurs d’extensions pour obtenir la solution.

### Vérifiez que les modifications sont appliquées.

Validez et envoyez vos modifications. Cela déclenchera automatiquement le déploiement.
