---
title: Variable d’incrément auto_incrémentation de la base de données définie sur "3" Adobe Commerce sur notre architecture cloud pro
description: Il s’agit du comportement attendu pour les solutions d’architecture de plan Adobe Commerce sur l’infrastructure cloud Pro en raison de l’architecture à 3 noeuds et il ne peut pas être modifié.
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Variable d’incrément auto_incrémentation de la base de données définie sur &quot;3&quot; Adobe Commerce sur notre architecture cloud pro

Il s’agit du comportement attendu pour les solutions d’architecture de plan Adobe Commerce sur l’infrastructure cloud Pro en raison de l’architecture à 3 noeuds et il ne peut pas être modifié.

La grappe de base de données Galera est utilisée, c’est-à-dire une grappe de base de données avec une base de données MariaDB MySQL par noeud avec un paramètre d’incrémentation automatique de trois pour les identifiants uniques de chaque base de données.

<u>Pourquoi l’identifiant d’incrément utilisé sur les grappes Pro n’est-il pas toujours séparé/incrémenté par 3 ?</u>

L’ID d’incrément utilisé sur les grappes ne sera pas toujours séparé/incrémenté par 3 en raison du fonctionnement de Galera.

Chacun des trois serveurs gère son propre espace d’identification. L’incrément utilisé dépend de celui du serveur de base de données principal MySQL (en fonction de la charge relative), d’où les écarts variables.
Si vous SSH sur chaque noeud et que vous vous connectez à l’instance MySQL locale s’exécutant sur ce noeud à l’aide du port 3307 (au lieu d’être proxy sur &quot;main&quot; sur le port standard 3306), l’image suivante s’affiche :

![auto_incrément](assets/auto_increment_id.png)

Par exemple, si la principale sélectionnée est le noeud 1 où `auto_increment_offset = 1`, l’identifiant sera incrémenté de 1. Ensuite, si un nouveau noeud principal est sélectionné ultérieurement, par exemple, le noeud 3 où `auto_increment_offset = 3`, il sera incrémenté de 3 à la place.

## Liens utiles

Consultez la documentation destinée aux développeurs :

* [Cloud pour Adobe Commerce > Architecture Pro > Sauvegarde et reprise après sinistre](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Cloud pour Adobe Commerce > Installer les prérequis : base de données](https://devdocs.magento.com/cloud/before/before-workspace-magento-prereqs.html#database)
