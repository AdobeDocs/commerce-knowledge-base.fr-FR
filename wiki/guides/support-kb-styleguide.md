---
source-git-commit: c992521cae8c847adc0cc23d2323300e0ba69cdc
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 0%

---
# Guide de style de la Base de connaissances d’assistance

Lorsque vous contribuez au Centre d’aide Adobe Commerce, suivez ces recommandations de style et de mise en forme.

## Titres

* Les titres sont en majuscules comme des phrases.
* Plural pour les titres ; singulier pour les en-têtes de procédure. Exemple : Titre - Écriture de livres. En-tête - Écrire un livre.
* Conservez des titres courts, avec des mots importants au début. Pour des raisons d’optimisation du moteur de recherche (SEO), il est vivement recommandé que les titres ne dépassent pas 70 caractères (il existe une exception pour les cas où une réduction de titre empêche la communication de la véritable signification). 

## En-têtes

* L’en-tête de niveau supérieur est H2. (H1 est par défaut le titre de l’article, même si le titre n’est pas formaté de manière visible avec H1).
* Utilisez des verbes infinitifs pour les en-têtes de tâche. Par exemple, « Comment identifier les événements à trafic élevé ».
* Utilisez le formulaire au singulier pour les en-têtes de tâche. Par exemple, « Structure de module ».
* Évitez les en-têtes doubles (il doit y avoir au moins une phrase entre les en-têtes).
* Majuscules de style phrase pour tous les titres.
* Les titres des tâches sont impératifs (« Créer x », et non « Créer x » ou « Créer x »).

## Listes

* Étapes d’une tâche : maximum 9

* Les listes à puces facilitent l’analyse.

  * Utilisez des listes à puces pour les méthodes, les approches, les options et les étapes de tâche non consécutives.
  * Veillez à ce que le texte des puces soit court, de préférence pas plus de deux phrases.
  * Réduisez le nombre de balles ; sept balles ou moins, c’est l’idéal.
  * Évitez de placer un conseil ou une note entre des éléments à puces.
  * Utilisez la structure de grammaire parallèle dans les listes, mais enfreignez cette règle si elle entraîne un excès de verbiage ou de langage inadapté.
  * Mettez en majuscule le premier mot de chaque élément d’une liste à puces, même s’il s’agit d’un fragment.

* Placez vos listes en parallèle. Par exemple, chaque élément doit être un substantif ou une expression commençant par un verbe.

## Notes et conseils

Conservez les notes et les conseils dans un seul paragraphe. La nécessité de plusieurs paragraphes signale la nécessité de restructurer le contenu et de l’inclure dans le corps de l’article.

## Majuscules

En cas de doute, n’utilisez pas les majuscules. Dans les en-têtes, mettez une majuscule en début de phrase. Mettez les noms propres en majuscules et le premier mot après deux points.

## Éléments de l’interface utilisateur

* Tout ce sur quoi l’utilisateur clique est **en gras**. Par exemple, « Cliquez sur **Continuer** ». Les valeurs des options et les messages d’erreur sont formatés en _italique_.
* Dans la mesure du possible, évitez de mentionner le type d’élément d’IU dans les instructions. (Cliquez sur **Suivant**. ou cliquez sur le bouton **Suivant**.)
* Utilisez « Choose » et « > » dans les séquences de commandes. (Choisissez **Modifier** > **Préférences**. ou cliquez sur Modifier | Préférences.)
* Préposition : « dans » pour la boîte de dialogue, la fenêtre, la zone, le panneau, la vue, l’assistant, la liste, le dossier, le nœud.
* Préposition : « activé » pour l’écran, la page, la barre d’outils, la barre de menus, l’onglet, le volet et le ruban.
* Préposition : cliquez sur (cliquez sur **Suivant** ou sur **Suivant**).

## Noms de fichiers

Les noms de fichier et les dossiers sont formatés sous forme de code. Exemple : le répertoire système `/var/log` contient des journaux pour tous les environnements.


## Nombres

Surtout, des règles de cohérence lors de l&#39;approche de la question des nombres écrits par rapport aux chiffres.

Écrivez un nombre, comme « cinq » ou « neuf » lorsque le nombre est inférieur à 10 (nombres un à neuf).

Écrivez un nombre sous forme de chiffre, comme « 42 » ou « 11 » lorsque :

* Le nombre est supérieur à 9 (nombres dix et supérieurs).
* Vous spécifiez le nombre :
  * Dans une ligne de code ou un fragment de code.
  * Dans un chemin de fichier ou un nom de répertoire.
  * Lors de la communication d’une plage, comme « entre 5 et 25 » ou « passer en revue les numéros 8 à 21 ».
  * Les nombres ont été mesurés ou calculés comme « 62 picas » ou « 830 MHz ».

Utilisez un mélange de chiffres et de chiffres lorsque vous notez une quantité de choses numérotées, comme « une collection de quinze mille essais ».

Écrivez les deux nombres en mots ou les deux en chiffres, si vous avez deux nombres dans une phrase, un de moins de 10 (comme 4) et un de plus de 10 (comme 14). Par exemple, vous devez vous en tenir aux chiffres : « 14 minutes pour 4 litres de liquide ».


## Cas particuliers de formulation

<table class="relative-table" style="width: 100.0%;"><colgroup><col style="width: 12.003596%;"> <col style="width: 16.444849%;"> <col style="width: 71.55351%;"></colgroup>

<tbody>

<tr>

<th>Incorrect</th>

<th>Correct</th>

<th> Raisonnement
</th>

</tr>

<tr>

<td>Connectez-vous à la page Compte Magento.com . </td>

<td>Connectez-vous à votre compte Adobe Commerce</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>Extensions tierces (modules)</td>

<td>extensions tierces (modules)</td>

<td colspan="1">
</td>

</tr>

<tr>

<td>Fragments de code SQL</td>

<td>Les instructions sont en majuscules (SELECT ou select).</td>

<td colspan="1">Meilleure lisibilité</td>

</tr>

<tr>

<td colspan="1">

Références à d’autres ressources.

Exemple : consultez xyz dans la documentation destinée aux développeurs


</td>

<td colspan="1">Consultez xyz dans notre documentation destinée aux développeurs</td>

<td colspan="1">

Exigence d’accessibilité : tous les liens décrivent la destination du lien.


</td>

</tr>

<tr>

<td colspan="1">

Adobe Commerce v2.4.0

Adobe Commerce 2.4.0

Adobe Commerce version 2.4.0

</td>

<td colspan="1">Adobe Commerce 2.4.0 (pas de version ou version)</td>

<td colspan="1"></td>

</tr>

<tr>

<td colspan="1">

2.4.x

2.4.X

</td>

<td colspan="1">

2.4.0

2.4.x

</td>

<td colspan="1">

Aucune raison de mettre les majuscules.

</td>

</tr>

<tr>

<td colspan="1">

Message d’erreur : _« Un problème est survenu. »_

Message d’erreur : __Un problème est survenu.__

</td>

<td colspan="1"> Message d’erreur : <i>Un problème est survenu.</i> </td>

<td colspan="1">
</td>

</tr>

</tbody>

</table>

## Accessibilité

* Tous les éléments non textuels ou graphiques comportent des équivalents textuels ou du Texte de remplacement. Exemple : ![example_image](/url "alt_text_for_this_image").

* Tous les liens décrivent la destination du lien. Exemple [link](/uri "destination_of_the_link").


<!--
## Accessible tables

Use tables for information that is best presented along two axes (rows and columns). Do not use tables when a list or definition list serves the purpose. If using tables, follow these recommendations:

*   Headers for rows and columns; row headers easier for screen readers.

*   Simple linear construction.

*   Content within cells consistently structured.  -->


## Langage abusif

* Évitez les propos abusifs. 
* Évitez les propos racistes ou « qui pourraient sembler racistes ».
* Évitez le langage à forte connotation négative ou à forte coloration émotionnelle, comme « tuer », « terminer ».


## Liens 

La plupart des liens apparaissent dans les listes de liens de l’article. Évitez les liens intégrés inutiles.

Il est recommandé d’isoler les liens intégrés dans une liste de liens dotée d’un titre configurable.

Une liste de liens spécialisée, appelée liste voir aussi, s’affiche à la fin d’un article uniquement.    Utilisez les listes de liens de manière stratégique, au maximum. En règle générale, une liste de liens ne contient pas plus de six liens.

### Liens vers des sites web externes

Utilisez des URL ordinaires plutôt que des goURL pour créer des liens vers des pages en dehors d’[Adobe.com](http://Adobe.com).


## Virgules

En général, suivez les recommandations du Chicago Manual of Style pour la ponctuation de style ouverte, en ne ponctuant que lorsque cela est nécessaire pour éviter les erreurs de lecture. Par exemple, vous pouvez omettre la virgule avant une conjonction dans une phrase composée s’il y a peu ou pas de risque de mauvaise lecture. Utilisez la virgule si nécessaire pour apporter des éclaircissements.

* Utilisez toujours la virgule série (une virgule précédant _et_ ou _ou_ dans une liste de trois éléments ou plus) : x, y et z

* Placez une virgule avant une conjonction introduisant une clause indépendante : « Spécifiez un emplacement et saisissez un nom pour la liste de fichiers. »

* Ne séparez pas les différences de plateforme par une virgule : «... Ctrl (Windows) ou Commande (Mac OS) »

* Utilisez toujours une virgule après une phrase ou une clause d’introduction : « Dans Photoshop, importez le fichier Illustrator ».

## Versions

* Nous utilisons « version » pour toutes les versions (majeure/mineure/correctif). Par exemple, « Versions prises en charge : Adobe Commerce 2.3.x »

* Nous utilisons la minuscule « x » lorsque nous écrivons sur toutes les versions de correctif dans les versions mineures, et toutes les versions mineures avec majeure. Par exemple, Adobe Commerce 2.x.x.

## Image de marque

* Magento Commerce est désormais Adobe Commerce. Reportez-vous au wiki [termes de changement de marque](https://github.com/magento/knowledge-base/wiki) pour plus d’informations sur l’utilisation d’un langage de marque à jour.
