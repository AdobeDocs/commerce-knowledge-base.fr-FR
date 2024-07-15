---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# Guide de validation des métadonnées

Pour garantir une mise en forme correcte des métadonnées dans les fichiers MD, nous avons mis en place un test de validation des métadonnées. Ce document fournit des instructions pour aider les contributeurs à éviter certaines des erreurs de validation des métadonnées les plus courantes.

**Exemple de métadonnées :**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## Erreurs de validation courantes et comment les éviter/les corriger

Voici quelques-uns des scénarios les plus courants où des erreurs de validation de métadonnées se produisent.

### Deux-points dans les métadonnées

Une erreur de validation se produira si le titre ou les libellés contiennent tous deux deux deux deux-points.

**Exemple :**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

Pour éviter cette erreur, placez le titre ou les libellés (ou les deux s’ils contiennent tous deux deux deux deux deux deux deux deux-points) dans les **guillemets simples**.

**Exemple :**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### Guillemet ou apostrophe simple deux-points dans les métadonnées

La solution précédente ne fonctionnera pas si le titre ou les libellés contiennent des deux-points, des guillemets simples ou des apostrophes.

**Exemple :**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

Cette erreur est corrigée en encapsulant le titre ou les libellés (ou les deux) dans **guillemets doubles**.

**Exemple :**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### Deux-points, un guillemet double et un guillemet ou apostrophe simple dans les métadonnées

**Exemple :**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

Dans ce cas, placez le ou les libellés (ou les deux) dans les **guillemets doubles** et utilisez une **barre oblique inverse** pour échapper tous les guillemets doubles dans le titre et les libellés.

**Exemple :**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### Champs manquants dans les métadonnées

Une erreur de validation se produit si le champ de titre ou le champ de libellés est absent des métadonnées.

**Exemple :**

```markdown
---
title: This is a title
---
```

OU

```markdown
---
labels: article,labels,tags
---
```

Pour éviter cette erreur, incluez les deux champs dans les métadonnées.

Le champ Libellés peut être laissé vide et ne pas générer d’erreur, mais le champ Titre doit être renseigné.

**Exemple :**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
