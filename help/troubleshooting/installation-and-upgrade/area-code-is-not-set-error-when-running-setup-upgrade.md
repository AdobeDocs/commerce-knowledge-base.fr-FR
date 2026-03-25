---
title: Erreur « L’indicatif régional n’est pas défini » lors de l’exécution de setup:upgrade
description: Cet article fournit un correctif pour le problème Adobe Commerce on cloud infrastructure 2.2.3 connu lié à l’erreur *L’indicatif régional n’est pas défini* lors de l’exécution de la commande setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Erreur « L’indicatif régional n’est pas défini » lors de l’exécution de `setup:upgrade`

Cet article fournit un correctif pour le problème Adobe Commerce on cloud infrastructure 2.2.3 connu lié à l’erreur *« L’indicatif régional n’est pas défini »* lors de l’exécution de la commande suivante :

```bash
setup:upgrade
```

>[!NOTE]
>
>Le problème a été résolu dans Adobe Commerce 2.2.4.

## Problème

Lors de l’exécution du

```bash
bin/magento setup:upgrade
```

, vous obtenez le message d’erreur suivant : *« Module &#39;Magento\_AdvancedSalesRule&#39; : Installation des données...Indicatif régional non défini : L’indicatif régional doit être défini avant de démarrer une session »* et l’exécution de la commande est interrompue. Le problème apparaît, car la configuration de zone est demandée avant d’être définie. Le correctif permet de capturer l’erreur sans interrompre le processus de mise à niveau.

## Patch

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Télécharger MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Versions d’Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur les infrastructures cloud 2.2.3

Le correctif est également compatible (mais peut ne pas résoudre le problème) avec les versions et éditions d’Adobe Commerce suivantes :

* Adobe Commerce sur les infrastructures cloud et Adobe Commerce on-premise 2.2.0 - 2.2.3

## Application du correctif

Pour obtenir des instructions, consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) dans notre base de connaissances d’assistance.

## Fichiers attachés
