---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%
---

# Guide de validation des métadonnées

Afin d&#39;assurer le bon formatage des métadonnées dans les fichiers MD, nous avons mis en place un test de validation des métadonnées. Ce document fournit des instructions pour aider les contributeurs et contributrices à éviter certaines des erreurs de validation de métadonnées les plus courantes.

**Exemple de métadonnées :**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## Erreurs de validation courantes et comment les éviter/corriger

Vous trouverez ci-dessous quelques-uns des scénarios les plus courants où des erreurs de validation des métadonnées se produisent.

### Deux-points dans les métadonnées

Une erreur de validation se produit si le titre ou les libellés, ou les deux, comportent deux points.

**Exemple:**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

Pour éviter cette erreur, placez le titre ou les libellés (ou les deux s’ils comportent deux points) entre **guillemets simples**.

**Exemple:**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### Deux-points et guillemets simples ou apostrophe dans les métadonnées

La solution précédente ne fonctionne pas si le titre ou les libellés contiennent des deux-points, des guillemets simples ou des apostrophes.

**Exemple:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

Cette erreur est corrigée en plaçant le titre ou les libellés (ou les deux) entre **guillemets doubles**.

**Exemple:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### Deux-points, guillemets doubles et guillemets simples ou apostrophe dans les métadonnées

**Exemple:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

Dans ce cas, placez le titre ou les libellés (ou les deux) entre **guillemets doubles** et utilisez une **barre oblique inverse** pour échapper tous les guillemets doubles du titre et des libellés.

**Exemple:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### Champs manquants dans les métadonnées

Une erreur de validation se produit si le champ de titre ou le champ de libellés est absent des métadonnées.

**Exemple:**

```markdown
---
title: This is a title
---
```

SOIT

```markdown
---
labels: article,labels,tags
---
```

Pour éviter cette erreur, incluez les deux champs dans les métadonnées.

Le champ des libellés peut rester vide et ne provoquera pas d’erreur, mais le champ du titre doit être renseigné.

**Exemple:**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
