---
title: Erreur "Code zone non défini" lors de l’exécution de setup:upgrade"
description: Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.3 lié à l’erreur *Le code régional n’est pas défini* lors de l’exécution de la commande setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Erreur &quot;Code zone non défini&quot; lors de l’exécution `setup:upgrade`

Cet article fournit un correctif pour le problème connu d’Adobe Commerce sur l’infrastructure cloud 2.2.3 lié à l’obtention de la variable *&quot;Code zone non défini&quot;* lors de l’exécution de la commande suivante :

```bash
setup:upgrade
```

>[!NOTE]
>
>Le problème a été corrigé dans Adobe Commerce 2.2.4.

## Problème

Lors de l’exécution de la variable

```bash
bin/magento setup:upgrade
```

, vous obtenez le message d’erreur suivant : *&quot;Module &#39;Magento\_AdvancedSalesRule&#39; : installation des données...Code de zone non défini : le code de zone doit être défini avant de démarrer une session&quot;* et l&#39;exécution de la commande est interrompue. Le problème s’affiche, car la configuration de zone est demandée avant d’être définie. Le correctif permet de capturer l’erreur et de ne pas interrompre le processus de mise à niveau.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch.](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.2.3

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions Adobe Commerce suivantes :

* Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.2.0 - 2.2.3

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

## Fichiers attachés
