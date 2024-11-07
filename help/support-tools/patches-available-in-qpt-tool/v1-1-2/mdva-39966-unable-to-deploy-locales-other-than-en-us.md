---
title: 'MDVA-39966 : impossible de déployer des paramètres régionaux autres que en_US'
description: Le correctif MDVA-39966 résout le problème où l’utilisateur ne peut pas déployer de paramètres régionaux autres que en_US. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-39966. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.1.
exl-id: fc0f5ef4-f6be-4f0d-af8d-803b411510a9
feature: Deploy
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# MDVA-39966 : impossible de déployer des paramètres régionaux autres que en_US

Le correctif MDVA-39966 résout le problème où l’utilisateur ne peut pas déployer de paramètres régionaux autres que en_US. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 est installé. L’ID de correctif est MDVA-39966. Veuillez noter que le problème a été corrigé dans Adobe Commerce version 2.4.1.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Impossible de déployer des paramètres régionaux autres que en_US.

<u>Étapes à reproduire</u> :

1. Configurez deux vues de magasin avec des paramètres régionaux différents, par exemple : en_US et de_DE.
1. Essayez de déployer du contenu statique pour ces paramètres régionaux en exécutant la commande suivante :

```bash
bin/magento setup:static-content:deploy --language=en_US
bin/magento setup:static-content:deploy --language=de_DE
```

<u>Résultats attendus</u> :

Le paramètre régional de de_DE est déployé.

```bash
bin/magento setup:static-content:deploy --language=de_DE

Deploy using quick strategy
adminhtml/Magento/backend/de_DE         2416/2416           ============================ 100%   9 secs
frontend/Magento/blank/de_DE            2486/2486           ============================ 100%   7 secs
frontend/Magento/luma/de_DE             2504/2504           ============================ 100%   8 secs

Execution time: 27.062166929245
```

<u>Résultats réels</u> :

paramètre régional en_US déployé au lieu de de_DE :

```bash
bin/magento setup:static-content:deploy --language=de_DE

Deploy using quick strategy
adminhtml/Magento/backend/en_US         2416/2416           ============================ 100%   2 secs
frontend/Magento/blank/en_US            2486/2486           ============================ 100%   1 sec
frontend/Magento/luma/en_US             2504/2504           ============================ 100%   2 secs
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
