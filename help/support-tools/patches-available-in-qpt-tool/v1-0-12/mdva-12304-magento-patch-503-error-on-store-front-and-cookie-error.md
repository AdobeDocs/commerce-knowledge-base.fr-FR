---
title: 'MDVA-12304 : erreur 503 sur l’interface du magasin et erreur du cookie'
description: Ce correctif Adobe Commerce MDVA-12304 résout les erreurs 503 sur les fronts de la boutique, avec *Impossible d’envoyer le cookie. Le nombre maximum de cookies sera dépassé.* message d’erreur dans les journaux. Il s’agit d’un problème connu d’Adobe Commerce 2.2.5. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 est installé.
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304 : Erreur 503 sur l’interface du magasin et erreur du cookie

Ce correctif Adobe Commerce MDVA-12304 résout les erreurs 503 sur les fronts des magasins, avec *Impossible d’envoyer le cookie. Le nombre maximum de cookies sera dépassé.* message d’erreur dans les journaux. Il s’agit d’un problème connu d’Adobe Commerce 2.2.5. Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.0.12 est installée.

## Produits et versions concernés

* **Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur site 2.2.5.
* **Compatible avec les versions d’Adobe Commerce :** Adobe Commerce (toutes les méthodes de déploiement) 2.x.x.

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les clients reçoivent une erreur 503 lorsqu’ils naviguent au front du magasin. Dans le `var/log/exception.log` Le fichier contient le message d’erreur suivant *Impossible d’envoyer le cookie. Le nombre maximum de cookies sera dépassé.*

Le problème se produit car la limite des cookies par défaut d’Adobe Commerce est définie sur 50. Si le navigateur du client atteint la limite, Commerce renvoie une exception. La solution fournie dans le correctif augmente la limite du cookie à 200.

<u>Étapes à reproduire :</u>

L’erreur 503 peut s’afficher à tout moment lorsque le client tente de se connecter et d’afficher son panier.

Dans le `var/log/exception.log` Le fichier contient le message d’erreur suivant *Impossible d’envoyer le cookie. Le nombre maximum de cookies sera dépassé.*

<u>Résultat réel :</u> Le client ne peut pas vérifier son panier ni terminer sa commande.

<u>Résultat attendu :</u> Le client peut vérifier son panier et terminer sa commande.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.


## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
