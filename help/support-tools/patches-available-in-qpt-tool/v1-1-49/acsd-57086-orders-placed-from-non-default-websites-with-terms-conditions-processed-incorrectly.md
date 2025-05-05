---
title: "ACSD-57086 : les commandes des sites web autres que les sites web par défaut pour lesquels les termes et conditions sont activés sont traitées incorrectement"
description: Appliquez le correctif ACSD-57086 pour résoudre le problème Adobe Commerce en raison duquel les commandes passées à partir de sites web non par défaut avec des termes et conditions activés ne sont pas traitées correctement.
feature: Orders
role: Admin, Developer
source-git-commit: ab90568b0333415e73ca42b9c127a2a599f00aa7
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---


# ACSD-57086 : les commandes des sites web autres que les sites web par défaut pour lesquels les termes et conditions sont activés sont traitées incorrectement.

Le correctif ACSD-57086 corrige le problème en raison duquel les commandes passées à partir de sites web autres que les termes et conditions activés ne sont pas traitées correctement. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49 est installé. L’ID de correctif est ACSD-57086. Veuillez noter que ce problème a été corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p5

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’utilisation d’une configuration multi-magasin avec le traitement AsyncOrder, les commandes placées sur des sites web/magasins autres que le site web principal sont rejetées en raison de problèmes liés à la gestion de la portée dans le code du consommateur de file d’attente.

<u>Étapes à reproduire</u> :

1. Installez [!DNL RabbitMQ] et exécutez `bin/magento setup:upgrade` pour créer les files d’attente pour [!DNL RabbitMQ].
1. Configurez le traitement AsyncOrder avec :

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Créez un site web secondaire, un magasin et une vue de magasin.
1. Créez un produit qui est partagé entre les deux sites web.
1. Activez les conditions générales :
   1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
   1. Définissez *[!UICONTROL Enable Terms And Conditions]* sur *Yes*.
1. Configurez les conditions générales des deux sites web :
   1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**.
   1. Utilisez les paramètres suivants :
      * *[!UICONTROL Condition Name]* : *Tout*
      * *[!UICONTROL Status]* : *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]* : *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]* : *[!UICONTROL Default Store View]*
   1. Créez une autre condition pour la deuxième vue de site web/magasin.
1. Modifiez le site web par défaut en accédant à **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**. Cliquez sur le deuxième site web, vérifiez *[!UICONTROL Set as Default]* et enregistrez.
1. Effacez le cache avec :

   ```bash
   bin/magento cache:clear
   ```

1. Accédez à Storefront et ajoutez un produit au panier. Passez à la caisse et passez une commande (une case à cocher devrait s’afficher à l’étape du mode de paiement pour accepter les conditions générales).
1. Revenez à Admin après avoir passé la commande, puis redéfinissez le site web par défaut sur le site web principal d’origine et enregistrez-le.
1. Effacez le cache :

   ```bash
   bin/magento cache:clear
   ```

1. Exécutez la commande suivante pour démarrer le consommateur de file d’attente :

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>Résultats attendus</u> :

L&#39;ordre est respecté ; il n&#39;est pas automatiquement rejeté.

<u>Résultats réels</u> :

L’état de la commande est *reject* avec le commentaire suivant :

*La commande n’a pas été placée. Commencez par accepter les conditions générales, puis essayez à nouveau de passer votre commande.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
