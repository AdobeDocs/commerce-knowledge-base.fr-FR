---
title: "ACSD-51907 : L’utilisateur administrateur restreint ne peut pas créer de note de crédit pour le remboursement hors ligne"
description: Appliquez le correctif ACSD-51907 pour résoudre le problème Adobe Commerce en raison duquel l’utilisateur administrateur restreint ne peut pas créer d’avoir avec un remboursement hors ligne.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907 : L’utilisateur administrateur restreint ne peut pas créer de note de crédit pour le remboursement hors ligne.

Le correctif ACSD-51907 corrige le problème de performances où l’utilisateur administrateur restreint ne peut pas créer d’avoir avec un remboursement hors ligne. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.33 est installée. L’ID de correctif est ACSD-51907. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur restreint ne peut pas créer d’avoir avec un remboursement hors ligne.

<u>Étapes à reproduire</u>:

1. Créez un **client** sur le site web par défaut.
1. Créer **nouveau site web** avec *store* et *vue de magasin*.
1. Définissez le site web par défaut sur le nouveau site web. Effacez les caches.
1. Modifier la configuration du client : **Administration** > **Magasin** > **Configuration** > **Clients** > **Configuration client** > **Partager les comptes client = Global**.
1. Créez un rôle d’utilisateur administrateur avec la portée du rôle définie sur le nouveau site web créé. *(accès aux données de vente uniquement)* in **Administration** > **Système** > **Autorisations**.
1. Créez un compte administrateur avec ce rôle.
1. Créer une commande à l’aide du mode de paiement en ligne *(par exemple, Auth.net ou PayPal)*.
1. Connectez-vous en tant qu’utilisateur administrateur restreint.
1. Accédez à **Ventes** > **Commandes** > puis **page d’affichage des commandes**.
1. Créez une facture.
1. Accédez à l’onglet Factures .
1. Cliquez sur **Facture**.
1. Cliquez sur **[!UICONTROL Credit Memo]**.
1. Vérifiez les **[!UICONTROL Refund to Store Credit]** , définissez le champ de texte à proximité de la case à cocher *1* .
1. Cliquez sur le bouton **[!UICONTROL Refund Offline]** bouton .

<u>Résultats attendus</u>:

l’avoir est créé, et *$1* est remboursé au crédit de la boutique.

<u>Résultats réels</u>:

le message d&#39;erreur, *Plus d’autorisations sont nécessaires pour afficher cet élément* s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
