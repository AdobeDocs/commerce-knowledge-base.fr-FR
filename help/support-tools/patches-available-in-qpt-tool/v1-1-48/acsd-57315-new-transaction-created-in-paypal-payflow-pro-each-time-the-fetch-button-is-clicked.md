---
title: '''ACSD-57315 : Nouvelle transaction créée dans [!DNL PayPal Payflow Pro] chaque fois que vous cliquez sur le bouton de récupération"'
description: Appliquez le correctif ACSD-57315 pour résoudre le problème Adobe Commerce où une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton de récupération dans l’écran d’affichage des transactions de la [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315 : Nouvelle transaction créée dans [!DNL PayPal Payflow Pro] chaque fois que vous cliquez sur le bouton de récupération

Le correctif ACSD-57315 corrige le problème de création d’une transaction dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton de récupération dans l’écran d’affichage des transactions de la [!UICONTROL Admin]. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.48 est installée. L’ID de correctif est ACSD-57315. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.5.0.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p4

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une nouvelle transaction est créée dans [!DNL PayPal Payflow Pro] chaque fois que l’utilisateur clique sur le bouton de récupération dans l’écran d’affichage des transactions de la [!UICONTROL Admin].

<u>Étapes à reproduire</u>:

1. Configurer [!DNL PayPal Payflow Pro].
1. Définissez la méthode de transaction sur *[!UICONTROL Sale]*.
1. Placez une commande à l’aide de *Carte de crédit*.
1. Ouvrir la transaction à partir de [!UICONTROL Admin].
1. Cliquez sur le bouton **[!UICONTROL Fetch]** bouton .
1. Vérifier [!DNL PayPal] compte pour les transactions liées à la commande passée.

<u>Résultats attendus</u>:

Une nouvelle transaction de paiement n’est pas créée.

<u>Résultats réels</u>:

Une nouvelle transaction de paiement est créée pour une commande déjà payée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
