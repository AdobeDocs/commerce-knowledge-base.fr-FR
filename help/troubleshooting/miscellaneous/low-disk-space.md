---
title: Espace disque faible
description: Cet article suggère des solutions à la situation lorsque vous êtes à court d’espace sur un certain environnement d’Adobe Commerce sur l’infrastructure cloud.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 9ee4145d5516a37fab1c092d539000627f242a93
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Espace disque faible

Cet article suggère des solutions à la situation lorsque vous êtes à court d’espace sur un certain environnement d’Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud, toutes les [ versions prises en charge](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problème

Vous n’avez plus d’espace disque sur le disque avec des répertoires modifiables. Un symptôme peut être [déploiement bloqué](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

Pour vérifier l’utilisation du disque, exécutez la commande suivante :

```bash
df -h var/
```

## Cause

Le répertoire `var` est généralement celui qui peut prendre beaucoup d&#39;espace et peut être nettoyé facilement.

Adobe Commerce stocke tous les fichiers journaux dans le répertoire `var`. De nouveaux fichiers journaux sont créés et les anciens sont archivés quotidiennement. Mais si le nombre d’erreurs générées continue à augmenter, les fichiers journaux prennent de plus en plus d’espace.

Les fichiers d&#39;import/export personnalisés sont également stockés dans le répertoire `var` et prennent de l&#39;espace si leur nombre augmente.

## Solution

Options de solution :

* Vérifiez si vous disposez de fichiers journaux volumineux et découvrez pourquoi ils sont volumineux. Corrigez le problème générant une grande quantité de sortie de journal.
* Nettoyez le répertoire `var`.
* Configurez une tâche cron pour effectuer le suivi de la taille du répertoire `var` et la nettoyer.
* Allouez plus d’espace disque, si vous n’en avez pas. (Voir la section ci-dessous pour plus d’informations sur la façon de vérifier quelle est votre limite d’espace.)
   * Pour le plan de démarrage, tous les environnements et les environnements d’intégration Pro, vous pouvez allouer l’espace disque si vous n’en avez pas utilisé, comme décrit dans la section [Gestion de l’espace disque : allocation de l’espace disque](https://devdocs.magento.com/guides/v2.3/cloud/project/manage-disk-space.html#application-disk-space).
   * Pour les environnements d’évaluation et de production ProPlan, contactez le support pour allouer plus d’espace disque si vous n’en avez pas.
* Si vous avez atteint votre limite d’espace et que vous rencontrez toujours des problèmes d’espace, envisagez d’acheter plus d’espace disque, contactez votre équipe de compte d’Adobe pour plus de détails.

### Vérifier la limite d&#39;espace disque

Pour vérifier l’espace dont vous disposez pour chaque environnement d’infrastructure cloud d’Adobe Commerce :

1. Connectez-vous à la [console cloud](https://console.adobecommerce.com).
1. Sur le tableau de bord **[!UICONTROL All projects]**, sélectionnez le projet approprié. Dans le coin gauche, vous pouvez voir la disponibilité de l’espace disque.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
