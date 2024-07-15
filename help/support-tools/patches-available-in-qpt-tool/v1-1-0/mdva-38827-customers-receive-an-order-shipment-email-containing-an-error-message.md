---
title: 'MDVA-38827 : les clients reçoivent une erreur de livraison de commande par email'
description: "Le correctif MDVA-38827 corrige le problème en raison duquel les clients reçoivent un email d’expédition de commande contenant le message d’erreur suivant : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0 est installé. L’ID de correctif est MDVA-38827. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4."
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827 : les clients reçoivent une erreur d’expédition de commande par courrier électronique

Le correctif MDVA-38827 corrige le problème en raison duquel les clients reçoivent un email d’expédition de commande contenant le message d’erreur suivant : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0 est installé. L’ID de correctif est MDVA-38827. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque l’option Avertir les clients par courrier électronique pour l’envoi est sélectionnée, les clients reçoivent un courrier électronique contenant le message d’erreur suivant : *Nous sommes désolés, une erreur s’est produite lors de la génération de ce contenu*.

<u>Étapes à reproduire</u> :

1. Accédez à **Marketing** > **Communications** > **Modèles d’e-mail** et sélectionnez **Ajouter un nouveau modèle**.
   * Sélectionnez **Ventes de Magento** > **Nouvel expédition**.
   * Cliquez sur **Charger le modèle**.
   * Ajoutez un nom de modèle (par exemple, modèle d’expédition principal) et cliquez sur **Enregistrer**.
1. Accédez à **Magasin** > Paramètres > **Configuration** > **Ventes** > **Courrier électronique de vente** :
   * Activez **Commentaires d’expédition**.
   * Sélectionnez **Modèle d’expédition principal** (voir la partie &quot;Ajouter un nom de modèle&quot; de l’étape 1) sous Modèle d’email de commentaire d’envoi et Modèle d’email de commentaire d’envoi pour l’invité.
1. passé une commande ; Accédez au panneau d’administration > **Ventes** > **Commande**, cliquez sur **Afficher**, puis envoyez la commande.
1. L’état de la commande passe de En attente à Traitement.
1. Cliquez sur **Expéditions** dans le menu de la barre latérale gauche, puis cliquez sur **Afficher** pour afficher la commande.
1. Ajoutez un commentaire dans **Texte de commentaire** sous **Historique des envois** et cochez la case **Avertir le client par courrier électronique**.
1. Cliquez sur **Submit Comment**.

<u>Résultats attendus</u> :

Un courrier électronique de vente contenant des commentaires d’expédition est généré.

<u>Résultats réels</u> :

Le message d&#39;erreur suivant est reçu dans l&#39;email : *Nous sommes désolés, une erreur s&#39;est produite lors de la génération de ce contenu.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
