---
title: Recherche avancée n’affichant pas les résultats les plus pertinents
description: Cet article fournit un correctif pour le problème Adobe Commerce connu, où la recherche avancée n’affiche pas en premier les résultats les plus pertinents.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Recherche avancée n’affichant pas les résultats les plus pertinents

Cet article fournit un correctif pour le problème Adobe Commerce connu, où la recherche avancée n’affiche pas en premier les résultats les plus pertinents.

## Versions affectées {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce (toutes les options de déploiement) 2.x.x
* Magento Open Source 2.x.x

## Problème {#Advancedsearchnotshowingmostrelevantresults-Description}

La fonction de recherche avancée ne renvoie pas d’abord les résultats les plus pertinents, comme le fait la recherche rapide. Le problème ne dépend pas du type de moteur de recherche sélectionné.

<u>Étapes à reproduire :</u>

1. Sur le storefront, accédez à la recherche rapide et recherchez &quot;Veste ajustée&quot;.
1. Remarquez &quot;Orion Two-Tone Fighet Jacket&quot; (Veste ajustée à deux tons d&#39;Orion) est le premier résultat.
1. Accédez à la recherche avancée et recherchez &quot;Veste ajustée&quot; dans le champ du nom.

<u>Résultat attendu :</u>

Le &quot;Jacket ajusté à deux tons Orion&quot; est le premier résultat obtenu lors de l’utilisation de la recherche avancée, comme résultat le plus pertinent.

<u>Résultat réel :</u>

La &quot;Jacket ajustée à deux tons Orion&quot; n&#39;est pas le premier résultat, bien que ce soit le plus pertinent.

## Solution {#Advancedsearchnotshowingmostrelevantresults-Solution}

Pour résoudre le problème, appliquez le correctif joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[Téléchargez MDVA-7256\_EE\_2.1.7\_v1.compositeur.patch.](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

Le correctif ajoute l’implémentation pour le tri par pertinence pour les résultats de recherche avancée comme champ de tri par défaut.

Le correctif est compatible avec toutes les versions et éditions concernées.

## Comment appliquer le correctif

Pour obtenir des instructions, voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

## Fichiers attachés
