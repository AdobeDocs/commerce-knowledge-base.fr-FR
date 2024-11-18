---
title: Base de connaissances du support Adobe Commerce
description: Tout ce que vous devez savoir pour résoudre les problèmes et gérer votre boutique Commerce.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 52d07e5a5bb7be492f6799d0e5ad9fd49c3a61ae
workflow-type: tm+mt
source-wordcount: '1074'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25234">Transfert de licence en raison d’une restructuration :</a> Cet article vous aidera à faciliter la transition de la propriété de votre compte Adobe Commerce, y compris toutes les étapes essentielles pour que vos services fonctionnent sans problème.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25289">Mises à jour de sécurité disponibles pour Adobe Commerce (APSB24-90) :</a> Le 12 novembre 2024, Adobe a publié une mise à jour de sécurité pour les fonctionnalités Adobe Commerce (sur le cloud et sur site) et Magento Open Sources optimisées par les services Commerce et déployées en tant que SaaS (Software as a Service). Cette mise à jour corrige une vulnérabilité <a href="https://helpx.adobe.com/security/severity-ratings.html">critical</a> . 
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25231">Le propriétaire du compte MageID ne peut pas se connecter et envoyer un ticket d’assistance :</a> Cet article traite du problème Adobe Commerce en raison duquel vous ne pouvez pas vous connecter à votre compte (MageID) à l’adresse account.magento.com pour envoyer un ticket d’assistance.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25135">L’extension de Braintree prête à l’emploi pour Adobe Commerce ne prend pas en charge les derniers champs Visa 3DS :</a> Cet article explique comment se conformer aux nouvelles réglementations Visa, puisque l’extension de Braintree prête à l’emploi Adobe Commerce ne prend pas en charge les derniers champs Visa 3DS.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61528-retrieving-roles-using-graphql-returns-no-results">ACSD-61528 : La récupération des rôles à l’aide de GraphQL ne renvoie aucun résultat :</a> Le correctif ACSD-61528 corrige le problème en raison duquel la récupération des rôles de l’administrateur de la société à l’aide de GraphQL renvoie toujours un résultat nul. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.53 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-48318-environment-emulation-nesting-error-in-system-log">ACSD-48318 : Erreur d’imbrication de l’émulation de l’environnement dans system.log :</a> Le correctif ACSD-48318 corrige le problème où un message d’erreur <em>main.ERROR:Environment imbrique n’est pas autorisé</em> apparaît dans <code>system.log</code> chaque fois qu’un email de facture est envoyé. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.53 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59366-delete-teams-with-deactivated-users-not-visible-in-the-team-list"> ACSD-59366 : Suppression d’équipes dont les utilisateurs désactivés ne sont pas visibles dans la liste des équipes : </a> Le correctif ACSD-59366 corrige le problème d’erreur qui se produit lorsque vous tentez de supprimer une équipe contenant des utilisateurs désactivés qui ne sont pas visibles dans la liste des équipes. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60234-paypal-shows-an-incorrect-amount-when-discount-is-applied">ACSD-60234 : PayPal affiche un montant incorrect lors de l’application de la remise :</a> Le correctif ACSD-60234 corrige le problème où [!DNL PayPal] affiche un montant incorrect lorsque la remise est appliquée par le biais du mode de paiement. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60673-cart-price-rule-fix-for-multiple-payment-methods-at-checkout">ACSD-60673 : problème de règle de prix du panier résolu pour plusieurs méthodes de paiement lors du passage en caisse :</a> Le correctif ACSD-60673 corrige le problème où les remises d'un [!UICONTROL Cart Price Rule] qui utilise une condition de mode de paiement ne sont pas toujours répertoriées dans les totaux. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60584-access-token-created-for-one-website-is-allowed-to-access-information-on-other-websites">ACSD-60584 : Le jeton d’accès créé pour un site web est autorisé à accéder aux informations sur d’autres sites web :</a> Le correctif ACSD-60584 corrige le problème en raison duquel le jeton d’accès créé pour l’utilisateur sur un site web est autorisé à accéder aux informations du client ou à les modifier sur d’autres sites web. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.53 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60788-fixes-issue-where-custom-scripts-for-google-tag-manager-are-not-executed-due-to-content-security-policy-errors">ACSD-60788 : les scripts personnalisés pour le Gestionnaire de balises de Google ne sont pas exécutés en raison d’erreurs de stratégie de sécurité du contenu :</a> Le correctif ACSD-60788 corrige le problème en raison duquel les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs de stratégie de sécurité du contenu. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61366-setup-command-fails-with-error">ACSD-61366 : la commande <code>bin/magento setup:static-content:deploy --jobs 4</code> rencontre plusieurs échecs de tâche avec une erreur :</a> Le correctif ACSD-61366 corrige le problème où la commande <code>bin/magento setup:static-content:deploy --jobs 4</code> rencontre plusieurs échecs de tâche avec le <em>port doit être configuré dans l’erreur du paramètre d’hôte</em>, malgré la spécification du port pour la connexion DB. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60816-newrelic-browser-monitoring-scripts-injected-by-apm-agent-are-not-compliant-with-csp">ACSD-60816 : les scripts de surveillance du navigateur New Relic injectés par l’agent APM ne sont pas conformes à la CSP :</a> Le correctif ACSD-60816 corrige le problème en raison duquel les [!DNL New Relic] scripts de surveillance du navigateur injectés par l’agent APM ne sont pas conformes à la stratégie de sécurité du contenu (CSP). Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59952-error-on-deleting-shared-catalog-with-same-group-id-as-another-shared-catalog">ACSD-59952 : erreur lors de la suppression d’un catalogue partagé avec le même ID de groupe qu’un autre catalogue partagé :</a> Le correctif ACSD-59952 corrige l’erreur générée lors de la suppression de catalogues partagés avec le même <code>customer_group_id</code> qu’un autre catalogue partagé. Elle empêche en outre les utilisateurs de créer de tels catalogues partagés. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.52 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59786-graphql-returns-an-error-when-fetching-a-quote-id-for-an-expired-quote">ACSD-59786 : GraphQL renvoie une erreur lors de la récupération d’un <code>quote_id</code> pour un guillemet expiré :</a> Le correctif ACSD-59786 corrige le problème où une requête GraphQL renvoie une erreur lors de la récupération d’un <code>quote_id</code> pour un guillemet expiré. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59967-javascript-error-prevents-google-maps-from-rendering-correctly">ACSD-59967 : l’erreur JavaScript empêche le rendu correct des cartes Google :</a> Le correctif ACSD-59967 corrige le problème où l’erreur JavaScript empêche [!DNL Google Maps] de procéder correctement au rendu. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.51 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-59930-improves-performance-of-company-flows">ACSD-59930 : améliore les performances des flux de l’entreprise :</a> Le correctif ACSD-59930 corrige le problème qui entraînait l’affichage d’une erreur <em>Timeout</em> dans le panneau d’administration lors de la création, de l’enregistrement ou de la suppression d’une entreprise ayant un administrateur comportant plus de 1 0000000000000 adresses. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.53 est installé.
    </td>
    <td>Nouvel article </td>
    <td>vendredi 14 novembre 2024</td>
  </tr>
</table>
