---
title: '''ACSD-47669 : Erreur interne du serveur lors de l''import de produits avec des options personnalisables'''
description: Appliquez le correctif ACSD-47669 pour résoudre le problème Adobe Commerce en raison duquel une erreur de serveur interne se produit lors de l’importation de produits avec des options personnalisables.
feature: Products
role: Admin, Developer
exl-id: 14afbd71-075a-4264-8da2-dbbd93f472a1
source-git-commit: 66e56b9ba31fd2c5d3f8a330f09d8e94df77b17d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47669 : Erreur interne du serveur lors de l&#39;import de produits avec des options personnalisables

Le correctif ACSD-47669 corrige le problème en raison duquel une erreur de serveur interne se produisait lors des importations de produits avec des options personnalisables. Ce correctif est disponible lorsque la variable [!DNL Quality Patches Tool (QPT)] La version 1.1.38 est installée. L’ID de correctif est ACSD-47669. Veuillez noter que le problème a déjà été corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Une erreur de serveur interne s’est produite lors de l’import de produits avec des options personnalisables.

<u>Étapes à reproduire</u>:

1. Créez une vue de magasin supplémentaire. Assurez-vous que vous avez 2 vues de magasin, par exemple en, Royaume-Uni.
1. Créez deux produits simples, par exemple prod1 et prod2.
1. Préparez un fichier csv qui ajoute des options personnalisées pour les produits dans chaque vue de magasin et pour le **Toutes les vues de magasin** portée. Importez ce fichier csv.
1. Préparez un autre fichier csv contenant deux enregistrements. Le premier enregistrement doit être de mettre à jour les options personnalisées de &quot;prod1&quot; spécifiquement pour la portée de la vue de magasin britannique et le second enregistrement doit être de mettre à jour les options personnalisées de &quot;prod2&quot; pour la variable **Toutes les vues de magasin** portée. Importez ce second fichier csv.

<u>Résultats attendus</u>:

Vous devriez être en mesure de personnaliser les options sans erreur.

<u>Résultats réels</u>:

Une erreur de violation de contrainte d’intégrité se produit.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
