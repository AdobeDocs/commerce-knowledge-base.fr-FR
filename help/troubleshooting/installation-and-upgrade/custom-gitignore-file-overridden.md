---
title: La commande d’installation du compositeur remplace le fichier .gitignore, Adobe Commerce
description: Cet article fournit une solution pour le cas où un fichier &grave;.gitignore&grave; tracké est remplacé par le compositeur sur Adobe Commerce sur l’infrastructure cloud 2.4.2-p1 et 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# La commande d’installation du compositeur remplace le fichier .gitignore, Adobe Commerce

Cet article fournit une solution pour lorsqu’un fichier `.gitignore` tracké est remplacé par le compositeur sur Adobe Commerce sur l’infrastructure cloud 2.4.2-p1 et 2.3.7.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud 2.4.2-p1 et 2.3.7.

## Problème

Le fichier `.gitignore` est remplacé lors de l’exécution de la commande d’installation du compositeur.

<u>Étapes à reproduire</u> :


1. Créez un répertoire vide pour votre espace de travail.
1. Exécutez cette commande dans le répertoire racine :

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \# ou 2.3.7

1. Exécutez ensuite les commandes suivantes :
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` # fichier validé dans le référentiel
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>Résultat attendu</u> :

`.gitignore` n’est pas remplacé par le compositeur.

<u>Résultat réel</u> :

`.gitignore` est remplacé par chaque exécution d’installation de compositeur.

## Solution

Pour conserver votre `.gitignore file` personnalisé, vous devez l&#39;ignorer dans la section `magento-deploy-ignore` .

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## Lecture connexe

* [Le fichier .gitignore tracké est remplacé par le compositeur !](https://github.com/magento/magento2/issues/32888) dans Magento2 GitHub.
