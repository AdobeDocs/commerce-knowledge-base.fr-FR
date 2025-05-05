---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# Guide de mise en forme de base de connaissances

## Création dans Markdown

En règle générale, nous utilisons le [Guide de style de syntaxe Adobe Experience League Markdown](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=fr), mais il existe des différences et des exceptions. Certaines balises d’HTML sont également requises dans certains cas.

Vous trouverez ci-dessous des exemples de mise en forme Markdown qui est le plus souvent utilisée dans notre référentiel.

## Mise en forme de base

Pour mettre le texte en gras, entourez-le de deux astérisques :

`This will be **bold** text`

Pour mettre le texte en italique, utilisez un seul astérisque :

`This text will be *italics*`

Pour mettre en forme le texte comme souligné, utilisez la balise `<ins>` :

`<ins>This text will be underlined</ins>`

Pour ajouter un saut de ligne, utilisez la balise d&#39;HTML `<br>`.


## En-têtes

Utilisez la mise en forme suivante pour les en-têtes H2 à H5. H1 n’est jamais utilisé, car le titre de l’article est considéré comme H1.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Code en ligne et blocs

Utilisez des apostrophes uniques pour encadrer l’élément de code que vous souhaitez mettre en surbrillance :

Il s’agit du \`code intégré\` dans un paragraphe de texte.

### Blocs de code

Pour insérer un bloc de code, placez le bloc de code dans une triple apostrophe et indiquez la langue après avoir ouvert trois apostrophes :

\`\`\` sql

SELECT TABLE_NAME AS `Table`,
ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = &quot;%project_id%&quot;
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;

\`\`

Le rendu sera alors effectué comme suit :

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Selon nos règles de liaison, vous devez toujours spécifier une langue pour le bloc de code.

Pour obtenir la liste des langues prises en charge, consultez https://github.com/github/linguist/blob/master/lib/linguist/languages.yml.

Si la mise en surbrillance ne fonctionne pas pour une certaine langue dans Markdown (c’est-à-dire si la langue n’est pas prise en charge), pour la mettre au moins en surbrillance lors de sa publication sur https://support.magento.com/hc/en-us/, utilisez l’HTML suivant :

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

Où ``%language-code%`` sont les codes définis par les [langues prises en charge par Prism.js](https://prismjs.com/#supported-languages).

## Listes

Séparez toujours les listes du reste du contenu par des lignes vides. Les listes doivent être précédées et suivies d’une ligne vide.

Utilisez la mise en forme suivante pour les listes triées :

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Pour créer une liste à puces non ordonnées, commencez une ligne par *, + ou -. Mais sélectionnez une méthode et utilisez-la de manière cohérente tout au long de l’article.

Exemple :

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Pour ajouter du contenu entre des éléments de liste, ajoutez 4 espaces au début de la ligne :

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

Tout type de pièce jointe doit être au format .png, .jpg et .jpeg. Pour des raisons de sécurité, nous acceptons uniquement les pièces jointes qui se présentent dans l’un des trois formats.

Pour insérer une image, placez l’image dans le sous-dossier *assets* du même dossier de section que l’article, puis utilisez la syntaxe suivante pour insérer l’image dans votre article :

```markdown
![alt text](assets/image.png)
```

Si vous souhaitez personnaliser la taille de votre image, vous devez le faire à l’aide de la balise d’HTML suivante :

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Liens vers des sections spécifiques de l’article

Si vous devez référencer une section dans votre article, il n’est pas nécessaire de créer une ancre distincte. Elles sont automatiquement générées au moment de la publication pour tous les en-têtes H2-H6. Les ancres sont générées à partir de l’en-tête en mettant tous les mots en minuscules et en utilisant &quot;-&quot; pour séparer les mots.

Exemple :

```markdown
## This is header
```

Voici un lien vers cet en-tête :

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Si vous devez référencer un élément autre que l’en-tête, utilisez HTML pour définir l’élément à ajouter et utilisez l’ [attribut id](https://www.w3schools.com/html/html_id.asp). Vous pouvez ensuite utiliser Markdown ou HTML pour référencer cet identifiant.

### Liens et liens relatifs vers d’autres articles

N’utilisez pas de liens relatifs pour faire référence aux articles de notre base de connaissances d’assistance. Ces liens ne fonctionneront pas lorsque votre article sera publié dans le [centre d’aide Adobe Commerce](https://support.magento.com/hc/en-us).
Veuillez utiliser des liens hypertexte complets à partir du [Centre d’aide Adobe Commerce](https://support.magento.com/hc/en-us).


## Tableaux

Utilisez [HTML formatage pour les tableaux](https://www.w3schools.com/html/html_tables.asp).


## Avertissements et blocs d’informations

Bloc de notes de succès :

```
>![success]
>
>This is a success note
```

Blocage d&#39;avertissement :

```
>![warning]
>
>This is a warning
```

Bloc de notes d’information :

```
>![info]
>
>This is a block with additional info
```
