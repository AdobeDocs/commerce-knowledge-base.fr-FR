---
title: "ACSD-50478 : problème JS pour l’action de restauration dans la grille de sauvegardes et la commande de restauration de base de données"
description: Appliquez le correctif ACSD-50478 afin de résoudre le problème JS pour l’action de restauration dans la grille de sauvegardes et la commande de restauration de la base de données dans le cas où le vidage DB contient des déclencheurs et une commande SQL *délimiteur*.
exl-id: 8b516705-29be-462e-b3ec-3a339b6e8006
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-50478 : problème JS pour l’action de restauration dans la commande de restauration de la grille de sauvegardes et de la base de données

Le correctif ACSD-50478 corrige le problème JS pour l’action de restauration dans la grille de sauvegardes et la commande de restauration de la base de données dans le cas où le vidage DB contient des déclencheurs et une commande SQL *délimiteur*. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33 est installé. L’ID de correctif est ACSD-50478. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Problème JS pour l’action de restauration dans la grille Sauvegardes et la commande de restauration de la base de données pour un cas où le vidage DB contient des déclencheurs et une commande SQL *délimiteur*.

<u>Étapes à reproduire</u> :

1. Définissez les indexeurs sur le mode [!UICONTROL Update on Schedule] afin que les déclencheurs soient créés dans la base de données.
1. Activez la fonctionnalité de sauvegarde à partir de la ligne de commande :

   `bin/magento config:set system/backup/functionality_enabled 1`

1. Accédez à **Système** > **Outils** > **Sauvegardes** et générez une sauvegarde DB.
1. Ouvrez la console du navigateur ; l’erreur suivante s’affiche :

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. Essayez d’importer la base de données à partir de la ligne de commande :

   `bin/magento setup:rollback --db-file="<filename>"`

1. L’erreur suivante s’affiche :

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>Résultats attendus</u> :

La restauration de la base de données a réussi à partir de la ligne de commande et de l’administrateur.

<u>Résultats réels</u> :

Vous avez observé les erreurs mentionnées aux étapes 4 et 6.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
