---
title: 'MDVA-43201 : erreur lors de l’utilisation du champ DOB avec le paramètre régional PT'
description: Le correctif MDVA-43201 résout le problème d’erreur lors de l’utilisation de l’attribut du client DOB dans le formulaire d’enregistrement du client pour la langue portugaise. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 est installé. L’ID de correctif est MDVA-43201. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201 : Erreur lors de l’utilisation du champ DOB avec le paramètre régional PT

Le correctif MDVA-43201 résout le problème d’erreur lors de l’utilisation de l’attribut du client DOB dans le formulaire d’enregistrement du client pour la langue portugaise. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 est installé. L’ID de correctif est MDVA-43201. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque l’attribut du client DOB est ajouté au formulaire d’enregistrement du client pour les paramètres régionaux portugais, le formulaire renvoie l’erreur *Argument 1 transmis à iterator_to_array() doit mettre en oeuvre l’interface pouvant être parcourue, null étant donné*.

<u>Conditions préalables</u> :

Les modules B2B sont installés.

<u>Étapes à reproduire</u> :

1. Accédez à Admin > **Magasins** > **Configuration** > **Général** > **Options de paramètres régionaux**, définissez Paramètres régionaux sur **Portugais (Portugal)** et cliquez sur **Enregistrer**.
1. Réindexez et effacez le cache.
1. Accédez à **Magasins** > **Attribut** > **Client**.
1. Ouvrez l’attribut du client DOB et définissez **Show on Storefront** sur **Yes**.
1. Sélectionnez tous les formulaires **Form à utiliser dans**.
1. Enregistrez l’attribut .
1. Accédez à la page Créer un compte dans le front-end.

<u>Résultats attendus</u> :

Le formulaire d’enregistrement du client pour la boutique portugaise ne donne aucune erreur lors de l’ajout de l’attribut DOB.

<u>Résultats réels</u> :

Le formulaire d’enregistrement du client pour la boutique portugaise renvoie une erreur lors de l’ajout de l’attribut DOB.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
