---
title: "MDVA-39163 : Méthodes de livraison non disponibles pour les utilisateurs nouvellement enregistrés avec des produits d’une session d’invité"
description: Le correctif MDVA-39163 résout le problème en raison duquel les méthodes d’expédition ne sont pas disponibles lorsqu’un nouvel utilisateur est enregistré et que les produits du panier proviennent de la session d’invité. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9 est installé. L’ID de correctif est MDVA-39163. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163 : Méthodes de livraison non disponibles pour les utilisateurs nouvellement enregistrés avec des produits d’une session d’invité

Le correctif MDVA-39163 résout le problème en raison duquel les méthodes d’expédition ne sont pas disponibles lorsqu’un nouvel utilisateur est enregistré et que les produits du panier proviennent de la session d’invité. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.9 est installée. L’ID de correctif est MDVA-39163. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les méthodes d’expédition ne sont pas disponibles lorsque le nouvel utilisateur est enregistré et que les produits du panier proviennent de la session d’invité.

<u>Étapes à reproduire</u>:

1. Accédez à **Administration** > **Magasins** > **Configuration** > **Ventes** > **Méthodes de diffusion**. Activez uniquement la variable **Taux d&#39;aplatissement** méthode d’expédition et désactivez tout le reste.
1. Dans le **Taux d&#39;aplatissement** mode d’expédition, sélectionnez **Spécifique** option country disponible dans **Expédier aux pays applicables** et sélectionnez un pays dans la liste (États-Unis, par exemple).
1. Accédez à **Administration** > **Magasins** > **Configuration** > **Client** > **Configuration client** et défini **Confirmation du message électronique requise** to _Oui_.
1. Créez un modèle de courrier électronique dans **Administration** > **Marketing** > **Modèles de courrier électronique** et chargement `Footer (magento/luma)` et remplacez le contenu du modèle par un bloc CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Accédez à **Administration** > **Contenu** > **Conception** > **Configuration** et sélectionnez le thème associé à votre site web frontend. Définissez le &quot;Modèle de pied de page&quot; sur le nouveau modèle d’email créé.
1. Positionnez-vous sur l&#39;interface frontale et ajoutez un produit au panier.
1. Créez un client ; vous obtiendrez un courrier électronique pour confirmer l’adresse électronique. Cliquez sur le lien de vérification. Vous serez connecté au site web.
1. Accédez à **Mon compte** et ajoutez une adresse. Définissez le pays de l’adresse sur le pays de livraison que vous avez précédemment défini dans la configuration d’administration.
1. Allez à la caisse.

<u>Résultats attendus</u>:

Le mode de livraison est disponible, car le client possède une adresse compatible avec le pays de livraison.

<u>Résultats réels</u>:

Le mode de livraison n’est pas disponible.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
