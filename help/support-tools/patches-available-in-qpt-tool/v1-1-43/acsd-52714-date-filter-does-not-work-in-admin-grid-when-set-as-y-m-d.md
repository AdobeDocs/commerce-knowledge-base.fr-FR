---
title: 'ACSD-52714 : le filtre de date ne fonctionne pas dans la grille d’administration lorsqu’il est défini sur y-m-d'
description: Appliquez le correctif ACSD-52714 pour résoudre le problème Adobe Commerce en raison duquel le filtre de date ne fonctionne pas dans la grille d’administration lorsque le format de date est défini sur y-m-d.
feature: Attributes
role: Admin, Developer
exl-id: b292ab2c-e12d-40df-a9ad-19f25fbde5a0
source-git-commit: 513cb47c054dbb907810bbdc3d20d2aca9d5e42b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-52714 : Le filtre de date ne fonctionne pas dans la grille d’administration lorsqu’il est défini sur y-m-d

Le correctif ACSD-52714 corrige le problème en raison duquel le filtre de date ne fonctionne pas dans la grille d’administration lorsque le format de date est défini sur y-m-d. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.43 est installée. L’ID de correctif est ACSD-52714. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le filtre de date ne fonctionne pas dans la grille admin lorsque le format de date est défini sur y-m-d.

<u>Étapes à reproduire</u>:

1. Installez Adobe Commerce propre.
1. Modifier
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
et ajoutez
   `<dateFormat>Y-MM-dd</dateFormat>`
to
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
sous la balise
   `<dataType>date</dataType>`

1. Vider le cache `bin/magento c:f`.
1. Connectez-vous à l’administrateur et créez un client à partir de **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * à partir de : date actuelle moins 1 jour
   * à : date courante

1. Cliquez sur **[!UICONTROL Apply Filters]**.

<u>Résultats attendus</u>:

Le filtre de date de la grille fonctionne correctement, quel que soit le paramètre régional défini.

<u>Résultats réels</u>:

Le message suivant apparaît : *Nous n&#39;avons trouvé aucun enregistrement.*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
