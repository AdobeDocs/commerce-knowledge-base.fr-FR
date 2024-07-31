---
title: Base de connaissances du support Adobe Commerce
description: Tout ce que vous devez savoir pour résoudre les problèmes et gérer votre boutique Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 738a5455267647d294d222d5bb6149254dcb93dd
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 0%

---

# Base de connaissances du support Adobe Commerce

![Page d’accueil de la base de connaissances](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Les informations de cette base de connaissances sont conçues comme complémentaires à la [documentation du développeur Adobe Commerce](https://developer.adobe.com/commerce/docs), au [Guide du marchand Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) et à d’autres publications Adobe Commerce. Il couvre le dépannage et les bonnes pratiques, héberge des annonces, répond aux questions fréquentes et met en évidence des scénarios spécifiques qui n’ont pas été mentionnés (pour une raison quelconque) dans la documentation officielle.

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
>Pour déposer un nouveau ticket, connectez-vous au [Centre d’aide Adobe Commerce](https://support.magento.com/) et suivez les étapes détaillées sous [Envoyer un ticket d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
>
>Si vous ne voyez pas l’option permettant d’envoyer un ticket, reportez-vous à la section *[Submit a ticket link not displayed](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* de notre [Guide de l’utilisateur du centre d’aide](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## Nouveautés

<table style="width:100%">
  <tr>
    <th style="width:70%">Description</th>
    <th style="width:15%">Type</th>
    <th style="width:15%">Date</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/the-magento-cloud-cli-doesnt-show-an-active-environment">L’interface de ligne de commande <code>Magento-cloud</code> n’affiche pas d’environnement actif : </a> Il existe plusieurs environnements actifs et vous tentez d’interagir avec un environnement en exécutant une commande d’interface de ligne de commande Magento-cloud. Toutefois, l’invite permettant de choisir l’environnement souhaité ne répertorie pas cet environnement.
    </td>
    <td>Nouvel article</td>
    <td>30 juillet 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches">Comment obtenir et appliquer un correctif de sécurité :</a> Cet article fournit des instructions sur la manière d’obtenir et d’appliquer un correctif de sécurité qui a été publié, mais les instructions ne sont pas disponibles.  
    </td>
    <td>Nouvel article</td>
    <td>30 juillet 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/falling-back-to-elasticsearch7-when-search-engine-set-to-opensearch">Revenir à Elasticsearch7 lorsque le moteur de recherche est défini sur OpenSearch :</a> Cet article fournit une solution au problème qui se produit lorsqu’une erreur Revenir à Elasticsearch7 se produit lorsque le moteur de recherche est défini sur OpenSearch dans Adobe Commerce. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-there-are-no-commands-defined-in-the-cache-namespace-error">Échec du déploiement : aucune commande n’est définie dans l’erreur d’espace de noms 'cache' :</a> Cet article fournit une solution au problème lorsque votre déploiement échoue et l’une des erreurs affichées dans le journal est <em>Aucune commande n’est définie dans l’espace de noms "cache"</em>. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-55566-mergecart-mutation-fails-with-an-internal-server-error-in-graphql-response">ACSD-55566 : <code>mergeCart</code> Échec de la mutation avec une erreur de serveur interne dans la réponse GraphQL :</a> Le correctif ACSD-55566 corrige le problème où la mutation <code>mergeCart</code> échoue avec une erreur de serveur interne dans la réponse GraphQL. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé.  
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56546-configurable-and-bundle-products-display-as-out-of-stock-on-the-storefront">ACSD-56546 : les produits configurables et groupés s’affichent en rupture de stock sur le storefront :</a> Le correctif ACSD-56546 corrige le problème où les produits configurables et groupés s’affichent en rupture de stock sur le storefront. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé.  
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57565-the-order-dashboard-displays-incorrect-order-information">ACSD-57565 : le tableau de bord des commandes affiche des informations de commande incorrectes :</a> Le correctif ACSD-57565 corrige le problème en raison duquel le tableau de bord des commandes affiche des informations de commande incorrectes jusqu’à ce que la période soit mise à jour. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57394-incorrect-product-sorting-by-multiple-sort-fields-in-graphql">ACSD-57394 : Tri incorrect des produits selon plusieurs attributs de tri dans GraphQL :</a> Le correctif ACSD-57394 corrige le problème de tri incorrect des produits lors de l’utilisation de plusieurs attributs de tri dans GraphQL. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57854-graphql-response-contains-disabled-categories-that-should-not-be-listed-in-the-category-aggregations">ACSD-57854 : La réponse GraphQL contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories :</a> Le correctif ACSD-57854 corrige le problème où la réponse GraphQL contient des catégories désactivées qui ne doivent pas être répertoriées dans les agrégations de catégories. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-57074-yes-no-custom-attribute-does-not-work-with-indexing">ACSD-57074 : Oui/Non attribut personnalisé avec le préfixe <code>price_*</code> dans l’attribut <code>attribute_code</code> ne fonctionne pas avec l’indexation : </a> Le correctif ACSD-57074 corrige le problème où l’attribut personnalisé <em>Oui/Non</em> avec le préfixe <code>price_*</code> dans l’attribut <code>attribute_code</code> ne fonctionne pas avec l’indexation. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-55241-used-and-times-used-attributes-display-incorrect-values-for-generated-coupons">ACSD-55241 : Used and Times Used attributes affichent des valeurs incorrectes pour les bons générés :</a> Le correctif ACSD-55241 corrige le problème en raison duquel les attributs Utilisés et Temps utilisé affichent des valeurs incorrectes pour les bons générés. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56760-admin-user-is-restricted-to-a-specific-website-and-is-unable-to-sort-or-add-new-products">ACSD-56760 : L’utilisateur administrateur est limité à un site web spécifique et ne peut pas trier ou ajouter de nouveaux produits :</a> Le correctif ACSD-56760 corrige le problème où l’utilisateur administrateur, qui est limité à un site web spécifique, ne peut pas trier ou ajouter de nouveaux produits dans une catégorie au cas où le magasin web possède sa propre catégorie racine. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56635-imported-customers-are-duplicated-with-the-same-email-address">ACSD-56635 : Les clients importés sont dupliqués avec la même adresse électronique lors du partage du compte défini sur Global :</a> Le correctif ACSD-56635 corrige le problème en raison duquel le client importé est dupliqué avec la même adresse électronique lorsque l’importation est utilisée avec le partage de compte défini sur Global. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57315-new-transaction-created-in-paypal-payflow-pro-each-time-the-fetch-button-is-clicked">ACSD-57315 : Une nouvelle transaction est créée dans PayPal Payflow Pro à chaque clic sur le bouton de récupération :</a> Le correctif ACSD-57315 corrige le problème de création d’une transaction dans PayPal Payflow Pro chaque fois que l’utilisateur clique sur le bouton de récupération dans l’écran d’affichage des transactions dans l’administrateur. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56741-database-setup-upgrade-error-with-custom-mysql-trigger">ACSD-56741 : résolution des erreurs de configuration de la base de données avec les déclencheurs MySQL personnalisés :</a> Le correctif ACSD-56741 corrige le problème où un message d’erreur <em> Tentative d’accès au décalage de tableau sur la valeur de type null</em> s’affiche pendant <code>setup:upgrade</code> en raison d’un déclencheur MySQL personnalisé dans la base de base de données sans rapport avec l’indexation et de tableau. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-58008-editing-the-end-date-as-empty-causes-the-schedule-update-to-disappear">ACSD-58008 : La modification de la date de fin comme vide entraîne la disparition de la mise à jour du planning :</a> Le correctif ACSD-58008 corrige le problème en raison duquel la modification de la date de fin comme vide provoquait la disparition de la mise à jour du planning. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57337-admin-user-with-access-restrictions-can-see-companies">ACSD-57337 : Un utilisateur administrateur avec des restrictions d’accès peut afficher toutes les entreprises dans la grille Entreprises :</a> Le correctif ACSD-57337 corrige le problème lorsqu’un utilisateur administrateur avec des restrictions d’accès à des sites web spécifiques pouvait afficher les entreprises de tous les sites web dans la grille Entreprises. Ce correctif est disponible lorsque <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48 est installé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-with-correct-access-key-env-composer-auth">Le déploiement échoue avec les clés d’accès correctes dans <code>env:COMPOSER_AUTH</code> ou <code>auth.json</code> : </a> Cet article fournit une solution au problème lorsque votre déploiement échoue avec une erreur telle que celle du journal de déploiement. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-bypass-waf-for-graphql-requests">Comment contourner WAF pour les requêtes GraphQL :</a> Cet article explique comment contourner les requêtes WAF pour les requêtes GraphQL lorsque le WAF rapide bloque vos requêtes GraphQL. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/email-stating-that-export-storage-is-almost-full">Courrier électronique indiquant que le stockage des exportations est presque saturé :</a> Cet article fournit une solution au problème où vous recevez un courrier électronique indiquant que le stockage des exportations est presque saturé. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-4-to-10-5-for-magento-commerce-cloud">Mise à niveau de MariaDB 10.4 vers 10.5 pour Adobe Commerce sur le cloud :</a> Cet article explique comment effectuer la mise à niveau de MariaDB 10.4 vers 10.5 pour continuer à utiliser Adobe Commerce sur l’infrastructure cloud. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/revised-patches-for-google-maps-access-loss-on-all-adobe-commerce-versions">Correctifs modifiés pour les pertes d’accès Google Maps sur toutes les versions d’Adobe Commerce : </a> Cet article fournit un correctif pour les marchands Adobe Commerce qui ne sont pas compatibles avec les versions récentes de Google Maps à partir de 3.54+. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102">Mise à jour de sécurité disponible pour Adobe Commerce - APSB24-40:</a> Cet article partage une mise à jour relative à CVE-2024-34102. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/poor-performance-in-integration-environments"> Mauvaises performances dans les environnements d’intégration : </a> Cet article fournit une solution au problème où les environnements d’intégration Pro et les environnements d’évaluation Starter sont peu performants. 
    </td>
    <td>Nouvel article </td>
    <td>30 juillet 2024</td>
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
