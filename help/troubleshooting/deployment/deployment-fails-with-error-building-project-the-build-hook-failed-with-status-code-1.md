---
title: '"Échec du déploiement avec le message "Erreur lors de la création du projet : le crochet de génération a échoué avec le code d’état 1""'
description: '"Cet article décrit les causes et les solutions du problème d’infrastructure du cloud d’Adobe Commerce, où la phase de génération du processus de déploiement échoue, et le message d’erreur est résumé par : *"Projet de création d’erreur : le crochet de génération a échoué avec le code d’état 1"*."'
exl-id: add1cdac-dbcb-4c55-8bc2-c1f27e24aadb
feature: Build, Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# Échec du déploiement avec &quot;Projet de création d’erreur : le crochet de génération a échoué avec le code d’état 1&quot;

Cet article décrit les causes et les solutions du problème d’infrastructure du cloud d’Adobe Commerce, où la phase de génération du processus de déploiement échoue, et le message d’erreur est résumé avec : *&quot;Error building project: The build hook failed with status code 1&quot;*.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les versions

## Problème

<u>Étapes à reproduire</u> :

Déclenchez le déploiement manuellement ou en effectuant une fusion, une notification push ou une synchronisation de votre environnement.

<u>Résultat attendu</u> :

Le déploiement est terminé avec succès.

<u>Résultat réel</u> :

1. La phase de création échoue et l’ensemble du processus de déploiement est bloqué.
1. Dans le journal des erreurs de déploiement, le message d’erreur se termine par : *&quot;Error building project : The build hook failed with status code 1. Version abandonnée&quot;.*

## Cause

La création d’environnement échoue pour plusieurs raisons. En règle générale, dans le journal de déploiement, un long message d’erreur s’affiche, où la première partie est plus précise sur la raison et la conclusion est *&quot;Error building project : The build hook failed with status code 1 (Échec du crochet de création avec le code d’état). Version abandonnée&quot;.*

En regardant de plus près la première partie spécifique au problème, vous pouvez identifier le problème. Voici les solutions les plus courantes. La section suivante propose des solutions :

* Il n’y a pas d’espace de stockage disponible.
* Configuration d’outils ECG incorrecte.
* Le correctif que vous essayez d’appliquer est incompatible avec votre version d’Adobe Commerce ou est en conflit avec d’autres correctifs appliqués pour vos personnalisations.
* Les problèmes liés au code de modules personnalisé empêchent la création.

## Solution

* Vérifiez que le stockage est suffisant. Pour plus d’informations sur la façon de vérifier l’espace disponible, reportez-vous à l’article [Vérification de l’espace disque dans l’environnement cloud à l’aide de l’interface de ligne de commande](/help/how-to/general/check-disk-space-on-cloud-environment-using-cli.md) . Vous pouvez envisager de nettoyer les répertoires du journal et/ou d’augmenter l’espace disque.
* Assurez-vous que les outils ETC sont correctement configurés.
* Vérifiez si c’est le correctif qui cause le problème. Résolvez le conflit ou contactez le [support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). Voir ci-dessous pour plus de détails.
* Vérifiez si c’est l’extension personnalisée qui cause le problème. Résolvez le conflit ou contactez les développeurs d’extensions pour la solution.

Les paragraphes suivants fournissent des détails supplémentaires.

### Nettoyer les journaux et/ou augmenter l’espace

Répertoires à considérer pour le nettoyage :

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Pour plus d’informations sur la façon d’augmenter l’espace disque si vous utilisez l’architecture du plan de démarrage de l’infrastructure cloud d’Adobe Commerce, consultez la section [Augmentation de l’espace disque pour l’environnement d’intégration sur le cloud](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md). Les mêmes instructions peuvent être utilisées pour augmenter l’espace d’Adobe Commerce dans l’environnement d’intégration de l’architecture de plan d’infrastructure cloud Pro. Pour Pro Production/Staging, vous devez déposer un ticket auprès du [support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) et demander un espace disque supplémentaire. Mais il est surveillé par Platform. En règle générale, vous n’aurez pas à gérer cela sur l’architecture intermédiaire/production de Pro, car Adobe Commerce surveille ces paramètres pour vous et vous alerte et/ou prend des mesures conformément au contrat.

### Assurez-vous que les outils EEC sont correctement configurés.

1. Assurez-vous que les hooks de génération sont correctement définis dans le fichier `magento.app.yaml`. Si vous utilisez Adobe Commerce 2.2.X, les crochets de création doivent être définis comme suit :

   ```yaml
   # We run build hooks before your application has been packaged.
   build: |
       php ./vendor/bin/ece-tools build
   # We run deploy hook after your application has been deployed and started.
   deploy: |
       php ./vendor/bin/ece-tools deploy
   ```

   Utilisez l’article [Mise à niveau vers ece-tools](https://devdocs.magento.com/guides/v2.3/cloud/project/ece-tools-upgrade-project.html) à titre de référence.

1. Assurez-vous que le package EC-tools est présent dans le fichier `composer.lock` en exécutant la commande suivante :    <pre><code class="language-bash">grep &#39;<code class="language-yaml">&quot;name&quot;: &quot;magento/ece-tools&quot;</code>&#39; compositeur.lock</code></pre>    Si elles sont spécifiées, la réponse ressemblerait à l’exemple suivant :    ```bash    "name": "magento/ece-tools",    "version": "2002.0.20",    ```

Voir l’article [Mise à niveau vers les outils de texte](https://devdocs.magento.com/guides/v2.3/cloud/project/ece-tools-upgrade-project.html) pour référence.

### Le correctif est-il à l’origine du problème ?

Si c’est le correctif appliqué qui empêche la création de l’environnement, vous verrez quelque chose de similaire à ce qui suit dans le journal de déploiement :

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

Ces messages d’erreur signifient que le correctif que vous essayez d’appliquer a été créé pour une autre version d’Adobe Commerce ou qu’il est en conflit avec vos personnalisations ou les correctifs précédemment appliqués. Essayez de résoudre le conflit ou contactez le [support Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

### L’extension est-elle à l’origine du problème ?

Si c’est l’extension personnalisée qui empêche la création de l’environnement, le(s) nom(s) du(s) module(s) personnalisé(s) mentionné(s) dans le journal de déploiement, ainsi que le conflit particulier provoqué par ce module, s’affiche. Résolvez le conflit ou contactez les développeurs d’extensions pour la solution.

### Assurez-vous que les modifications sont appliquées.

Validez et poussez vos modifications. Cela déclenche automatiquement le déploiement.
