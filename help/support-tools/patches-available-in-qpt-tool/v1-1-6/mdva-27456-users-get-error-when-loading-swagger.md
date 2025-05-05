---
title: 'MDVA-27456 : les utilisateurs reçoivent une erreur lors du chargement de Swagger'
description: Le correctif MDVA-27456 corrige le problème d’erreur des utilisateurs lorsqu’ils tentent de charger Swagger. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 est installé. L’ID de correctif est MDVA-27456. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.7.
exl-id: e331595f-a94b-4070-803a-60f559735b29
feature: Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# MDVA-27456 : les utilisateurs reçoivent une erreur lors du chargement de Swagger.

Le correctif MDVA-27456 corrige le problème d’erreur des utilisateurs lorsqu’ils tentent de charger Swagger. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6 est installé. L’ID de correctif est MDVA-27456. Veuillez noter que le problème a été corrigé dans Adobe Commerce 2.3.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.5-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs reçoivent une erreur lors du chargement de Swagger.

<u>Étapes à reproduire</u> :

Accédez à `../swagger.`

<u>Résultats attendus</u> :

Swagger se charge sans erreur.

<u>Résultats réels</u> :

Les utilisateurs reçoivent l’erreur suivante : *Échec du chargement de la définition de l’API*. Le journal des erreurs contient :

*report.CRITICAL : ID de rapport : webapi-5ea9c6da19cb1; Message : le type de paramètre &quot;\DateTime&quot; n’est pas valide. Vérifiez le paramètre et réessayez.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) .
