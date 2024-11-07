---
title: 'MDVA-39713 : l’utilisateur peut modifier l’heure de début de la mise à jour planifiée active'
description: Le correctif MDVA-39713 corrige le problème lorsqu’un utilisateur est en mesure de modifier l’heure de début d’une mise à jour planifiée active. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-39713. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713 : l’utilisateur peut modifier l’heure de début de la mise à jour planifiée active

Le correctif MDVA-39713 corrige le problème lorsqu’un utilisateur est en mesure de modifier l’heure de début d’une mise à jour planifiée active. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 est installé. L’ID de correctif est MDVA-39713. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.3.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur peut modifier l’heure de début d’une mise à jour planifiée active.

<u>Étapes à reproduire</u> :

1. Créez de nouvelles pages CMS.
1. Sélectionnez **Planifier une nouvelle mise à jour** et définissez la **Date de début** sur la valeur actuelle de +1 minute.
1. Activez la Mise à jour planifiée en exécutant la commande `bin/magento cron:run --group=staging` dans un environnement local. Patientez quelques minutes et vérifiez si le planning est actif.
1. Une fois que la planification est active, actualisez la page.
1. Cliquez sur **Afficher/Modifier** dans la section Modifications planifiées .
1. Modifiez l’heure en ajoutant +2 minutes et enregistrez la modification.
1. Enregistrez la page CMS.
1. Exécutez à nouveau la commande suivante : `bin/magento cron:run --group=staging`.
1. Cliquez sur **Afficher/Modifier** de la mise à jour planifiée.

<u>Résultats attendus</u> :

L’utilisateur ne peut pas modifier l’heure de début d’une mise à jour planifiée active.

<u>Résultats réels</u> :

L&#39;utilisateur obtient une erreur du type *Item (Magento\Cms\Model\Page) avec le même ID &quot;11&quot; existe déjà.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
