---
title: le développement de l’origine d’extraction git échoue lors de la mise à jour du logiciel Adobe Commerce
description: Cet article fournit un correctif pour les cas où vous ne pouvez pas mettre à jour le logiciel Adobe Commerce lors de l’exécution de « Git pull origin develop ».
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%
---
# le développement de l’origine d’extraction git échoue lors de la mise à jour du logiciel Adobe Commerce

Cet article fournit un correctif pour les cas où vous ne pouvez pas mettre à jour le logiciel Adobe Commerce lors de l’exécution de `git pull origin develop`.

## Détails

L’une des étapes de la mise à jour du logiciel Adobe Commerce consiste à mettre à jour votre référentiel local en exécutant :

```bash
$ git pull origin develop
```

L’erreur suivante peut s’afficher :

```bash
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Pour identifier les fichiers susceptibles d’être remplacés, lisez le message ou saisissez :

```bash
git status
```

La section suivante présente les solutions suggérées.

### Solutions suggérées

Votre solution dépend de si vous avez modifié intentionnellement ou non des fichiers dans le système de fichiers Adobe Commerce. Pour plus d’informations, consultez l’une des sections suivantes.

#### Vous avez intentionnellement modifié des fichiers

Résolvez les conflits manuellement de la manière habituelle. Si vous ne savez pas quoi faire, consultez [Aide GitHub](https://help.github.com/).

#### Vous n’avez intentionnellement modifié aucun fichier

Essayez l’une des méthodes suivantes :

* Si vous êtes certain de n’avoir modifié aucun fichier et que la suppression ou le remplacement des modifications dans le système de fichiers Adobe Commerce ne vous dérange pas, saisissez :

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Ensuite, reprenez là où vous en étiez avec votre mise à jour d’Adobe Commerce.

* Il est possible qu’un paramètre de configuration GitHub empêche ces erreurs à l’avenir. Par défaut, GitHub stocke le contenu à l’aide des caractères de fin de ligne par défaut du système d’exploitation. Si vous utilisez Linux, mais qu’un autre collaborateur a validé une modification à l’aide de Windows, GitHub convertit les fins de ligne Windows en Linux lorsque vous clonez ou extrayez. Cela donne l’apparence d’une modification des fichiers alors qu’en fait, aucune modification n’a été apportée.

  Pour configurer GitHub afin d’ignorer les fins de ligne, saisissez la commande suivante dans votre client Git :

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Si vous utilisez Windows, saisissez :

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >Adobe ne recommande ni n’endosse aucun paramètre de configuration GitHub particulier. Vous ne trouverez ci-dessus que des suggestions. Pour plus d’informations, consultez [Aide de GitHub](https://help.github.com/).

  Continuez là où vous en étiez avec votre mise à jour d’Adobe Commerce.
