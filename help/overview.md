---
title: Base de connaissances du support Adobe Commerce
description: Tout ce que vous devez savoir pour résoudre les problèmes et gérer votre boutique Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 95509b717d41436b68ad94c3c28ac72e1887fdfc
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 1%

---

# Base de connaissances du support Adobe Commerce

![Page d’accueil de la base de connaissances](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Les informations contenues dans cette base de connaissances sont conçues comme complémentaires à [Documentation destinée aux développeurs Adobe Commerce](https://developer.adobe.com/commerce/docs), et [Guide du marchand Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html), ainsi que d’autres publications Adobe Commerce. Il couvre le dépannage et les bonnes pratiques, héberge des annonces, répond aux questions fréquentes et met en évidence des scénarios spécifiques qui n’ont pas été mentionnés (pour une raison quelconque) dans la documentation officielle.

## Qu&#39;y a-t-il dans la base de connaissances ?

| CATÉGORIE | DESCRIPTION |
| --- | --- |
| [Outils d’assistance](/help/support-tools/overview.md) | Améliorez votre expérience de la boutique en ligne grâce aux différents outils d’assistance proposés par Adobe Commerce. Nous fournissons des bonnes pratiques personnalisées, des outils de diagnostic et de surveillance, ainsi que les informations les plus pertinentes sur votre site. |
| [Annonces](/help/announcements/overview.md) | Obtenez des mises à jour importantes de la part des équipes Adobe Commerce. |
| [Dépannage](/help/troubleshooting/overview.md) | Procurez-vous des solutions et correctifs en libre-service auprès de l’équipe d’assistance d’Adobe Commerce. |
| [Guide de l’utilisateur du centre d’aide](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Découvrez comment gérer vos tickets d’assistance, accorder un accès partagé et parcourir efficacement la base de connaissances. |
| [Procédures](/help/how-to/overview.md) | Suivez les instructions détaillées de l’équipe d’assistance d’Adobe Commerce. |
| [FAQ](/help/faq/overview.md) | Découvrez les questions fréquentes sur les stratégies, les stratégies et les détails d’Adobe Commerce concernant les fonctionnalités d’Adobe Commerce. |

>[!NOTE]
>
>Pour déposer un nouveau ticket, connectez-vous à [Centre d’aide Adobe Commerce](https://support.magento.com/) et suivez les étapes présentées dans la section [Envoyer un ticket d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
>
>Si vous ne voyez pas l’option permettant d’envoyer un ticket, reportez-vous au *[Envoi d’un lien de ticket non affiché](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* dans notre section [Guide de l’utilisateur du centre d’aide](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## Nouveautés

<table style="width:100%">
  <tr>
    <th style="width:70%">Description</th>
    <th style="width:15%">Type</th>
    <th style="width:15%">Date</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-update-the-cloud-account-profile">Comment mettre à jour le profil du compte cloud :</a> Cet article décrit les étapes à suivre pour modifier le profil sur le compte cloud.
    </td>
    <td>Nouvel article</td>
    <td>22 avril 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/admin-create-order-page-in-csp-restricted-mode">Dépannage de la création d’une page de commande en mode restreint CSP :</a> Cet article fournit des explications et des correctifs pour les problèmes d’Adobe Commerce 2.4.7 lors de la création d’une commande côté administrateur lorsque le mode restreint CSP est <em>Activé</em>.  
    </td>
    <td>Nouvel article</td>
    <td>22 avril 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/storefront-checkout-page-in-csp-restricted-mode">Dépannage de la page de passage en caisse du storefront en mode restreint CSP :</a> Cet article fournit des explications et des correctifs pour les problèmes d’Adobe Commerce 2.4.7 lors de l’affichage de la page de passage en caisse en mode CSP restreint, avec la variable <em>"Refusé d’exécuter un script intégré, car il enfreint la directive suivante de la politique de sécurité du contenu : "script-src ..."</em> message d’erreur dans le journal de la console du navigateur. 
    </td>
    <td>Nouvel article </td>
    <td>22 avril 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-54656-invisible-recaptcha-fails-during-checkout-preventing-order-placement">ACSD-54656 : l’invisibilité de reCAPTCHA ne fonctionne pas pendant le passage en caisse empêchant le placement de la commande :</a> Le correctif ACSD-54656 corrige le problème lorsque le reCAPTCHA invisible ne fonctionne pas correctement lors du passage en caisse, ce qui empêche le placement d’une commande. Ce correctif est disponible lorsque la variable <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> La version 1.1.46 est installée. 
    </td>
    <td>Nouvel article </td>
    <td>22 avril 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-46767-category-page-caches-invalidate-when-the-stock-quantity-changes">ACSD-46767 : Les caches de page de catégorie sont invalidés lorsque la quantité de stock change :</a> Le correctif ACSD-46767 corrige le problème de mise en cache de la page Catégorie lorsque la quantité de stock change, même si le produit est toujours en stock. Ce correctif est disponible lorsque la variable <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> La version 1.1.46 est installée.  
    </td>
    <td>Nouvel article </td>
    <td>22 avril 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-45/acsd-56415-performance-of-partial-price-indexing-is-slowed-down-due-to-a-delete-query">ACSD-56415 : les performances de l’indexation de prix partielle sont ralenties en raison de la requête du DELETE :</a> Le correctif ACSD-56415 corrige le problème de ralentissement des performances de l’indexation de prix partielle en raison d’une requête DELETE lorsque la base de données contient un grand nombre d’index de données de prix partiels. Ce correctif est disponible lorsque la variable <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> La version 1.1.45 est installée.  
    </td>
    <td>Nouvel article </td>
    <td>22 avril 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56858-role-permissions-display-issue-in-b2b-company-admin-panel">ACSD-56858 : incohérence des autorisations de rôle dans l’administration de la société B2B :</a> Le correctif ACSD-56858 corrige le problème en raison duquel les autorisations de rôle s’affichent incorrectement pour un administrateur de société restreint dans l’environnement B2B. Ce correctif est disponible lorsque la variable <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> La version 1.1.47 est installée. 
    </td>
    <td>Nouvel article </td>
    <td>22 avril 2024</td>
 </tr>
</table>

## Articles populaires

* [Transformation en OpenSearch pour Adobe Commerce sur Cloud 2.4.4](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Vulnérabilité d’Apache log4j2 dans Adobe Commerce](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [Mises à jour de sécurité disponibles pour Adobe Commerce APSB22-12](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [Identifier et mesurer les pannes d’Adobe Commerce sur l’infrastructure cloud](/help/how-to/general/how-to-identify-outages.md)
* [Affichage du niveau vCPU de l’environnement dans votre grappe sur Adobe Commerce](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [Adobe Commerce sur l’infrastructure cloud : calcul de l’allocation du processeur](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [Adobe Commerce sur l’infrastructure cloud : vérifiez la configuration du processeur de l’hôte.](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
