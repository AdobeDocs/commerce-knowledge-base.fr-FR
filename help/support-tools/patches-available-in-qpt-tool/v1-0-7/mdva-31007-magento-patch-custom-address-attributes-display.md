---
title: 'MDVA-31007 : affichage des attributs d’adresse personnalisés'
description: Le correctif MDVA-31007 résout le problème en raison duquel les attributs d’adresse personnalisés ne s’affichent pas correctement dans la page des détails de la commande dans la zone Mon compte et dans le serveur principal (à l’emplacement **Sales &gt; Commandes**). Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007 : affichage des attributs d’adresse personnalisés

Le correctif MDVA-31007 résout le problème en raison duquel les attributs d’adresse personnalisés ne s’affichent pas correctement dans la page des détails de la commande dans la zone Mon compte et dans le serveur principal (à l’emplacement **Ventes > Commandes**). Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7 est installé. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce sur l’infrastructure cloud 2.4.0

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u> :

1. Connectez-vous au serveur principal d’administration.
1. Accédez à **Magasins** > **Attributs** > **Adresses client**.
1. Créez deux attributs :

   * Définissez le type d’entrée : *Liste déroulante*.
   * Définissez le type d’entrée : *Texte*.

1. Accédez à **Magasins** > **Configurations** > **Client** > **Configurations client**.
1. Sélectionnez *Portée* comme vue **Boutique par défaut**.
1. Développez la section **Modèle d’adresse** . Mettez à jour *Text*, *Text One Line* et *HTML* pour inclure les deux attributs personnalisés ci-dessus :

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. Ouvrez Storefront.
1. Créez et connectez-vous avec un utilisateur.
1. Accédez à **Mon compte** > **Carnet d&#39;adresses** et ajoutez une nouvelle adresse (renseignez les deux attributs personnalisés).
1. Ajoutez un produit au panier et passez une commande.
1. Sur la page de succès de la commande, cliquez sur le lien **Numéro de commande**.
1. Sur la page des détails de la commande, observez la section **Informations sur la commande**.
1. Accédez à **Serveur principal** > **Ventes** > **Commandes**, cliquez sur la commande ci-dessus et observez la section **Informations sur l&#39;adresse**.

<u>Résultats attendus</u> :

Sur le front-end et le serveur principal, l’adresse de facturation et de livraison s’affiche comme prévu.

<u>Résultats réels</u> :

Sur le front-end et le serveur principal, l’adresse de facturation ne s’affiche pas correctement. L’option sélectionnée de l’attribut de liste déroulante est manquante et la valeur de l’attribut d’entrée contient le code d’attribut.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
