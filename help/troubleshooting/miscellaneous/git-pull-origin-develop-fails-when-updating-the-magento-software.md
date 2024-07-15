---
title: Échec du développement de l’origine de l’extraction git lors de la mise à jour du logiciel Adobe Commerce
description: Cet article fournit un correctif pour les cas où vous ne pouvez pas mettre à jour le logiciel Adobe Commerce lors de l’exécution de "git pull origin development".
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Échec du développement de l’origine de l’extraction git lors de la mise à jour du logiciel Adobe Commerce

Cet article fournit un correctif pour les cas où vous ne pouvez pas mettre à jour le logiciel Adobe Commerce lors de l’exécution de `git pull origin develop`.

## Détails

L’une des étapes de mise à jour du logiciel Adobe Commerce consiste à mettre à jour votre référentiel local en exécutant :

```bash
$ git pull origin develop
```

L’erreur suivante peut s’afficher :

```terminal
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Pour identifier les fichiers susceptibles d’être remplacés, lisez le message ou saisissez :

```bash
git status
```

La section suivante aborde les solutions suggérées.

### Solutions proposées

Votre solution dépend du fait que vous ayez ou non intentionnellement modifié des fichiers dans le système de fichiers Adobe Commerce. Pour plus d’informations, reportez-vous à l’une des sections suivantes.

#### Vous avez intentionnellement modifié des fichiers

Résolvez manuellement les conflits de la manière habituelle. Si vous ne savez pas quoi faire, consultez l’[aide GitHub](https://help.github.com/).

#### Vous n’avez intentionnellement modifié aucun fichier.

Essayez l’une des méthodes suivantes :

* Si vous êtes certain que vous n’avez modifié aucun fichier et que vous n’avez aucun problème à supprimer ou à remplacer les modifications du système de fichiers Adobe Commerce, saisissez :

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Ensuite, continuez là où vous vous êtes arrêté avec votre mise à jour Adobe Commerce.

* Il est possible qu’un paramètre de configuration GitHub puisse empêcher ces erreurs à l’avenir. Par défaut, GitHub stocke le contenu à l’aide des caractères de fin de ligne par défaut du système d’exploitation. Si vous utilisez Linux, mais qu’un autre collaborateur a apporté une modification à l’aide de Windows, GitHub convertit les fins de ligne Windows en Linux lorsque vous clonez ou extrayez. Cela donne l’apparence d’une modification des fichiers alors qu’en fait, aucune modification n’a été apportée.

  Pour configurer GitHub afin d’ignorer les fins de ligne, saisissez la commande suivante dans votre client Git :

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Si vous utilisez Windows, saisissez :

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >Adobe ne recommande pas ou n’approuve aucun paramètre de configuration GitHub particulier. Les suggestions ci-dessus ne sont que des suggestions. Pour plus d’informations, consultez l’ [aide de GitHub](https://help.github.com/).

  Continuez là où vous vous êtes arrêté avec votre mise à jour d’Adobe Commerce.
