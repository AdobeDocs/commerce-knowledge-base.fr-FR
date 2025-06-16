---
title: Espace disque faible
description: Cet article propose des solutions pour la situation lorsque vous manquez d’espace sur un certain environnement d’Adobe Commerce sur une infrastructure cloud.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Espace disque faible

Cet article propose des solutions pour la situation lorsque vous manquez d’espace sur un certain environnement d’Adobe Commerce sur une infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud, toutes les [versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

L’espace disque sur le disque contenant des répertoires accessibles en écriture est insuffisant. Un symptôme peut être [déploiement bloqué](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26878).

Pour vérifier l’utilisation du disque, exécutez la commande suivante :

```bash
df -h var/
```

## Cause

Le répertoire `var` est généralement celui qui peut prendre beaucoup d&#39;espace et peut être nettoyé facilement.

Adobe Commerce stocke tous les fichiers journaux dans le répertoire `var`. De nouveaux fichiers journaux sont créés et les anciens sont archivés quotidiennement. Cependant, si le nombre d’erreurs générées ne cesse d’augmenter, les fichiers journaux occupent de plus en plus d’espace.

Les fichiers d’import/export personnalisés sont également stockés dans le répertoire `var` et occupent de l’espace si leur nombre augmente.

## Solution

Options de solution :

* Vérifiez si vous disposez de fichiers journaux volumineux et déterminez pourquoi ils sont volumineux. Corrigez le problème en générant une grande quantité de sortie de journal.
* Nettoyez le répertoire `var`.
* Configurez une tâche cron pour suivre la taille du répertoire `var` et le nettoyer.
* Allouez plus d’espace disque, si vous en avez inutilisé. (Pour plus d’informations sur la façon de vérifier votre limite d’espace, reportez-vous à la section ci-dessous.)
   * Pour le plan de démarrage, tous les environnements et les environnements d’intégration de plan Pro, vous pouvez allouer l’espace disque si vous en avez inutilisé, comme décrit dans la section [Gérer l’espace disque : allouer l’espace disque](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space).
   * Pour les environnements d’évaluation et de production ProPlan, contactez l’assistance pour allouer plus d’espace disque si vous en avez inutilisé.
* Si vous avez atteint votre limite d’espace et rencontrez toujours des problèmes d’espace disque faible, pensez à acheter plus d’espace disque. Pour plus d’informations, contactez l’équipe chargée de votre compte Adobe.

### Vérifier la limite d’espace disque

Pour vérifier l’espace disponible pour chaque Adobe Commerce dans l’environnement d’infrastructure cloud :

1. Connectez-vous à [Cloud Console](https://console.adobecommerce.com).
1. Dans le tableau de bord **[!UICONTROL All projects]**, sélectionnez le projet approprié. Dans le coin gauche, vous pouvez voir la disponibilité de l’espace disque.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
