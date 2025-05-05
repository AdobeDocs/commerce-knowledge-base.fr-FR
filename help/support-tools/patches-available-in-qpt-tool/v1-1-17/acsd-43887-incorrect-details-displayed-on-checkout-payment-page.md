---
title: "ACSD-43887 : informations incorrectes affichées sur la page de paiement du passage en caisse"
description: Le correctif ACSD-43887 corrige le problème en raison duquel des détails incorrects s’affichaient sur la page de paiement du passage en caisse lorsque les commandes d’achat pour les entreprises étaient activées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 est installé. L’ID de correctif est ACSD-43887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887 : informations incorrectes affichées sur la page de paiement du passage en caisse

Le correctif ACSD-43887 corrige le problème en raison duquel des détails incorrects s’affichaient sur la page de paiement du passage en caisse lorsque les commandes d’achat pour les entreprises étaient activées. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 est installé. L’ID de correctif est ACSD-43887. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des détails incorrects s’affichent sur la page de paiement du passage en caisse lorsque les commandes d’achat des entreprises sont activées.

<u>Conditions préalables</u> :

1. Les modules B2B sont installés.
1. L’option Activer la société est définie sur _Oui_. Accédez à **Magasins** > **Configurations** > **Général** > **Fonctionnalités B2B** > **Activer la société** > **Oui**.
1. L’option Activer les commandes d’achat est définie sur _Oui_. Accédez à **Configuration d’approbation de commande** > **Activer les commandes** > **Oui**.
1. PayPal Express est configuré comme mode de paiement.

<u>Étapes à reproduire</u> :

1. Créez un produit virtuel.
1. Enregistrez un compte de société à partir de l’interface avec un administrateur de société.
1. Approuvez le compte de la société depuis le serveur principal et définissez **Activer les commandes** sur _Oui_ lors de l’approbation de la société.
1. Accédez à l’interface frontale et connectez-vous à l’aide du compte administrateur de l’entreprise créé à l’étape 2.
1. Créez un &quot;utilisateur par défaut&quot; pour la société. Accédez à **Utilisateur de la société** > **Ajouter un nouvel utilisateur**.
1. Créez une &quot;règle d’approbation&quot; pour la société. Accédez à **Règles d’approbation** > **Ajouter une nouvelle règle**.

   * Type de règle : Total de la commande
   * Total de la commande : est supérieur ou égal à 1 $
   * Demande l’approbation de : administrateur de l’entreprise

1. Déconnectez-vous et connectez-vous à l’aide du compte &quot;Utilisateur par défaut&quot;.
1. Ajoutez le produit virtuel créé à l’étape 1 au panier et passez en caisse.
1. Sélectionnez PayPal Express comme mode de paiement et cliquez sur **Passer un bon de commande**.
1. Déconnectez-vous et connectez-vous à l’aide du compte administrateur de la société.
1. Accédez à **Mes commandes** et, dans **Commandes d’achat d’entreprise**, cliquez sur **Afficher** pour la commande créée à l’étape 9.
1. Validez le bon de commande. Le statut du bon de commande doit être &quot;Approuvé : paiement en attente&quot;.
1. Déconnectez-vous et connectez-vous à l’aide du compte &quot;Utilisateur par défaut&quot; de la société.
1. Accédez à **Mes commandes** > **Vue** > **Passer commande**.
1. Vérifiez le **résumé de la commande**.

<u>Résultats attendus</u> :

Le résumé de la commande affiche les valeurs correctes non nulles.

<u>Résultats réels</u> :

La valeur totale du résumé de la commande est zéro.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
