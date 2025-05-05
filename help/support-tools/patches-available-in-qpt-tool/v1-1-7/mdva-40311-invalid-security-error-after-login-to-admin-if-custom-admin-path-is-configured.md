---
title: 'MDVA-40311 : "Erreur de sécurité ou de clé de formulaire non valide" après connexion à Admin si le chemin d’accès d’administrateur personnalisé est configuré'
description: '''Le correctif MDVA-40311 corrige le problème où l''utilisateur administrateur reçoit un message d''erreur : *Sécurité non valide ou clé de formulaire. Actualisez la page*, après vous être connecté à l’administrateur si le chemin d’accès d’administrateur personnalisé est configuré et si la clé secrète est activée. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 est installé. L’ID de correctif est MDVA-40311. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4."'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311 : erreur &quot;Sécurité non valide ou clé de formulaire non valide&quot; après connexion à Admin si le chemin d’accès d’administrateur personnalisé est configuré

Le correctif MDVA-40311 corrige le problème où l&#39;utilisateur administrateur reçoit un message d&#39;erreur : *Sécurité non valide ou clé de formulaire non valide. Actualisez la page*, après vous être connecté à l’administrateur si le chemin d’accès d’administrateur personnalisé est configuré et si la clé secrète est activée. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7 est installé. L’ID de correctif est MDVA-40311. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L&#39;utilisateur administrateur reçoit un message d&#39;erreur : *Sécurité non valide ou clé de formulaire. Actualisez la page*, après vous être connecté à l’administrateur si le chemin d’accès d’administrateur personnalisé est configuré et si la clé secrète est activée.

<u>Étapes à reproduire</u> :

* Connectez-vous en tant qu’utilisateur administrateur à l’aide d’un nom d’utilisateur et d’un mot de passe valides.

<u>Résultats attendus</u> :

L’utilisateur peut se connecter sans message d’erreur.

<u>Résultats réels</u> :

*Sécurité ou clé de formulaire non valide. Actualisez le message d’erreur page* qui s’affiche.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) de notre documentation destinée aux développeurs.
