---
title: Le rapport de l’outil d’analyse de sécurité est vide
description: Cet article fournit un correctif pour le problème où l’outil d’analyse de sécurité affiche une page vierge au lieu du rapport réel. Pour le résoudre, vous devrez peut-être ajouter les adresses IP utilisées par l’outil à la Liste autorisée de pare-feu.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Le rapport de l’outil d’analyse de sécurité est vide

Cet article fournit un correctif pour le problème où l’outil d’analyse de sécurité affiche une page vierge au lieu du rapport réel. Pour le résoudre, vous devrez peut-être ajouter les adresses IP utilisées par l’outil à la Liste autorisée de pare-feu.

## Produits et versions concernés :

* Adobe Commerce (toutes les méthodes de déploiement) et Magento Open Source, toutes les versions

## Problème

<u>Étapes à reproduire</u>:

1. Configurez l’outil d’analyse de sécurité pour vérifier votre site web, comme décrit dans la section [Analyse de sécurité](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) dans notre guide d’utilisation.
1. Dans la colonne Actions , sélectionnez **Exécution de l’analyse**.

<u>Résultats attendus</u>:

Affichez la notification d’achèvement du rapport et la possibilité d’ouvrir le rapport.

<u>Résultats réels</u>:

Aucune notification et aucun rapport disponible.

## Cause

Ce problème peut apparaître car l’outil d’analyse de sécurité n’a pas pu atteindre votre site web. Cela signifie que le site web est hors service et ne peut pas être accessible du tout ou que l&#39;outil d&#39;analyse de sécurité est en train d&#39;être bloqué.

## Solution

Essayez d’ouvrir votre site web.

* Si la page se charge correctement, vous devrez peut-être ajouter les adresses IP utilisées par les outils d’analyse de sécurité à la Liste autorisée de pare-feu. Les adresses IP suivantes sont utilisées : 52.87.98.44, 34.196.167.176, 3.218.25.102 aux ports 80 et 443.
* Si le site ne se charge pas et renvoie la variable *&quot;Une erreur s’est produite lors du traitement de votre requête&quot;* , vérifiez les erreurs possibles sur votre site web.

## Lecture connexe

* [Mise en ligne et lancement](https://devdocs.magento.com/guides/v2.3/cloud/live/live.html?_ga=2.73579601.273749082.1559572284-888339099.1547722854#security-scan) dans notre documentation destinée aux développeurs.
* [Analyse de sécurité](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html) dans notre guide d’utilisation.
