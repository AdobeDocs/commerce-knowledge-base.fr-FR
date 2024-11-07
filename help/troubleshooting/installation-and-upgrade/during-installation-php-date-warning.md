---
title: Lors de l’installation, avertissement de date PHP
description: Cet article fournit un correctif pour un avertissement de date PHP lors de l’installation.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Vérifiez attentivement le paramètre de fuseau horaire PHP. Reportez-vous au [Guide d’installation > Paramètres PHP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) dans notre documentation destinée aux développeurs.
