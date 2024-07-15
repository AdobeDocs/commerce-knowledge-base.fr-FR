---
title: Erreurs de déploiement lors de la validation de fichiers incorrects
description: Cet article fournit une solution au problème lorsque vous obtenez des erreurs de déploiement dues à des validations incorrectes dans le référentiel des fichiers/dossiers qui n’auraient pas dû être ajoutés.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Erreurs de déploiement lors de la validation de fichiers incorrects

Cet article fournit un correctif pour le problème lorsque vous obtenez des erreurs de déploiement dues à des validations incorrectes dans le référentiel des fichiers/dossiers qui n’auraient pas dû être ajoutés.

## Produits et versions concernés

Adobe Commerce sur l’infrastructure cloud (toutes versions)

## Problème

Vous obtenez des erreurs de déploiement lorsque vous validez dans le référentiel de fichiers/dossiers. Par exemple, l’erreur suivante est provoquée par une tentative de connexion à la base de données alors qu’elle n’est actuellement pas disponible pendant la [phase de création](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase) :

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

Certains fichiers/dossiers ne doivent pas être validés dans le référentiel, car ils provoquent une interruption dans le [workflow de déploiement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html).

## Solution

Supprimez ces fichiers/dossiers de votre référentiel s’ils sont présents :

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
