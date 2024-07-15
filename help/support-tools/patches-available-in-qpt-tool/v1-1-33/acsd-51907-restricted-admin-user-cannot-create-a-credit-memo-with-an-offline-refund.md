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

Le correctif ACSD-51907 corrige le problème de performances où l’utilisateur administrateur restreint ne peut pas créer d’avoir avec un remboursement hors ligne. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.33 est installé. L’ID de correctif est ACSD-51907. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un utilisateur administrateur restreint ne peut pas créer d’avoir avec un remboursement hors ligne.

<u>Étapes à reproduire</u> :

1. Créez un **customer** sur le site web par défaut.
1. Créez **un nouveau site Web** avec les *magasin* et *vue de magasin* associés.
1. Définissez le site web par défaut sur le nouveau site web. Effacez les caches.
1. Modifier la configuration du client : **Admin** > **Magasin** > **Configuration** > **Clients** > **Configuration du client** > **Partager les comptes du client = Global**.
1. Créez un nouveau rôle d’utilisateur administrateur avec la portée du rôle définie sur le nouveau site web *(accès aux données commerciales uniquement)* dans **Admin** > **Système** > **Autorisations**}.
1. Créez un compte administrateur avec ce rôle.
1. Créez une nouvelle commande à l’aide du mode de paiement en ligne *(par exemple, Auth.net ou PayPal)*.
1. Connectez-vous en tant qu’utilisateur administrateur restreint.
1. Accédez à **Sales** > **Commandes** > puis **page de vue de commande**.
1. Créez une facture.
1. Accédez à l’onglet Factures .
1. Cliquez sur **Invoice**.
1. Cliquez sur **[!UICONTROL Credit Memo]**.
1. Cochez la case **[!UICONTROL Refund to Store Credit]** et définissez le champ de texte à proximité de la valeur *1* .
1. Cliquez sur le bouton **[!UICONTROL Refund Offline]** .

<u>Résultats attendus</u> :

La note de crédit est créée et *$1* est remboursé au crédit de la boutique.

<u>Résultats réels</u> :

Le message d’erreur, *Plus d’autorisations sont nécessaires pour afficher cet élément* s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce en utilisant  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
