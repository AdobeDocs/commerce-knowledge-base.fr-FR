---
title: Impossible d’enregistrer le serveur principal Adobe Commerce de l’entité
description: Cet article fournit une solution pour lorsque vous ne parvenez pas à enregistrer une entité dans le serveur principal Adobe Commerce. Par exemple, lorsque vous ne pouvez pas modifier et enregistrer une règle "cart_price" spécifique.
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Impossible d’enregistrer le serveur principal Adobe Commerce de l’entité

Cet article fournit une solution pour lorsque vous ne parvenez pas à enregistrer une entité dans le serveur principal Adobe Commerce. Par exemple, lorsque vous ne pouvez pas modifier et enregistrer une règle `cart_price` spécifique.

## Produits et versions concernés

Ce problème peut affecter toutes les versions d’Adobe Commerce dont la taille de session maximale est configurée. Ceci a été ajouté à partir de Magento Open Source 2.3.7-p1 et Adobe Commerce (toutes les méthodes de déploiement) 2.4.3.


## Problème

Lorsque vous essayez de reconfigurer votre magasin, la page se recharge et vos modifications ne sont pas enregistrées. Un message est visible dans `var/log/system.log` :

*[2021-11-27 00:30:52] report.WARNING : la taille de la session de 418056 a dépassé la taille maximale autorisée de la session de 256000. [][]*

<u>Étapes à reproduire</u> :

Exemple de configuration de magasin non enregistrée :

1. Sélectionnez une règle dans la boutique Adobe Commerce dans Production > **Marketing** > **Règles de prix du panier**.
1. Sélectionnez une règle et définissez cette règle sur *Inactive* et enregistrez la modification.

<u>Résultat attendu</u> :

La règle est définie sur inactive.

<u>Résultat réel</u> :

* Chargements de page sans message.
* La règle est toujours définie sur active.

## Cause

Ce problème est lié à la nouvelle fonctionnalité introduite récemment qui a eu un impact sur la taille de session maximale. Voir [Gestion de session](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management) dans notre documentation destinée aux développeurs.

## Solution

Augmentez la valeur &quot;Taille de session maximale&quot; dans (**Magasins** > **Configuration** > **Avancé** > **Système** > **Sécurité** > Taille de session maximale).

## Lecture connexe

* [Menu marketing](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/marketing-menu) dans notre guide d’utilisation.
