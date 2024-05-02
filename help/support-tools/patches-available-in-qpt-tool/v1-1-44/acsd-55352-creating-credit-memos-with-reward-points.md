---
title: "ACSD-55352 : création de crédits à crédit avec des points de récompense"
description: Appliquez le correctif ACSD-55352 pour résoudre le problème Adobe Commerce en raison duquel, après la création d’un avoir partiel avec des points de récompense client, l’état de la commande passe à *fermé* et les options de note de crédit disparaissent de la page de commande de l’administrateur.
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352 : création de crédits à crédit avec des points de récompense

Le correctif ACSD-55352 corrige le problème en raison duquel, après la création d’un avoir de crédit partiel avec des points de récompense client, l’état de la commande passe à *fermée* et les options de note de crédit disparaissent de la page de commande de l’administrateur. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.44 est installée. L’ID de correctif est ACSD-55352. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Après la création d’un avoir partiel avec des points de récompense client, l’état de la commande passe à *fermée* et les options de note de crédit disparaissent de la page de commande de l’administrateur.

<u>Étapes à reproduire</u>:

1. Connectez-vous à l’administrateur Adobe Commerce.
2. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Ajoutez deux taux :
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Points vers une devise*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Devise en points*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Créer un produit simple avec le prix de *100 $* et avec *Qté* : *100*.
5. Créez un client à partir du storefront.
6. Revenez au serveur principal : **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Ajouter *100* et enregistrez le client.
7. Accédez au storefront et connectez-vous comme le client créé précédemment.
8. Ajouter le produit au panier avec *Qté* : *10*.
9. Accédez à **[!UICONTROL Checkout]** et utiliser les *100* points de récompense lorsque vous y êtes invité et passez la commande.
10. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** et expédiez cette commande.
11. Accédez à [!UICONTROL Credit Memo] et mettre à jour la variable *Qté à rembourser* to *8*.
12. Cliquez sur le bouton **[!UICONTROL Refund Reward Points]** case à cocher et clic **[!UICONTROL Refund offline]**.
13. Essayez de rembourser les deux autres produits de la commande, en utilisant la variable [!UICONTROL Credit Memo].

<u>Résultats attendus</u>:

* L’administrateur crée [!UICONTROL Credit Memo] pour renvoyer les deux produits restants.
* L’état de la commande est *Terminé*.

<u>Résultats réels</u>:

* Impossible de créer plus [!UICONTROL Credit Memo].
* L’état de la commande est *Fermé*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
