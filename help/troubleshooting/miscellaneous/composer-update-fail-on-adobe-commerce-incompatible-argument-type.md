---
title: "Échec de la mise à jour du compositeur sur Adobe Commerce : type d’argument incompatible"
description: Cet article fournit une solution pour lorsque le déploiement est bloqué en raison d’un problème de compilation de code. Ce problème est dû à une nouvelle version de la dépendance symfony/console (4.4.27, 4.4.28).
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Échec de la mise à jour du compositeur sur Adobe Commerce : type d’argument incompatible

>[!NOTE]
>
>Ce problème est maintenant résolu dans la dernière version de symfony 4.4.29.

Cet article fournit une solution pour lorsque le déploiement est bloqué en raison d’un problème de compilation de code. Ce problème est dû à une nouvelle version de la dépendance symfony/console (4.4.27, 4.4.28).

## Produits et versions concernés

* Adobe Commerce (toutes les méthodes de déploiement) et Magento Open Source :
   * 2.4.0, 2.4.0-p1, 2.4.1, 2.4.1-p1, 2.4.2, 2.4.2-p1, 2.4.2-p2, 2.4.3
   * 2.3.5, 2.3.5-p1, 2.3.5-p2, 2.3.6, 2.3.6-p1, 2.3.7, 2.3.7-p1
* dépendance symfony/console (4.4.27, 4.4.28).

## Problème

Une nouvelle version de la dépendance symfony/console (4.4.27, 4.4.28) entraîne l’échec du processus de compilation des dépendances.

<u>Étapes à reproduire</u> :

Lorsque vous installez ou mettez à niveau Adobe Commerce ou exécutez la mise à jour du compositeur, l’exécution échoue avec le message d’erreur suivant :
*Type d’argument incompatible : type requis : int. Type réel : string*

## Cause

Le problème est dû à l’incompatibilité du code principal Adobe Commerce avec la dernière dépendance &quot;symfony/console&quot; publiée dans les versions 4.4.27 et 4.4.28.

## Solution

Le problème sera résolu automatiquement lorsqu’une nouvelle version de symfony/console 4.2.29 sera publiée (prévu en août 2021).

**Comment résoudre le problème sur Adobe Commerce on-premise :**

Adobe Commerce On-Premise 2.4.x

Exécutez la commande suivante dans l’interface de ligne de commande/le terminal :

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

Tous les commerçants sur site Adobe Commerce 2.3.5+ doivent exécuter la commande d’interface de ligne de commande suivante :

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**Comment résoudre le problème sur Adobe Commerce sur l’infrastructure cloud :**

Exécutez les commandes ci-dessus ou effectuez une mise à niveau vers la dernière version des outils de la CEE (ece-tools: 2002.1.7), qui sera disponible le jeudi 29 juillet. Pour les étapes, reportez-vous à la section [Cloud pour Adobe Commerce > Mise à jour des outils de mise à jour version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) dans notre documentation destinée aux développeurs.

Le correctif complet sera publié dans Adobe Commerce (toutes les méthodes de déploiement) 2.4.4.

## Lecture connexe

* Github : [2021-07-27 Composer update Type d’argument incompatible : type requis : int. Type réel : string](https://github.com/magento/magento2/issues/33595)
