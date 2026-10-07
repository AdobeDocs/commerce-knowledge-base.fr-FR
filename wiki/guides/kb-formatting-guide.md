---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%
---
# Guide de formatage des Ko

## Auteur en Markdown

En règle générale, nous utilisons le [guide de style de la syntaxe Markdown d’Adobe Experience League](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=en), mais il existe certaines différences et exceptions. En outre, certaines balises HTML sont requises dans certains cas.

Vous trouverez ci-dessous des exemples de mise en forme Markdown qui sont les plus couramment utilisées dans votre référentiel.

## Formatage de base

Pour mettre le texte en gras, placez-le entre deux astérisques :

`This will be **bold** text`

Pour mettre le texte en italique, utilisez un seul astérisque :

`This text will be *italics*`

Pour mettre en forme le texte comme souligné, utilisez la balise `<ins>` :

`<ins>This text will be underlined</ins>`

Pour ajouter un saut de ligne, utilisez la balise `<br>` HTML .


## En-têtes

Utilisez la mise en forme suivante pour les en-têtes de H2 à H5. H1 n’est jamais utilisé, car le titre de l’article est considéré comme H1.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Code en ligne et blocs

Utilisez des accents graves simples pour entourer l’élément de code que vous souhaitez mettre en évidence :

Il s’agit de l’élément \« code intégré » dans un paragraphe de texte.

### Blocs de code

Pour insérer un bloc de code, placez-le entre trois accents graves et spécifiez la langue après l’ouverture des accents graves :

\`\`\` sql

SÉLECTIONNEZ TABLE_NAME COMME `Table`,
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
OÙ TABLE_SCHEMA = « %project_id% »
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC ;

\`\`\`

Le rendu sera :

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Selon nos règles de lint, vous devez toujours spécifier une langue pour le bloc de code.

Pour obtenir la liste des langues prises en charge, consultez https://github.com/github/linguist/blob/master/lib/linguist/languages.yml.

Si la mise en surbrillance ne fonctionne pas pour une certaine langue dans Markdown (c’est-à-dire que la langue n’est pas prise en charge), utilisez l’HTML suivante pour qu’elle soit au moins mise en surbrillance lors de sa publication sur https://support.magento.com/hc/en-us/ :

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

Où ``%language-code%`` les codes définis par les langages [pris en charge par Prism.js](https://prismjs.com/#supported-languages).

## Listes

Toujours séparer les listes du reste du contenu par des lignes vides. Les listes doivent être précédées et suivies d’une ligne vide.

Utilisez la mise en forme suivante pour les listes ordonnées :

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Pour créer une liste à puces non triée, commencez une ligne par *, ou +, ou -. Mais sélectionnez une méthode et utilisez-la de manière cohérente tout au long de l’article.

Exemple :

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Pour ajouter du contenu entre les éléments de liste, ajoutez 4 espaces au début de la ligne :

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

Vous pouvez également incorporer des listes de cette manière.

## Liens

Les liens externes sont simples :

```markdown
[Adobe](https://www.adobe.com)
```

### Liens vers les pièces jointes

Tout type de pièce jointe doit être au format .png, .jpg et .jpeg. Pour des raisons de sécurité, nous acceptons uniquement les pièces jointes qui sont dans l&#39;un des trois formats.

Pour insérer une image, placez-la dans le sous-dossier *assets* dans le même dossier de sections que l’article, puis utilisez la syntaxe suivante pour insérer l’image dans votre article :

```markdown
![alt text](assets/image.png)
```

Si vous souhaitez personnaliser la taille de votre image, vous devez le faire à l’aide de la balise HTML suivante :

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Liens vers des sections spécifiques de l’article

Si vous devez référencer une section à l’intérieur de votre article, vous n’avez pas besoin de créer une ancre distincte. Elles sont automatiquement générées au moment de la publication pour tous les titres H2-H6. Les ancres sont générées à partir de l’en-tête en mettant tous les mots en minuscules et en utilisant « - » pour séparer les mots.

Exemple :

```markdown
## This is header
```

Voici un lien vers cet en-tête :

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Si vous devez référencer un élément autre que l’en-tête, utilisez HTML pour définir l’élément à ajouter et utilisez l’attribut [id](https://www.w3schools.com/html/html_id.asp). Vous pouvez ensuite utiliser Markdown ou HTML pour référencer cet identifiant.

### Liens relatifs et liens vers d’autres articles

N’utilisez pas de liens relatifs pour référencer nos articles de la base de connaissances d’assistance. Ces liens ne fonctionneront pas lorsque votre article sera publié dans le Centre d’aide d’[&#128279;](https://support.magento.com/hc/en-us).
Veuillez utiliser des liens hypertexte complets à partir du Centre d&#39;aide [&#128279;](https://support.magento.com/hc/en-us).


## Tableaux

Utilisez la mise en forme [HTML pour les tableaux](https://www.w3schools.com/html/html_tables.asp).


## Avertissements et blocs d&#39;informations

Bloc de notes de succès :

```
>![success]
>
>This is a success note
```

Bloc d&#39;avertissement :

```
>![warning]
>
>This is a warning
```

Bloc de notes d’informations :

```
>![info]
>
>This is a block with additional info
```
