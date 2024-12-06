---
title: Base de connaissances du support Adobe Commerce
description: Tout ce que vous devez savoir pour résoudre les problèmes et gérer votre boutique Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 6d22ea4725249df1528625672be405464b1411e8
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 2%

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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25301">Résolvez les problèmes de l’agent [!DNL New Relic] avec la mise à niveau de PHP 8.2 vers 8.3 dans Adobe Commerce :</a> Lorsque vous effectuez une mise à niveau de PHP de la version 8.2 vers 8.3, vous pouvez constater que l’agent [!DNL New Relic] cesse de fonctionner dans votre environnement Adobe Commerce. Ce problème a été observé dans les environnements d’évaluation et de production. Dans cet article, vous trouverez des étapes de dépannage et de résolution de ce problème.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25321">[!DNL Security Scan Tool] renvoie "Mises à jour de sécurité APSByy-xx disponibles" même si le correctif est déjà appliqué : </a> Les [!DNL Security Scan Tool] indiquent les mises à jour de sécurité APSByy-xx disponibles pour Adobe Commerce et Magento Open Source même si vous avez déjà appliqué le correctif. Vous pouvez ignorer cette notification.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61845-error-occurs-for-requests-with-text-html-accept-header">ACSD-61845 : Erreur pour les requêtes avec l’en-tête d’acceptation text/html :</a> Le correctif ACSD-61845 corrige le problème lorsqu’une requête HTTP avec un en-tête d’acceptation text/html entraîne une erreur 500 en raison de non-correspondances du type de média dans la gestion des réponses. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.54 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61200-fixes-discount-tax-compensation-in-sales-total-calculations">ACSD-61200 : Incorrect discount tax compensation in sales total calculs :</a> Le correctif ACSD-61200 corrige le problème en raison duquel le montant de la compensation de la taxe sur les remises et le montant de la compensation de la taxe sur les frais de livraison sont absents des calculs Montant total et Montant total réel, ce qui entraîne des incohérences entre les données du rapport des commandes client et des coupons. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.54 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61199-cms-page-hierarchy-tab-doesnt-display-proper-tree-structure">ACSD-61199 : l’onglet [!UICONTROL Hierarchy] de la page CMS n’affiche pas la structure arborescente appropriée :</a> Le correctif ACSD-61199 corrige le problème en raison duquel l’onglet [!UICONTROL Hierarchy] de la page CMS n’affiche pas une arborescence correcte lors de la modification d’une page CMS avec une hiérarchie existante. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.54 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60804-editing-customer-linked-to-deleted-company-causes-error">ACSD-60804 : la modification d’un client associé à une société supprimée entraîne une erreur :</a> Le correctif ACSD-60804 corrige le problème où la modification d’un client associé à une société supprimée entraîne une erreur <em>Appel à une fonction membre getSuperUserId() sur null</em>. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.53 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-61522-email-in-name-fields-sends-invalid-order-confirmations">ACSD-61522 : Les adresses électroniques des champs [!UICONTROL First] et [!UICONTROL Last Name] envoient des confirmations de commande non valides : </a> Le correctif ACSD-61522 corrige le problème où il est possible de saisir des adresses électroniques dans les champs [!UICONTROL First Name] et [!UICONTROL Last Name] d’un client invité, ce qui entraîne l’envoi d’emails de confirmation de commande non valides. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.54 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-54/acsd-62485-async-operations-all-consumer-stops-working-when-company-is-created">ACSD-62485 : <code>async.operations.all</code> le consommateur cesse de fonctionner lors de la création de l’entreprise : </a> Le correctif ACSD-62485 corrige le problème où le consommateur <code>async.operations.all</code> cesse de fonctionner lorsqu’une entreprise B2B est créée. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.54 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60684-graphql-product-sorting-by-multiple-fields-does-not-work-as-expected">ACSD-60684 : Le tri des produits GraphQL par plusieurs champs ne fonctionne pas comme prévu :</a> Le correctif ACSD-60684 corrige le problème en raison duquel le tri des produits GraphQL par plusieurs champs ne fonctionne pas lorsque le tri est transmis dans les variables. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61553-cart-price-rule-discounts-are-incorrectly-calculated-when-multiple-discounts-with-different-priorities-are-applied">ACSD-61553 : [!UICONTROL Cart Price Rule] est incorrectement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées :</a> Le correctif ACSD-61553 corrige le problème où [!UICONTROL Cart Price Rule] est incorrectement calculé lorsque plusieurs remises avec des priorités différentes sont appliquées. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.53 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58383-duplicate-credit-memos-from-simultaneous-refund-requests-via-rest-api">Correctif Adobe Commerce ACSD-58383 : duplication de crédits à partir de demandes de remboursement simultanées via l’API REST :</a> Le correctif ACSD-58383 corrige le problème en raison duquel l’émission d’un remboursement via l’API REST avec deux demandes identiques exécutées simultanément, entraîne la duplication de crédits. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.55 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58471-dynamic-content-fails-load-product-detail-page">ACSD-58471 : le chargement du contenu dynamique échoue sur la page des détails du produit, lorsque les règles de prix du catalogue associées ont été planifiées :</a> Le correctif ACSD-58471 résout le problème où le contenu dynamique ne se charge pas sur la page des détails du produit, lorsque les règles de prix du catalogue associées ont été planifiées. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.55 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-58735-restricted-admin-cant-view-abandoned-shopping-carts">ACSD-58735 : L’administrateur avec accès limité ne peut pas afficher les paniers abandonnés sur le compte client pour le site web associé :</a> Le correctif ACSD-58735 corrige le problème où un utilisateur administrateur avec un rôle restreint ne peut pas afficher les paniers des clients abandonnés à partir de l’onglet <strong>[!UICONTROL Commerce Admin]</strong> &gt; <strong>[!UICONTROL Reports]</strong> &gt; <strong>[!UICONTROL Abandoned Carts]</strong> &gt; <strong>[!UICONTROL Select Cart]</strong> &gt; <strong>[!UICONTROL Shopping Cart]</strong> . Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.55 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 5 décembre 2024</td>
  </tr>
</table>
