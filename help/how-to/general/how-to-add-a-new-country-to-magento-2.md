---
title: Comment ajouter un nouveau pays à Adobe Commerce
description: Cet article explique comment ajouter un pays qui n’est pas présent dans Adobe Commerce et la bibliothèque Zend Locale. Cela nécessite des modifications du code et de la base de données qui constituent des personnalisations du client selon les conditions de votre contrat. Veuillez noter que les exemples de matériaux inclus dans cet article sont fournis "TELS QUELS" sans aucune garantie de quelque type que ce soit. Ni Adobe ni aucune entité affiliée n’est tenue de conserver, corriger, mettre à jour, modifier, modifier ou de toute autre manière de prendre en charge ces documents. Nous décrirons ici les principes de base de ce qui doit être fait pour y parvenir.
exl-id: af499add-4966-4a3a-972a-62a34c169a1b
feature: Build, Cache
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 0%

---

# Comment ajouter un nouveau pays à Adobe Commerce

Cet article explique comment ajouter un pays qui n’est pas présent dans Adobe Commerce et la bibliothèque Zend Locale. Cela nécessite des modifications du code et de la base de données qui constituent des personnalisations du client selon les conditions de votre contrat. Veuillez noter que les exemples de matériaux inclus dans cet article sont fournis &quot;TELS QUELS&quot; sans aucune garantie de quelque type que ce soit. Ni Adobe ni aucune entité affiliée n’est tenue de conserver, corriger, mettre à jour, modifier, modifier ou de toute autre manière de prendre en charge ces documents. Nous décrirons ici les principes de base de ce qui doit être fait pour y parvenir.

Dans cet exemple, nous créons un nouveau module Adobe Commerce avec un correctif de données qui est appliqué au processus d’installation ou de mise à niveau d’Adobe Commerce et ajoute un Pays abstrait avec le code de pays XX à Adobe Commerce. Le [répertoire Adobe Commerce](https://developer.adobe.com/commerce/php/module-reference/module-directory/) crée une première liste de pays, puis il utilise des correctifs de configuration pour ajouter des territoires à cette liste. Cet article explique comment créer un nouveau module qui ajoutera un nouveau pays à la liste. Vous pouvez consulter le code du module de répertoire Adobe Commerce existant à titre de référence. Cela est dû au fait que l’exemple de module suivant poursuit la tâche du module Répertoire de création d’une liste de pays et de régions et réutilise des parties du code du module de configuration de correctifs du module d’annuaire Adobe Commerce.

## Documentation recommandée

Pour en créer un nouveau, vous devez maîtriser le développement de module Adobe Commerce.

Reportez-vous aux rubriques suivantes de notre documentation destinée aux développeurs avant de tenter de créer un nouveau module :

* [Guide du développeur PHP](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/bk-extension-dev-guide.html)
* [Présentation du module](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html)
* [Créer un module](https://devdocs.magento.com/videos/fundamentals/create-a-new-module/)
* [ Fichiers de configuration de module](https://devdocs.magento.com/guides/v2.4/config-guide/config/config-files.html)

## Informations requises

Un nouveau pays doit posséder un nom, un ID de pays, des codes ISO2 et ISO3 uniques dans Adobe Commerce.

## Structure du module

Dans cet exemple, nous allons créer un module appelé \`ExtraCountries\` avec la structure de répertoires suivante :

(Pour en savoir plus sur la structure des modules, consultez la [présentation des modules](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html) dans notre documentation destinée aux développeurs).

<pre><ExtraCountries>
 |
 <etc>
 | |
 | config.xml
 | di.xml
 | module.xml
 |
 <Plugin>
 | |
 | <Framework>
 |   |
 |   <Locale>
 |     |
 |     TranslatedListsPlugin.php
 |
 <Setup>
 | |
 | <Patch>
 |   |
 |   <Data>
 |     |
 |     AddDataForAbstractCountry.php
 |
 compositeur.json
 registration.php</pre>

>[!NOTE]
>
>Chaque section Header de cet article décrit les fichiers de la section de structure de module.

## ExtraCountries/etc/config.xml

Une nouvelle configuration de module est définie dans ce fichier XML. Les configurations et balises suivantes peuvent être modifiées afin d’ajuster les nouveaux paramètres par défaut de pays.

* `allow` - Pour ajouter par défaut le pays nouvellement ajouté à la liste &quot;Autoriser les pays&quot;, ajoutez le nouveau code pays à la fin du contenu de la balise `allow`. Les codes pays sont séparés par des virgules. Notez que cette balise va remplacer les données de la balise `Directory` de configuration de module *(Directory/etc/config.xml)* `allow`. C’est pourquoi nous répétons tous les codes ici et ajoutons le nouveau.
* `optional_zip_countries` - Si le code postal du pays nouvellement ajouté doit être facultatif, ajoutez le code pays à la fin du contenu de la balise `optional_zip_countries`. Les codes pays sont séparés par des virgules. Notez que cette balise va remplacer les données de la balise `Directory` de configuration de module *(Directory/etc/config.xml)* `optional_zip_countries`. C’est pourquoi nous répétons tous les codes ici et ajoutons le nouveau.
* `eu_countries` - Si le pays nouvellement ajouté doit faire partie de la liste Pays de l’Union européenne par défaut, ajoutez le code pays à la fin du contenu de la balise `eu_countries` . Les codes pays sont séparés par des virgules. Notez que cette balise va remplacer les données du fichier de configuration de module `Store` *(\_Store/etc/config.xml\_)* `eu_countries`. C’est pourquoi nous répétons tous les codes ici et ajoutons le nouveau.
* Exemple de fichier `config.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <general>
            <country>
                <!-- append a new country codes to the end of this list -->
                <allow>AF,AL,DZ,AS,AD,AO,AI,AQ,AG,AR,AM,AW,AU,AT,AX,AZ,BS,BH,BD,BB,BY,BE,BZ,BJ,BM,BL,BT,BO,BQ,BA,BW,BV,BR,IO,VG,BN,BG,BF,BI,KH,CM,CA,CD,CV,KY,CF,TD,CL,CN,CX,CW,CC,CO,KM,CG,CK,CR,HR,CU,CY,CZ,DK,DJ,DM,DO,EC,EG,SV,GQ,ER,EE,ET,FK,FO,FJ,FI,FR,GF,PF,TF,GA,GM,GE,DE,GG,GH,GI,GR,GL,GD,GP,GU,GT,GN,GW,GY,HT,HM,HN,HK,HU,IS,IM,IN,ID,IR,IQ,IE,IL,IT,CI,JE,JM,JP,JO,KZ,KE,KI,KW,KG,LA,LV,LB,LS,LR,LY,LI,LT,LU,ME,MF,MO,MK,MG,MW,MY,MV,ML,MT,MH,MQ,MR,MU,YT,FX,MX,FM,MD,MC,MN,MS,MA,MZ,MM,NA,NR,NP,NL,AN,NC,NZ,NI,NE,NG,NU,NF,KP,MP,NO,OM,PK,PW,PA,PG,PY,PE,PH,PN,PL,PS,PT,PR,QA,RE,RO,RS,RU,RW,SH,KN,LC,PM,VC,WS,SM,ST,SA,SN,SC,SL,SG,SK,SI,SB,SO,ZA,GS,KR,ES,LK,SD,SR,SJ,SZ,SE,CH,SX,SY,TL,TW,TJ,TZ,TH,TG,TK,TO,TT,TN,TR,TM,TC,TV,VI,UG,UA,AE,GB,US,UM,UY,UZ,VU,VA,VE,VN,WF,EH,XK,YE,ZM,ZW,XX</allow>
​
                <!-- if added countries need to belong to the European Union Countries list by default, append their codes to the end of this list -->
                <eu_countries>AT,BE,BG,CY,CZ,DK,EE,FI,FR,DE,GR,HR,HU,IE,IT,LV,LT,LU,MT,NL,PL,PT,RO,SK,SI,ES,SE,GB,XX</eu_countries>
​
                <!-- if added countries are not require zip code, append it's code to the end of this list -->
                <optional_zip_countries>HK,IE,MO,PA,GB,XX</optional_zip_countries>
            </country>
        </general>
    </default>
</config>
```

Pour plus d’informations sur les fichiers de configuration de module, consultez le [Guide du développeur de PHP > Définir les fichiers de configuration](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/required-configuration-files.html) dans notre documentation du développeur.

Notez que ces modifications sont facultatives et n’affectent que l’appartenance par défaut du nouveau pays aux listes &quot;Autoriser les pays&quot;, &quot;Code postal facultatif pour&quot; et &quot;Pays de l’Union européenne&quot;. Si ce fichier est ignoré de la structure du module, un nouveau pays est toujours ajouté, mais il doit être configuré manuellement à l’adresse **Admin** > **Magasins** > *Paramètres* > **Configuration** > **Général** > **Options de pays** .

### ExtraCountries/etc/di.xml

Le fichier `di.xml` configure les dépendances qui sont injectées par le gestionnaire d’objets. Pour plus d&#39;informations sur `di.xml`, consultez le <a>Guide du développeur PHP > Le di.xml</a> dans la documentation destinée aux développeurs.

Dans notre exemple, nous devons enregistrer un `_TranslatedListsPlugin_` qui convertira les nouveaux codes pays en noms de pays complets si les codes ne figurent pas dans les données de localisation de la bibliothèque locale Zend.

Exemple `di.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\Framework\Locale\TranslatedLists">
        <plugin name="Magento_Directory" type="VendorName\ExtraCountries\Plugin\Framework\Locale\TranslatedListsPlugin"/>
    </type>
</config>
```

### ExtraCountries/etc/module.xml

Dans le fichier d’enregistrement du module, nous devons spécifier la dépendance pour le module &quot;Répertoire Adobe Commerce&quot;, en veillant à ce que le module &quot;Pays supplémentaires&quot; soit enregistré et exécuté après le module Répertoire.

Pour plus d’informations sur les dépendances de module, voir [Gestion des dépendances de module](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_depend.html#managing-module-dependencies) dans la documentation destinée aux développeurs.

Exemple `module.xml`

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="VendorName_ExtraCountries" >
        <sequence>
            <module name="Magento_Directory"/>
        </sequence>
    </module>
</config>
```

### ExtraCountries/Plugin/Framework/Locale/TranslatedListsPlugin.php

Dans la méthode de module externe `aroundGetCountryTranslation()`, nous devons traduire un code de pays en nom de pays complet. Il s’agit d’une étape requise pour les pays qui n’ont pas de nom complet associé à un nouveau code de pays dans la bibliothèque Zend Locale.

```php
<?php
namespace VendorName\ExtraCountries\Plugin\Framework\Locale;
​
use Magento\Framework\Locale\ListsInterface;
​
/**
 * Plugin to add full names of added countries that are not included in Zend Locale Data
 */
class TranslatedListsPlugin
{
    /**
     * Get the full name of added countries
     *
     * Since the locale data for the added country may not be present in the Zend Locale Library,
     * we need to provide full country name matching the added code
     *
     * @param ListsInterface $subject
     * @param callable $proceed
     * @param $value
     * @param null $locale
     * @return string
     */
    public function aroundGetCountryTranslation(
        ListsInterface $subject,
        callable $proceed,
        $value,
        $locale = null
    )
    {
        if ($value == 'XX') {
            return 'Abstract Country';
        }
​
        return $proceed($value, $locale);
    }
}
```

### ExtraCountries/Setup/Patch/Data/AddDataForAbstractCountry.php

Ce correctif de données sera exécuté pendant le processus d’installation/mise à niveau d’Adobe Commerce et ajoutera un nouvel enregistrement de pays à la base de données.

Pour plus d’informations sur les correctifs de données, reportez-vous à la section [Développement de correctifs de données et de schémas](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/data-patches.html) de notre documentation destinée aux développeurs.

Dans l’exemple ci-dessous, vous pouvez constater que le tableau `$data` de la méthode `apply()` contient les codes Country ID, ISO2 et ISO3 du nouveau pays, et que ces données sont insérées dans la base de données.

```php
<?php
namespace Magento\ExtraCountries\Setup\Patch\Data;
​
use Magento\Framework\Setup\ModuleDataSetupInterface;
use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
​
/**
 * Add Abstract Country data to the country list
 *
 * @package Magento\ExtraCountries\Setup\Patch
 */
class AddDataForAbstractCountry implements DataPatchInterface, PatchVersionInterface
{
    /**
     * @var ModuleDataSetupInterface
     */
    private $moduleDataSetup;
​
    /**
     * @param ModuleDataSetupInterface $moduleDataSetup
     */
    public function __construct(
        ModuleDataSetupInterface $moduleDataSetup
    ) {
        $this->moduleDataSetup = $moduleDataSetup;
    }
​
    /**
     * @inheritdoc
     */
    public function apply()
    {
        /**
         * Fill table directory/country
         */
        $data = [
            ['XX', 'XX', 'XX']
        ];
​
        $columns = ['country_id', 'iso2_code', 'iso3_code'];
        $this->moduleDataSetup->getConnection()->insertArray(
            $this->moduleDataSetup->getTable('directory_country'),
            $columns,
            $data
        );
    }
​
    /**
     * @inheritdoc
     */
    public static function getDependencies()
    {
        return [];
    }
​
    /**
     * @inheritdoc
     */
    public static function getVersion()
    {
        return '0.0.1';
    }
​
    /**
     * @inheritdoc
     */
    public function getAliases()
    {
        return [];
    }
}
```

### ExtraCountries/registration.php

Il s’agit d’un exemple du fichier registration.php. Pour en savoir plus sur l’enregistrement des modules, consultez le [Guide du développeur PHP > Enregistrer votre composant](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html) dans la documentation du développeur.

```php
<?php
use Magento\Framework\Component\ComponentRegistrar;
​
ComponentRegistrar::register(ComponentRegistrar::MODULE, 'VendorName_ExtraCountries', __DIR__);
```

### ExtraCountries/composer.json

Il s’agit d’un exemple de fichier compositeur.json.

Pour en savoir plus sur le fichier compositeur.json, consultez le [Guide du développeur PHP > Le fichier compositeur.json](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/composer-integration.html) dans notre documentation du développeur.

```json
{
    "name": "vendor_name/module-extra-countries",
    "description": "A module that adds extra countries to magento directory",
    "type": "magento2-module",
    "license": [
    ],
    "require": {
        "php": "~7.3.0||~7.4.0",
        "lib-libxml": "*",
        "magento/framework": "*",
        "magento/module-directory": "*"
    },
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "VendorName\\ExtraCountries\\": ""
        }
    },
    "config": {
        "sort-packages": true
    }
}
```

## Installation des modules

Pour savoir comment installer le module, voir [Emplacements de module](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_intro.html#module-locations) dans notre documentation destinée aux développeurs.

Une fois que le répertoire du module est placé à un emplacement correct, exécutez `bin/magento setup:upgrade` pour appliquer les correctifs de données et enregistrer le module externe de traduction.

Vous devrez peut-être nettoyer le cache du navigateur pour que les nouvelles modifications fonctionnent.
