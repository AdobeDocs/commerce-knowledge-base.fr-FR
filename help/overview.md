---
title: Base de connaissances du support Adobe Commerce
description: Tout ce que vous devez savoir pour résoudre les problèmes et gérer votre boutique Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 0%

---

# Base de connaissances du support Adobe Commerce

>[!NOTE]
>
>Le guide de la base de connaissances de la prise en charge d’Adobe Commerce sera bientôt restructuré et son contenu sera déplacé vers d’autres emplacements dans Adobe Experience League. En attendant, nous continuerons à gérer et mettre à jour le contenu de ce guide.

![Page d’accueil de la base de connaissances](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Les informations de cette base de connaissances sont conçues comme complémentaires à la [documentation du développeur Adobe Commerce](https://developer.adobe.com/commerce/docs), au [Guide du marchand Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) et à d’autres publications Adobe Commerce. Il couvre le dépannage et les bonnes pratiques, héberge des annonces, répond aux questions fréquentes et met en évidence des scénarios spécifiques qui n’ont pas été mentionnés (pour une raison quelconque) dans la documentation officielle.

## Qu’est-ce que contient cette base de connaissances ?

| CATÉGORIE | DESCRIPTION |
| --- | --- |
| [Outils d’assistance](/help/support-tools/overview.md) | Améliorez votre expérience de la boutique en ligne grâce aux différents outils d’assistance proposés par Adobe Commerce. Nous fournissons des bonnes pratiques personnalisées, des outils de diagnostic et de surveillance, ainsi que les informations les plus pertinentes sur votre site. |
| [Annonces](/help/announcements/overview.md) | Obtenez des mises à jour importantes de la part des équipes Adobe Commerce. |
| [Dépannage](/help/troubleshooting/overview.md) | Procurez-vous des solutions et correctifs en libre-service auprès de l’équipe d’assistance d’Adobe Commerce. |
| [Guide de l’utilisateur du centre d’aide](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Découvrez comment gérer vos tickets d’assistance, accorder un accès partagé et parcourir efficacement la base de connaissances. |
| [Procédures](/help/how-to/overview.md) | Suivez les instructions détaillées de l’équipe d’assistance d’Adobe Commerce. |
| [FAQ](/help/faq/overview.md) | Découvrez les questions fréquentes sur les stratégies, les stratégies et les détails d’Adobe Commerce concernant les fonctionnalités d’Adobe Commerce. |

## Nouveautés

<table style="width:100%">
  <tr>
    <th style="width:70%">Description</th>
    <th style="width:15%">Type</th>
    <th style="width:15%">Date</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">L’outil d’analyse de sécurité renvoie "Impossible de déterminer si votre serveur utilise 2FA":</a> Pour résoudre l’erreur, vérifiez si le module <code>Magento_TwoFactorAuth</code> a été désactivé. Pour réussir la vérification, elle doit généralement être activée.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt"> ACSD-60632 : adresse enregistrée avec chaque tentative de commande : </a> Le correctif ACSD-60632 corrige le problème d’enregistrement d’une nouvelle adresse à chaque tentative de placement de commande, que la commande ait été créée ou non. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326 : Requête GraphQL sur le statut du retour du client donne une erreur :</a> Le correctif ACSD-60326 corrige le problème lorsqu’une erreur se produit dans la requête GraphQL pour le statut de retour du client. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925 : Tri des éléments dans la galerie de médias par position dans GraphQL :</a> Le correctif ACSD-59925 corrige le problème en raison duquel les éléments dans la galerie de médias ne sont pas triés par position, ce qui entraîne un ordre d’affichage incorrect. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322 : les produits non affectés au catalogue partagé sont inclus dans le plan de site XML :</a> Le correctif ACSD-61322 corrige le problème en raison duquel les produits/catégories non affectés au catalogue partagé pour le groupe Par défaut (Général) sont toujours inclus dans le plan de site XML. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590 : amélioration des performances de la génération de rapports quotidiens agrégés des Bestsellers :</a> Le correctif ACSD-60590 corrige le problème en raison duquel le rapport quotidien agrégé des Bestsellers prend un temps important pour générer un volume important de commandes passées. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865 : La règle du prix du panier ne parvient pas à annuler les règles précédentes en raison d’une quantité insuffisante de produits :</a> Le correctif ACSD-59865 corrige le problème où la valeur de l’ <em>étape de quantité de rabais</em> dans <em>remise de prix fixe</em>, <em>pourcentage de remise sur le prix du produit</em> et <em>achat X obtenant Y} Les règles de prix du panier n’annulent plus l’action des règles précédentes. </em> Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">Erreur lors du filtrage des commandes dans l’Admin :</a> Cet article fournit un correctif pour le problème Adobe Commerce où une erreur se produit lorsqu’une tentative de filtrage des commandes dans l’Admin par date affiche le message : <em>Violation de contrainte d’intégrité : 1052 Colonne 'created_at' où la clause est ambiguë</em>.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce : problèmes JavaScript en ligne sur la page de passage en caisse en mode restreint de la stratégie de sécurité du contenu (CSP) :</a> Cet article fournit des explications détaillées et des solutions pour les problèmes rencontrés avec JavaScript personnalisé ajouté via Adobe Commerce Admin et Google Tag Manager dans Adobe Commerce 2.4.7 lors du passage en caisse lorsque le <strong>mode restreint CSP</strong> est activé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195 : la demande GraphQL du panier ne parvient pas à renvoyer les éléments sur la dernière page : </a> Le correctif ACSD-61195 corrige le problème lorsqu’aucun élément de panier n’est renvoyé sur la dernière page pour la demande GraphQL du panier. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514 : Forms dans Admin avec le Créateur de pages renvoie une erreur dans la console du navigateur :</a> Le correctif ACSD-59514 corrige le problème en raison duquel les formulaires dans Admin avec le Créateur de pages généraient l’erreur <em>Le Créateur de pages effectuait le rendu pendant 5 secondes sans déclencher de verrouillage</em> dans la console du navigateur après l’envoi du formulaire, et les modifications ne peuvent pas être enregistrées. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538 : les attributs ne s’affichent pas correctement si le produit est désactivé dans <em>Toutes les vues de magasin</em> : </a> Le correctif ACSD-60538 corrige le problème en raison duquel si un produit est désactivé dans <em>Toutes les vues de magasin</em> et activé uniquement dans des portées de vue de magasin spécifiques, les attributs de produit ne s’affichent pas correctement dans la réponse GraphQL. produit ne s’affiche pas correctement. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352 : Les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via l’API GraphQL :</a> Le correctif ACSD-58352 corrige le problème en raison duquel les libellés d’attribut de retour pour le magasin par défaut sont renvoyés via l’API GraphQL lorsqu’une vue de magasin autre que celle par défaut est spécifiée dans l’en-tête de requête. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">La liste déroulante <em>Changer de compte</em> est absente de votre compte :</a> Cet article fournit une solution au problème Adobe Commerce où la liste déroulante <em>Changer de compte</em> est absente de votre compte et où vous avez perdu l’accès à l’envoi de tickets pour le compte du commerçant.
    </td>
    <td>Nouvel article</td>
    <td>17 octobre 2024</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979 : suppression des images de produit après suppression de la mise à jour d’évaluation : </a> Le correctif ACSD-56979 corrige le problème en raison duquel les images de produit sont supprimées après suppression d’une mise à jour d’évaluation. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.49 est installé.  
    </td>
    <td>Nouvel article</td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210 : les attributs de portée spécifiques de la vue de magasin remplacent les valeurs globales :</a> Le correctif ACSD-48210 corrige le problème en raison duquel, lors de la mise à jour d’un attribut <em>Portée du site Web</em> dans une vue de magasin spécifique, les valeurs d’attribut dans la portée globale. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280 : erreur ReflectionUnionType::getName() dans les installations 2.4.4-pX :</a> Le correctif ACSD-59280 corrige le problème où l’appel à la méthode non définie <code>ReflectionUnionType::getName()</code> se produit pendant l’installation des versions 2.4.4-pX. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887 : le panier client est effacé une fois la session du client expirée :</a> Le correctif ACSD-54887 corrige le problème en raison duquel le panier du client est effacé une fois la session du client expirée avec l’activation de <em>Panier persistant</em>. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303 : résolution du problème d’emplacement des commandes d’administration avec la minification d’HTML activée :</a> Le correctif ACSD-60303 corrige le problème qui empêchait de placer une commande d’Admin si la minification d’HTML était activée. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045 : les réécritures d’URL provoquent une boucle de page infinie après <em>Racine du site Web</em> non cochée dans la hiérarchie : </a> Le correctif ACSD-57045 corrige le problème où les réécritures d’URL provoquent une boucle de page infinie après que <em>Racine du site Web</em> n’est décoché dans la hiérarchie. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.49 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446 : La suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL donne un message d’erreur non informatif :</a> Le correctif ACSD-58446 corrige le problème Adobe Commerce où la suppression d’une équipe avec des utilisateurs ou des équipes enfants via GraphQL renvoie un message d’erreur non informatif incompatible avec l’interface utilisateur. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.49 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735 : Une clé d’API YouTube mal configurée provoque une erreur lors de l’ajout de la vidéo au niveau de l’affichage du magasin :</a> Le correctif ACSD-58735 corrige le problème en raison duquel une configuration de clé d’API YouTube incorrecte provoque une erreur lors de l’ajout d’une vidéo YouTube au niveau de l’affichage du magasin. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.49 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086 : les commandes de sites web non par défaut pour lesquels les termes et conditions sont activés sont traitées incorrectement :</a> Le correctif ACSD-57086 corrige le problème en raison duquel les commandes passées à partir de sites web non par défaut pour lesquels les termes et conditions sont activés ne sont pas traitées correctement. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.49 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141 : PHPSESSID se régénère sur les demandes du POST pour les clients connectés si le cache de Redis L2 est activé :</a> Le correctif ACSD-58141 corrige le problème où PHPSESSID se régénère sur les demandes du POST pour un client connecté si le cache de Redis L2 est activé et le client est mis à jour depuis l’administrateur. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790 : corrige la fonctionnalité de pincement pour zoomer sur les images de la page des détails du produit dans la vue mobile sur Chrome :</a> Le correctif ACSD-58790 corrige le problème Adobe Commerce où l’image dans la vue mobile sur Chrome n’effectuait pas de zoom avant sur l’image comme prévu. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442 : corrige le problème où les appareils avec une largeur de 768px sont traités comme mobiles, ce qui entraînait le chargement du menu et de l’en-tête dans la vue mobile pas du bureau :</a> Le correctif ACSD-5842 corrige le problème Adobe Commerce où les appareils avec une largeur de 768px sont traités comme mobiles, ce qui entraîne le chargement du menu et de l’en-en-tête dans une vue mobile. un bureau. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.50 est installé.
    </td>
    <td>Nouvel article </td>
    <td>17 octobre 2024</td>
  </tr>
</table>
