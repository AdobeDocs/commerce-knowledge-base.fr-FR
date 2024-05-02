---
title: "ACSD-51120 : cache de demande de GET GraphQL non effacé pour les pages CMS contenant des blocs CMS"
description: Appliquez le correctif ACSD-51120 pour résoudre le problème Adobe Commerce en raison duquel le cache de demande de GET GraphQL n’est pas effacé pour les pages CMS contenant des blocs CMS.
exl-id: 22abba89-b697-45d7-972e-bf3233e5e9ec
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-51120 : cache de demande de GET GraphQL non effacé pour les pages CMS contenant des blocs CMS

Le correctif ACSD-51120 corrige le problème en raison duquel le cache de demande de GET GraphQL n’est pas effacé pour les pages CMS contenant des blocs CMS mis à jour par le biais d’une mise à jour intermédiaire. Ce correctif est disponible lorsque la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) La version 1.1.33 est installée. L’ID de correctif est ACSD-51120. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles [!DNL Quality Patches Tool] versions. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour la variable `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool]: recherchez la page des correctifs.](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le cache de requête de GET GraphQL n’est pas effacé pour les pages CMS qui contiennent des blocs CMS mis à jour par le biais d’une mise à jour intermédiaire.

<u>Étapes à reproduire</u>:

1. Créez un bloc CMS.
1. Inclure le bloc CMS dans une page CMS à l’aide du [!DNL Page Builder].
1. Récupérez la page CMS à l’aide de la requête GraphQL donnée à l’aide d’une requête GET :

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Vérifiez que la réponse GraphQL est mise en cache dans [!DNL Varnish].
1. Créez une mise à jour planifiée pour le bloc.
1. Attendez que la mise à jour planifiée s’applique et exécute la tâche cron pour appliquer la mise à jour planifiée.
1. Récupérez à nouveau la page CMS à l’aide de la requête GraphQL donnée à l’aide d’une requête GET.

<u>Résultats attendus</u>:

La réponse affiche le contenu mis à jour.

<u>Résultats réels</u>:

La réponse affiche toujours l’ancien contenu.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) dans le [!DNL Quality Patches Tool] guide.
* Adobe Commerce sur l’infrastructure cloud : [Mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de soutien.
* [Vérifiez si le correctif est disponible pour votre problème Adobe Commerce à l’aide de [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de soutien.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le [!DNL Quality Patches Tool] guide.
