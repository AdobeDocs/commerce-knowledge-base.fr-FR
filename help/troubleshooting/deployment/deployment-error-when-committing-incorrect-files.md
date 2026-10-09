---
title: Erreurs de déploiement lors de la validation de fichiers incorrects
description: Cet article fournit une solution au problème d’erreurs de déploiement provoquées par des validations incorrectes dans le référentiel de fichiers/dossiers qui n’auraient pas dû être ajoutés.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%
---
# Erreurs de déploiement lors de la validation de fichiers incorrects

Cet article fournit un correctif pour le problème lorsque vous obtenez des erreurs de déploiement causées par des validations incorrectes dans le référentiel de fichiers/dossiers qui n’auraient pas dû être ajoutés.

## Produits et versions concernés

Adobe Commerce sur les infrastructures cloud (toutes versions)

## Problème

Des erreurs de déploiement se produisent lorsque vous validez le référentiel de fichiers/dossiers. Par exemple, l’erreur suivante est due à une tentative de connexion à la base de données alors qu’elle n’est pas disponible pendant la [phase de création](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase) :

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## Cause

Certains fichiers/dossiers ne doivent pas être validés dans le référentiel, car ils entraînent une interruption du [workflow de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html).

## Solution

Supprimez ces fichiers/dossiers du référentiel s’ils sont présents :

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
