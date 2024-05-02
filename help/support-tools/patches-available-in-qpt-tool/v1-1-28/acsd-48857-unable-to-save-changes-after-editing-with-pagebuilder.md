---
title: 'ACSD-48857 : impossible d’enregistrer les modifications après modification avec [!DNL Page Builder]'
description: Appliquez le correctif ACSD-48857 pour résoudre le problème Adobe Commerce où l’utilisateur ne peut pas enregistrer les modifications après les avoir modifiées avec [!DNL Page Builder].
exl-id: c95b354d-8954-4e9c-9e92-8a64f62f0a68
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857 : impossible d’enregistrer les modifications après modification avec [!DNL Page Builder]

Le correctif ACSD-48857 corrige le problème où l’utilisateur ne peut pas enregistrer les modifications après les avoir modifiées avec [!DNL Page Builder]. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.28 est installée. L’ID de correctif est ACSD-48857. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.6

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur ne peut pas enregistrer les modifications après modification avec [!DNL Page Builder].

<u>Étapes à reproduire</u>

1. Connectez-vous au site Web d’administration.
1. Accédez à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** pour créer une page CMS vide.
1. Exécutez ce script SQL pour définir les éléments suivants : **[!UICONTROL Content]** valeur du champ :

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Revenir à **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** dans Admin.
1. Modifiez votre page.
1. Accédez au **[!UICONTROL Content]** .
1. Cliquez sur **[!UICONTROL Save]**.

<u>Résultats attendus</u>

L’assainissement du contenu du HTML est mis en oeuvre. Cette opération supprime [!DNL Page Builder] attributs de HTML réservés dans les contenus générés par l&#39;éditeur de texte.

<u>Résultats réels</u>

La page n’est pas enregistrée et le chargeur continue à tourner. Dans la console, l&#39;erreur suivante est générée :

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
