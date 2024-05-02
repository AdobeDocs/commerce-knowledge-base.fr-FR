---
title: "ACSD-52133 : impossible d’enregistrer le compte client après une mise à niveau"
description: Appliquez le correctif ACSD-52133 pour résoudre le problème Adobe Commerce en raison duquel un compte client ne peut pas être enregistré après une mise à niveau.
feature: Customers, Upgrade
role: Admin
exl-id: 0db7c79e-10e1-4850-81b5-4812fb051941
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-52133 : le compte client ne peut pas être enregistré après une mise à niveau

Le correctif ACSD-52133 corrige le problème lorsqu’un compte client ne peut pas être enregistré après une mise à niveau. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.35 est installée. L’ID de correctif est ACSD-52133. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le compte client ne peut pas être enregistré après une mise à niveau.

<u>Étapes à reproduire</u>:

1. Installez Adobe Commerce version 2.4.4.
1. Créez un client.
1. Mettez à niveau Adobe Commerce vers la version 2.4.6 à partir de la version précédente de 2.4.4 où un client a déjà été créé.
1. Définissez la clé de chiffrement comme ci-dessous dans `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Définissez les valeurs ci-dessous dans la base de données pour n’importe quel client sous le `customer_entity` table :

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Accédez à **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifiez le client pour lequel les valeurs ci-dessus ont été mises à jour.
1. Cliquez sur **[!UICONTROL Save Customer]** ou **[!UICONTROL Save and Continue Edit]**

<u>Résultats attendus</u>:

Le client est enregistré avec succès sans erreur.

<u>Résultats réels</u>:

* L’enregistrement du client n’est pas enregistré.
* L’administrateur voit le message d’erreur suivant : *Un problème s’est produit lors de l’enregistrement du client.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
