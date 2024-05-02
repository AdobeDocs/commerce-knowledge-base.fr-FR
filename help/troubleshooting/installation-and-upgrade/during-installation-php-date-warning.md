---
title: Lors de l’installation, avertissement de date PHP
description: Cet article fournit un correctif pour un avertissement de date PHP lors de l’installation.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Lors de l’installation, avertissement de date PHP

Cet article fournit un correctif pour un avertissement de date PHP lors de l’installation.

## Détails {#details}

Lors de l’installation, le message suivant s’affiche :

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### Solution {#solution}

Vérifiez attentivement le paramètre de fuseau horaire PHP. Voir [Guide d’installation > Paramètres PHP](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html) dans notre documentation destinée aux développeurs.
