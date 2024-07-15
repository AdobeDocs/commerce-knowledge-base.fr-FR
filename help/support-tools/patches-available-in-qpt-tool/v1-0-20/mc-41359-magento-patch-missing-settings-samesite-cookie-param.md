---
title: 'Correctif commercial MC-41359 : paramètres manquants Paramètre de cookie SameSite'
description: Le correctif commercial MC-41359 corrige le problème lié aux paramètres de cookie SameSite manquants. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 est installé. L’ID de correctif est MC-41359. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Correctif commercial MC-41359 : paramètres manquants Paramètre de cookie SameSite

Le correctif commercial MC-41359 corrige le problème lié aux paramètres de cookie SameSite manquants. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 est installé. L’ID de correctif est MC-41359. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.3.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :** Adobe Commerce sur l’infrastructure cloud 2.4.2

**Compatible avec les versions d’Adobe Commerce :** Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Paramètres manquants du paramètre de cookie SameSite.

<u>Étapes à reproduire :</u>

Conditions préalables :

* Ouvrez Chrome et accédez à chrome://flags/
* Activez les **cookies samesite par défaut** et les **cookies sans samesite doivent être sécurisés**.
* Ouvrez l’Inspecteur Chrome.

<u>Scénario 1 : </u>

1. Activez PayPal.
1. Allez au devant du magasin.
1. Ajoutez un produit au panier.
1. Allez à la caisse.

<u>Scénario 2 : </u>

Si New Relic [est activé](https://docs.magento.com/user-guide/reports/new-relic-reporting.html), l’avertissement s’affiche sur n’importe quelle page frontale.

<u>Résultat réel :</u>

Message d&#39;avertissement dans la console du navigateur : *Un cookie associé à une ressource intersite a été défini sans attribut SameSite.*

<u>Résultat attendu :</u>

&quot;lax&quot; ne doit pas être ajouté au domaine du cookie ; l’attribut samesite doit être présent avec la valeur par défaut.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquez les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Pour plus d’informations sur les autres correctifs disponibles dans l’outil QPT, reportez-vous à la section [Correctifs disponibles dans l’outil QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) de notre documentation destinée aux développeurs.
