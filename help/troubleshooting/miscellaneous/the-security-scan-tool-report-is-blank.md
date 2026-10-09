---
title: Le rapport de l’outil d’analyse de sécurité est vide
description: Cet article fournit un correctif pour le problème où l’outil Analyse de sécurité affiche une page vierge au lieu du rapport réel. Pour le résoudre, vous devrez peut-être ajouter les adresses IP utilisées par l’outil au pare-feu.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%
---
# Le rapport de l’outil d’analyse de sécurité est vide

Cet article fournit un correctif pour le problème où l’outil Analyse de sécurité affiche une page vierge au lieu du rapport réel. Pour le résoudre, vous devrez peut-être ajouter les adresses IP utilisées par l’outil au pare-feu.

## Produits et versions concernés :

* Adobe Commerce (toutes les méthodes de déploiement) et Magento Open Source, toutes versions

## Problème

<u>Procédure à suivre </u> :

1. Configurez l’outil de scan de sécurité pour vérifier votre site web, comme décrit dans [Scan de sécurité](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-scan) dans notre guide d’utilisation.
1. Dans la colonne Actions, sélectionnez **Exécuter l&#39;analyse**.

<u>Résultats attendus</u> :

Affichez la notification de fin de l’état et la possibilité d’ouvrir l’état.

<u>Résultats réels</u> :

Aucune notification et aucun rapport disponible.

## Cause

Ce problème peut se produire car l&#39;outil Analyse de sécurité n&#39;a pas pu atteindre votre site Web. Cela signifie que le site web est en panne et n&#39;est pas accessible du tout ou que l&#39;outil d&#39;analyse de sécurité est bloqué.

## Solution

Essayez d’ouvrir votre site web.

* Si la page se charge correctement, vous devrez peut-être ajouter les adresses IP utilisées par les outils d’analyse de sécurité au pare-feu. Les adresses IP utilisées sont les suivantes : 52.87.98.44, 34.196.167.176 et 3.218.25.102 sur les ports 80 et 443.
* Si le site ne charge pas et renvoie le message *« Une erreur s’est produite lors du traitement de votre demande »* recherchez d’éventuelles erreurs sur votre site web.

## Lecture connexe

* [Activez et lancez](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/launch/overview) dans notre documentation destinée aux développeurs.
* [Security Scan](https://experienceleague.adobe.com/fr/docs/commerce-admin/systems/security/security-scan) dans notre guide de l’utilisateur.
