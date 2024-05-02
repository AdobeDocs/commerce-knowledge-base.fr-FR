---
title: "Correctif MDVA-32545 : les factures de commande ne sont pas envoyées automatiquement"
description: Le correctif MDVA-32545 corrige le problème en raison duquel les courriers électroniques de facture ne sont pas automatiquement envoyés au client pour les commandes passées depuis l’administrateur. Cela affecte tout mode de paiement avec le type de transaction **Sale**, comme **Braintree** ou **PayPal Payflow Pro**.
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Correctif MDVA-32545 : les factures de commande ne sont pas envoyées automatiquement

Le correctif MDVA-32545 corrige le problème en raison duquel les courriers électroniques de facture ne sont pas automatiquement envoyés au client pour les commandes passées depuis l’administrateur. Cela affecte tout mode de paiement avec la variable **Sale** type de transaction, par exemple **Braintree** ou **PayPal Payflow Pro**.

Ce correctif est disponible lorsque la variable [Outil Correctifs de qualité (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) La version 1.0.13 est installée. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.2.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud 2.3.2-p2

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce sur l’infrastructure cloud et Adobe Commerce sur site 2.3.0 - 2.4.1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

<u>Étapes à reproduire</u>:

1. Activez n’importe quel mode de paiement avec la variable **Sale** type de transaction. (Par exemple : **Braintree** ou **PayPal Payflow Pro**.)
1. Créez un produit simple.
1. Créez un compte client dans le front-end.
1. passé une commande auprès de l’administrateur.

<u>Résultats attendus</u>:

L&#39;email de la facture est automatiquement envoyé au client, comme prévu.

<u>Résultats réels</u>:

L&#39;email de la facture n&#39;est pas envoyé automatiquement au client.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://devdocs.magento.com/cloud/project/project-patch.html) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [L’outil Correctifs de qualité est disponible : un nouvel outil pour les correctifs de qualité en libre-service.](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil Correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) dans notre documentation destinée aux développeurs.
