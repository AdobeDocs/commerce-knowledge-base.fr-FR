---
title: Erreur "Impossible d’enregistrer la classe dans le répertoire de code"
description: Cet article décrit comment résoudre le problème en raison duquel la manière dont vous avez spécifié les dépendances empêche la génération automatique des classes à la volée et vous obtenez le message d’erreur *"La classe ne peut pas être enregistrée dans le répertoire généré/code"*.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Erreur &quot;Impossible d’enregistrer la classe dans le répertoire de code&quot;

Cet article décrit comment résoudre le problème en raison duquel la manière dont vous avez spécifié les dépendances empêche la génération automatique des classes à la volée et vous obtenez le message d’erreur *&quot;Class can be save in the generated/code directory&quot;* (La classe ne peut pas être enregistrée dans le répertoire généré/code&quot;).

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.0 ou version ultérieure

## Problème

<u>Étapes à reproduire</u>

1. Dans votre environnement local, écrivez une classe personnalisée avec une dépendance sur la classe générée automatiquement.
1. Exécutez le scénario, où votre classe personnalisée est déclenchée, et vérifiez qu’elle fonctionne correctement.
1. Validez et envoyez vos modifications à l’environnement d’intégration. Cela déclencherait le processus de déploiement. Le déploiement a réussi.
1. Dans l&#39; [environnement d&#39;intégration](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), exécutez le scénario où votre classe personnalisée est déclenchée.

<u>Résultat attendu</u>

Tout fonctionne correctement, de la même manière que dans votre environnement local.

<u>Résultat réel</u>

Échec avec le message d’erreur indiquant que votre classe ne peut pas être enregistrée dans le répertoire `generated/code`.

## Cause

La cause du problème est que la classe sur laquelle vous avez une dépendance, n’est pas générée pendant le déploiement et ne peut pas être générée ultérieurement à la volée lorsque la classe est déclenchée, car le répertoire `generated/code` n’est pas disponible pour écriture une fois le déploiement terminé.

Deux raisons principales peuvent expliquer cette situation :

* Cas 1 : la classe avec des dépendances sur les classes générées automatiquement se trouve dans le point d’entrée (comme `index.php` ), qui n’est pas analysé pour les dépendances lors du déploiement.
* Cas 2 : la dépendance à la classe générée automatiquement est spécifiée directement (par rapport à l’utilisation recommandée du constructeur pour déclarer la dépendance).

## Solution

Une solution courante pour les deux cas serait de créer une véritable usine au lieu de la classe générée automatiquement.

Ou il existe une solution particulière pour chaque cas.

### Solution spécifique au cas 1

Déplacez le code de classe du point d’entrée vers un module distinct, puis utilisez-le dans le point d’entrée.

<u>Exemple</u>

Code d’origine dans, par exemple, `index2.php` :

```php
<?php
use YourVendor\SomeModule\Model\GeneratedFactory;

require realpath(__DIR__) . '/../app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);

class SomeClass
{
    private $generatedFactory;

    public function __construct(GeneratedFactory $generatedFactory)
    {
        $this->generatedFactory = $generatedFactory;
    }

// Some code here...
}

$someObject = $bootstrap->getObjectManager()->create(SomeClass::class);

// There is some code that uses $someObject
```

Vous devez effectuer les étapes suivantes :

1. Déplacez la définition de classe vers `app/code/YourVendor/YourModule` :

   ```php
      <?php
       namespace YourVendor\YourModule;
       use YourVendor\YourModule\Model\GeneratedFactory;
       class YourClass
       {
           private $generatedFactory;
   
           public function __construct(GeneratedFactory $generatedFactory)
           {
               $this->generatedFactory = $generatedFactory;
           }
       // Some code here...
       }
   ```

1. Modifiez le point d’entrée `my_api/index.php` de sorte qu’il ressemble à ce qui suit :

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### Solution spécifique à Cas 2

Déplacez la déclaration de dépendance vers le constructeur.

<u>Exemple</u>

Déclaration de classe d’origine :

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\SomeModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam)
    {
        $this--->someParam = $someParam;
        $this->generatedFactory = ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

Vous devez modifier son constructeur comme suit :

```php
<?php
namespace YourVendor\YourModule;

use YourVendor\YourModule\Model\GeneratedFactory;
use Magento\Framework\App\ObjectManager;

class YourClass
{
    private $generatedFactory;
    private $someParam;

    public function __construct($someParam, GeneratedFactory $generatedFactory = null)
    {
        $this->someParam = $someParam;
        $this->generatedFactory = $generatedFactory ?: ObjectManager::getInstance()->get(GeneratedFactory::class);
    }

    // Some code here...
}
```

## Lecture connexe

* [Génération de code](https://developer.adobe.com/commerce/php/development/components/code-generation/) dans notre documentation destinée aux développeurs.
