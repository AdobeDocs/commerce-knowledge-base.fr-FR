---
title: Impossible de cloner le référentiel GitHub du Magento
description: Cet article fournit un correctif pour les cas où vous ne pouvez pas cloner le référentiel GitHub du Magento.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Impossible de cloner le référentiel GitHub du Magento

Cet article fournit un correctif pour les cas où vous ne pouvez pas cloner le référentiel GitHub du Magento.

## Détail {#detail}

L’erreur est similaire à ce qui suit :

```terminal
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Solution {#solution}

Téléchargez votre clé SSH sur GitHub, comme décrit dans la section [la page d’aide de GitHub ;](https://help.github.com/articles/generating-ssh-keys) .
