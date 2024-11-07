---
title: '"MDVA-42509 : le fichier CSV n’a pas pu être chargé dans un ordre rapide, ce qui a pour conséquence l’erreur "Impossible d’envoyer le cookie""'
description: Le correctif MDVA-42509 résout le problème en raison duquel un fichier CSV n’a pas pu être chargé dans un ordre rapide. L’erreur *Impossible d’envoyer le cookie* s’affiche. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-42509. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 7aa0e710-9a28-4531-b9cb-c82f654487f4
feature: B2B, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-42509 : le fichier CSV n’a pas pu être téléchargé dans un ordre rapide, ce qui a pour conséquence l’erreur &quot;Impossible d’envoyer le cookie&quot;.

Le correctif MDVA-42509 résout le problème où un fichier CSV n’a pas pu être chargé dans un ordre rapide, ce qui entraîne l’erreur *Impossible d’envoyer le cookie*. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 est installé. L’ID de correctif est MDVA-42509. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La création d’une commande rapide avec un grand nombre de produits à l’aide d’un fichier CSV affiche une erreur de cookie : *Impossible d’envoyer le cookie*

<u>Étapes à reproduire</u> :

1. Activez l’ordre rapide en accédant à **Magasins** > **Paramètres** > **Configurations** > **Général** > **Fonctionnalités B2B**.
1. Créez un compte client et accédez à **Commande rapide** à l’aide du lien supérieur.
1. Essayez de créer un ordre rapide à l’aide d’un fichier CSV contenant plus de 100 SKU.

<u>Résultats attendus</u> :

Vous pouvez créer un ordre rapide avec de nombreux SKU.

<u>Résultats réels</u> :

Un message d’erreur s’affiche en rapport avec la taille du cookie.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
