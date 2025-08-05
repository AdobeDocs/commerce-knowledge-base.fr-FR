---
title: Erreur « La classe ne peut pas être enregistrée dans le répertoire de code »
description: Cet article décrit comment résoudre le problème où la manière dont vous avez spécifié les dépendances empêche la génération automatique des classes à la volée et où vous obtenez le message d’erreur *« La classe ne peut pas être enregistrée dans le répertoire généré/code »*.
exl-id: e2c00d4d-31c3-4446-a317-a8ac92c707d5
feature: Configuration
role: Developer
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Erreur « La classe ne peut pas être enregistrée dans le répertoire de code »

Cet article décrit comment résoudre le problème où la manière dont vous avez spécifié les dépendances empêche la génération automatique des classes à la volée et où vous obtenez le message d’erreur *« La classe ne peut pas être enregistrée dans le répertoire généré/code »*.

## Produits et versions concernés

* Adobe Commerce sur infrastructure cloud 2.2.0 ou version ultérieure

## Problème

<u>Procédure à suivre</u>

1. Dans votre environnement local, écrivez une classe personnalisée avec une dépendance sur la classe générée automatiquement.
1. Exécutez le scénario, où votre classe personnalisée est déclenchée, et vérifiez qu’elle fonctionne correctement.
1. Validez et envoyez vos modifications à l’environnement d’intégration. Cela déclencherait le processus de déploiement. Le déploiement a réussi.
1. Dans l’[environnement d’intégration](https://experienceleague.adobe.com/fr/docs/experience-cloud-kcs/kbarticles/ka-27242), exécutez le scénario dans lequel votre classe personnalisée est déclenchée.

<u>Résultat attendu</u>

Tout fonctionne correctement, de la même manière que dans votre environnement local.

<u>Résultat réel</u>

Échec avec le message d&#39;erreur indiquant que votre classe ne peut pas être enregistrée dans le répertoire `generated/code`.

## Cause

La cause du problème est que la classe dont vous avez une dépendance n’est pas générée pendant le déploiement et ne peut pas être générée ultérieurement à la volée lorsque la classe est déclenchée, car le répertoire `generated/code` n’est pas disponible pour l’écriture une fois le déploiement terminé.

Il existe deux principales raisons à cela :

* Cas 1 : la classe avec des dépendances sur des classes générées automatiquement se trouve dans le point d’entrée (comme `index.php` ), qui n’est pas analysé pour les dépendances pendant le déploiement.
* Cas 2 : la dépendance à la classe générée automatiquement est spécifiée directement (comparez à l’utilisation recommandée du constructeur pour déclarer une dépendance).

## Solution

Une solution commune pour les deux cas serait de créer une véritable usine au lieu de la classe auto-générée.

Ou il y a une solution particulière pour chaque cas.

### Solution spécifique au cas 1

Déplacez votre code de classe du point d’entrée vers un module distinct, puis utilisez-le dans le point d’entrée.

<u>Exemple</u>

Code d’origine dans , par exemple `index2.php` :

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

Procédez comme suit :

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

1. Modifiez la `my_api/index.php` du point d’entrée afin qu’elle ressemble à ce qui suit :

   ```php
     <?php
     use YourVendor\YourModule\YourClass;
         require realpath(__DIR__) . '/../app/bootstrap.php';
         $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
         $someObject = $bootstrap->getObjectManager()->create(YourClass::class);
     // Some code using $someObject
   ```

### Solution spécifique au cas 2

Déplacez la déclaration de dépendance vers le constructeur.

<u>Exemple</u>

Déclaration de classe originale :

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
