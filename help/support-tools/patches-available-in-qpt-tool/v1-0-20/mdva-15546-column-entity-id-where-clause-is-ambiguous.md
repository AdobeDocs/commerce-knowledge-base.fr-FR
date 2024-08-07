---
title: "MDVA-15546 : Colonne 'entity_id' où la clause est ambiguë"
description: "Le correctif MDVA-15546 résout des problèmes de performances pouvant être liés à certaines extensions d’Amazon. Ce problème est indiqué par l’erreur suivante dans les journaux d’exception : *where*   *Colonne 'entity\_id' dans laquelle la clause est ambiguë, la requête était : SELECT \\`main\_table\\`.\\*, \\`extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\`. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 est installé. L’ID de correctif est MDVA-15546."
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546 : colonne &quot;entity_id&quot; où la clause est ambiguë

Le correctif MDVA-15546 résout des problèmes de performances pouvant être liés à certaines extensions d’Amazon. Ce problème est indiqué par l’erreur suivante dans les journaux d’exception : *where*   *Colonne &#39;entity\_id&#39; dans laquelle la clause est ambiguë, la requête était : SELECT \`main\_table\.\*, \`extension\_attribute\_amazon\_order\_reference\_id* \`. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 est installé. L’ID de correctif est MDVA-15546.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.2.5

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.0 - 2.4.2

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Problèmes de performances pouvant être liés à certaines extensions Amazon.

<u>Conditions préalables</u> :

Nettoyez Adobe Commerce avec B2B et Amazon\_payment.

<u>Étapes à reproduire</u> :

1. Accédez à la page de vitrine.
1. Ajoutez un produit au panier.
1. Attendez ou déclenchez la tâche cron `flush_preview_quotas`.

<u>Résultat réel</u> :

Lorsque vous cochez `var/log/exception/log`, l’erreur suivante s’affiche :

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `main_table`.*, `extension_attribute_amazon_order_reference_id`.`amazon_order_reference_id` AS `extension_attribute_amazon_order_reference_id_amazon_order_reference_id`, `extension_attribute_amazon_reference_id`.`quote_id_de_référence_de_l&#39;extension` AS `extension_attribute_amazon_order_reference_id_id_de_id`, `7}_attribute_amazon_order_reference_id`.` sandbox_simulation_reference` AS `extension_attribute_amazon_order_reference_sandbox_simulation_reference`, `extension_attribute_amazon_order_reference_id`.`confirm` AS `extension_attribute_amazon_order_reference_id_confirm` FROM `quote_main_table` AS `5}amazon_quote` AS `extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*` LEFT JOIN `

<u>Résultat attendu</u> :

La tâche Cron se termine sans erreur.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
