---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---
# Guide sur les étiquettes de base de connaissances

Ce document fournit des instructions pour l’ajout d’étiquettes aux articles dans la base de connaissances de prise en charge d’Adobe Commerce.
Les étiquettes (également appelées balises) améliorent l’expérience de recherche dans [Base de connaissances du support Adobe Commerce](https://support.magento.com/hc/en-us).
Les libellés sont ajoutés dans le champ &quot;libellés&quot; de la section des métadonnées d’un fichier d’article, séparés par des virgules, sans espace entre une virgule et le libellé suivant.
Voir [../../.github/CONTRIBUTING.md#metadata] pour plus d’informations.

## Dispositions générales

Pour chaque article, ajoutez les types de libellés suivants :

* Libellé(s) du ou des produits. (obligatoire)
* Libellé(s) des versions concernées. (obligatoire, à l’exception des articles relatifs au support général)
* Libellé du type de contenu. (obligatoire)
* Étiquettes pour le composant technologique principal.(le cas échéant)
* Étiquettes de processus/fonctionnalités en cours de dépannage/description. (le cas échéant)
* Étiquettes du problème corrigé/décrit. (le cas échéant)

Consultez les sections ci-dessous pour obtenir des recommandations détaillées sur la manière de définir des libellés pour chacun de ces types d’étiquettes.

## Étiquettes de produits

<table>
<tbody>
  <tr>
    <th>Nom du produit</th>
    <th>Libellé</th>
  </tr>
  <tr>
    <td>Adobe Commerce (toutes les méthodes de déploiement) </td>
    <td>
    "Adobe Commerce, infrastructure cloud, sur site"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce sur l’infrastructure cloud</td>
    <td>
      "Adobe Commerce, infrastructure cloud"
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce sur site</td>
    <td>"Adobe Commerce,on-premise"</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        "Magento Business Intelligence,MBI"
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        "Magento Open Source"
    </td>
  </tr>
  <tr>
    <td>B2B pour Adobe Commerce</td>
    <td>"B2B"</td>
  </tr>
  <tr>
    <td>PWA pour Adobe Commerce</td>
    <td>"PWA"</td>
  </tr>
  <tr>
    <td>Projet de vitrine Venia</td>
    <td>"Venia"</td>
  </tr>
  <tr>
    <td>Outil Correctifs de qualité, QPT</td>
    <td>"Outil Correctifs de qualité, correctifs QPT"</td>
  </tr>
  </tbody>
</table>

## Étiquettes des versions de produits

* Ajoutez un libellé distinct pour chaque version d’Adobe Commerce. Exemple : &quot;2.3.7&quot;
* N’ajoutez pas de libellés pour les intervalles.
Autrement dit, si 2.3.0-2.3.5 est concerné, ajoutez : &quot;2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2&quot; NOT &quot;2.2.2&quot; 3.0-2.3.5&quot;
* N’ajoutez pas d’étiquettes avec .x. Exemple : &quot;2.3.x&quot;

## Étiquettes pour le type de contenu (selon la catégorie)

<table>
  <tbody>
    <tr>
      <th>Catégorie</th>
      <th>Libellé</th>
    </tr>
    <tr>
      <td>Bonnes pratiques</td>
      <td>"bonnes pratiques" (pas "bonnes pratiques" ni "bonnes pratiques")</td>
    </tr>
    <tr>
      <td>
        Dépannage
      </td>
      <td>
      "dépannage"
      </td>
    </tr>
    <tr>
      <td>Comment</td>
      <td>"How to"</td>
    </tr>
    <tr>
      <td>FAQ</td>
      <td >"FAQ"</td>
    </tr>
  </tbody>
</table>

## Étiquettes des principaux composants techniques

* Utilisez la mise en majuscules en fonction du nom officiel du composant.
* N’utilisez pas de synonymes, un libellé pour un composant.
* Les libellés d’un mot sont préférables, mais si le nom du composant contient plusieurs mots, utilisez plusieurs mots. N’ajoutez pas de descriptions de problème. C&#39;est-à-dire mettre &quot;Elasticsearch&quot; au lieu de &quot;problèmes Elasticsearch&quot;.
* Si le contenu est pertinent pour une version spécifique du composant uniquement, ajoutez un libellé contenant le nom + version.\
  Exemple : &quot;Elasticsearch 5&quot;. S’il est pertinent pour plusieurs versions spécifiques, ajoutez plusieurs libellés de ce type. Exemple : &quot;Elasticsearch 5&quot;, &quot;Elasticsearch 6&quot;. Lorsque cela est pertinent, utilisez &quot;x&quot; pour plusieurs versions. Exemple : &quot;Elasticsearch 2.x&quot;

Exemples :

* &quot;Elasticsearch&quot;
* New Relic
* &quot;Assistant de configuration web&quot;

## Étiquettes de processus/fonctionnalités en cours de dépannage/description

* Utilisez la casse basse, à l’exception des noms appropriés.
* N’utilisez pas de synonymes, un libellé pour une entité.
* Les libellés d’un mot sont préférables. N’ajoutez pas de description du problème. Autrement dit, placez &quot;base de données&quot; au lieu de &quot;blocages de base de données&quot;.

Exemples : 

* &quot;database&quot;
* &quot;cron&quot;
* &quot;deployment&quot;
* &quot;mise à jour en masse&quot;

## Étiquettes pour le problème corrigé/décrit

* Utilisez la casse basse, à l’exception des noms appropriés.
* N’utilisez pas de synonymes, un libellé pour une entité.
* Les libellés d’un mot sont préférables. Ne convertissez pas un message d’erreur en libellé.

Exemples :

* &quot;site down&quot;
* &quot;Erreur 500&quot;
* &quot;coincé cron&quot;
