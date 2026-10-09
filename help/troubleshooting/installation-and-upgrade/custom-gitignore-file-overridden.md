---
title: La commande d’installation du compositeur remplace le fichier .gitignore, Adobe Commerce
description: Cet article fournit une solution pour le remplacement d’un fichier suivi « .gitignore » par le compositeur sur Adobe Commerce sur les infrastructures cloud 2.4.2-p1 et 2.3.7.
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%
---
# La commande d’installation du compositeur remplace le fichier .gitignore, Adobe Commerce

Cet article fournit une solution pour le remplacement d’un fichier `.gitignore` suivi par le compositeur sur Adobe Commerce sur les infrastructures cloud 2.4.2-p1 et 2.3.7.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud 2.4.2-p1 et 2.3.7.

## Problème

`.gitignore` fichier est remplacé lors de l&#39;exécution de la commande d&#39;installation du compositeur.

<u>Procédure à suivre </u> :


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

<u>Résultat attendu </u> :

`.gitignore` n’est pas remplacé par le compositeur.

<u>Résultat réel</u> :

`.gitignore` est remplacé par chaque exécution d&#39;installation du compositeur.

## Solution

Pour conserver votre `.gitignore file` personnalisé, vous devez l’ignorer dans la section `magento-deploy-ignore` .

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

* [Le fichier .gitignore suivi est remplacé par le compositeur !](https://github.com/magento/magento2/issues/32888) dans Magento2 GitHub.
