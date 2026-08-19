---
source-git-commit: 88a2b8fe11d718f33c26bbc6f407c55d9f1fd189
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---
# Guide des libellés de la base de connaissances

Ce document fournit des instructions pour l’ajout de libellés aux articles de la base de connaissances de l’assistance Adobe Commerce.
Les libellés (également appelés balises) améliorent l’expérience de recherche dans la base de connaissances de l’[assistance d’](https://support.magento.com/hc/en-us).
Les libellés sont ajoutés dans le champ « libellés » de la section des métadonnées d’un fichier d’article, séparés par des virgules, sans espace entre une virgule et le libellé suivant.
Voir [../../.github/CONTRIBUTING.md#metadata] pour plus d’informations.

## Dispositions générales

Pour chaque article, ajoutez les types de libellés suivants :

* Étiquette(s) pour produit(s). (obligatoire)
* Libellé(s) pour les versions concernées. (obligatoire, sauf pour les articles liés au support général)
* Libellé du type de contenu. (obligatoire)
* Étiquettes des principaux composants technologiques (le cas échéant).
* Libellés du processus/de la fonctionnalité en cours de dépannage/description. (le cas échéant)
* Libellés du problème en cours de résolution/description. (le cas échéant)

Consultez les sections ci-dessous pour obtenir des recommandations détaillées sur la définition de libellés pour chacun de ces types de libellés.

## Étiquettes pour les produits

<table>
<tbody>
  <tr>
    <th>Nom du produit</th>
    <th>Libellé</th>
  </tr>
  <tr>
    <td>Adobe Commerce (toutes les méthodes de déploiement) </td>
    <td>
    « Adobe Commerce,infrastructure cloud,local »
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce sur les infrastructures cloud</td>
    <td>
      « Adobe Commerce,infrastructure cloud »
    </td>
  </tr>
  <tr>
    <td>Adobe Commerce On-Premise</td>
    <td>« Adobe Commerce, On-premise »</td>
  </tr>
  <tr>
    <td>Magento Business Intelligence (MBI)</td>
    <td>
        « Magento Business Intelligence, MBI »
    </td>
  </tr>
   <tr>
    <td>Magento Open Source</td>
    <td>
        « Magento Open Source »
    </td>
  </tr>
  <tr>
    <td>B2B pour Adobe Commerce</td>
    <td>« B2B »</td>
  </tr>
  <tr>
    <td>PWA pour Adobe Commerce</td>
    <td>« PWA »</td>
  </tr>
  <tr>
    <td>Projet Venia storefront</td>
    <td>Venia</td>
  </tr>
  <tr>
    <td>Outil de correctifs de qualité, QPT</td>
    <td>« Outil de correctifs de qualité, correctifs QPT »</td>
  </tr>
  </tbody>
</table>

## Étiquettes des versions des produits

* Ajoutez un libellé distinct pour chaque version d’Adobe Commerce. Exemple : « 2.3.7 »
* N’ajoutez pas de libellés pour les intervalles.
En d’autres termes, si les versions 2.3.0 à 2.3.5 sont concernées, ajouter : « 2.3.0,2.3.1,2.3.2,2.3.2-p2,2.3.3,2.3.3-p1,2.3.4,2.3.4-p2,2.3.5-p1,2.3.5-p2 »
PAS « 2.3.0-2.3.5 »
* N’ajoutez pas de libellés avec .x. Exemple : « 2.3.x »

## Libellés pour le type de contenu (selon la catégorie)

<table>
  <tbody>
    <tr>
      <th>Catégorie</th>
      <th>Libellé</th>
    </tr>
    <tr>
      <td>Bonnes pratiques</td>
      <td>« bonnes pratiques » (et non pas « bonnes pratiques » ni « bonnes pratiques »)</td>
    </tr>
    <tr>
      <td>
        Dépannage
      </td>
      <td>
      « résolution des problèmes »
      </td>
    </tr>
    <tr>
      <td>Comment</td>
      <td>« comment »</td>
    </tr>
    <tr>
      <td>FAQ</td>
      <td >« FAQ »</td>
    </tr>
  </tbody>
</table>

## Libellés des principaux composants techniques

* Utilisez des majuscules selon l’appellation officielle du composant.
* N’utilisez pas de synonymes, un libellé pour un composant.
* Un libellé de mot est préférable, mais si le nom du composant contient plusieurs mots, utilisez plusieurs mots. N’ajoutez pas de descriptions d’événement. En d’autres termes, placez « Elasticsearch » au lieu de « Problèmes Elasticsearch ».
* Si le contenu est pertinent uniquement pour une version particulière du composant, ajoutez un libellé contenant nom + version.\
  Exemple : « Elasticsearch 5 ». S’il est pertinent pour plusieurs versions particulières, ajoutez plusieurs libellés de ce type. Exemple : « Elasticsearch 5 », « Elasticsearch 6 ». Le cas échéant, utilisez « x » pour plusieurs versions. Exemple : « Elasticsearch 2.x »

Exemples :

* « Elasticsearch »
* « New Relic »
* « Assistant Configuration Web »

## Libellés du processus/de la fonctionnalité en cours de dépannage/description

* Utilisez des minuscules, à l’exception des noms propres.
* N’utilisez pas de synonymes, un libellé pour une entité.
* Les libellés Un mot sont préférables. N’ajoutez pas de description de problème. En d’autres termes, placez « base de données » au lieu de « base de données bloquée ».

Exemples : 

* « base de données »
* « cron »
* « déploiement »
* « mise à jour en masse »

## Libellés du problème en cours de résolution/description

* Utilisez des minuscules, à l’exception des noms propres.
* N’utilisez pas de synonymes, un libellé pour une entité.
* Les libellés Un mot sont préférables. Ne convertissez pas un message d’erreur en libellé.

Exemples :

* « site en panne »
* « Erreur 500 »
* « cron bloqué »
