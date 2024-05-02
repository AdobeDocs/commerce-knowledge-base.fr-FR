---
title: "Le fichier ne peut pas être supprimé. Avertissement ! unlink : aucune erreur de fichier ou de répertoire de ce type de la part de la fonction [!DNL Admin]"
description: Cet article fournit une solution au problème d’erreur. *Le fichier ne peut pas être supprimé. Warning!unlink Aucune erreur de fichier ou de répertoire de ce type* [!DNL Admin] lorsque vous effectuez une [!DNL Javascript/CSS] videz.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *Le fichier ne peut pas être supprimé. Warning!unlink : aucune erreur de fichier ou de répertoire de ce type* de la [!DNL Admin]

Cet article fournit une solution au problème d’erreur. *Le fichier ne peut pas être supprimé. Warning!unlink : aucune erreur de fichier ou de répertoire de ce type* de la [!DNL Commerce Admin] lorsque vous effectuez une [!DNL JavaScript/CSS] videz.

## Produits et versions concernés

* Adobe Commerce 2.4.0 - 2.4.6, toutes les méthodes de déploiement

## Problème

Une erreur se produit lorsque vous effectuez une [!DNL JS/CSS] purge :

*Le fichier &quot;/app/pub/static/_cache/merge/.nfsa42d0e64799fd1000000001b&quot; ne peut pas être supprimé. Warning!unlink(/app/pub/static/_cache/merge/.nfsa42d0e64799fd1000000001b) : aucun fichier ou répertoire de ce type*

Ou : l’erreur ci-dessus s’affiche dans la variable [!DNL Admin]et/ou une erreur similaire dans [!DNL New Relic] ou dans les journaux de déploiement.

Ou : vous ne pouvez pas accéder à la création de rapports avancés et la tâche cron analytics_collect_data échoue avec cette erreur :

*Le fichier &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot; ne peut pas être supprimé. Warning!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): No such file or directory*

<u>Étapes à reproduire :</u>

Méthode 1 :

1. Connectez-vous au [!DNL Admin].
1. Accédez à **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Cliquez sur **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Méthode 2 :

1. Connectez-vous au [!DNL Admin].
1. Accédez à **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Apportez des modifications au [!UICONTROL Base URL] ou [!UICONTROL Base URL (Secure)].
1. Cliquez sur **[!UICONTROL Save Config]**.

## Solution

Si vous utilisez l’infrastructure Adobe Commerce on Cloud et que vous disposez de [!DNL magento/magento-cloud-patches] 1.0.22 installé, qui inclut le correctif, vous n’avez pas besoin d’installer séparément ACSD-50165.

Adobe Commerce on Cloud infrastructure : mise à niveau des correctifs cloud pour Commerce vers la version 1.0.22 (**ou plus récent**) qui contient ce correctif : [Correctifs cloud pour Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce sur site : appliquez ACSD-50165 à l’aide de [Outils de correctifs de qualité > Utilisation](/docs/commerce-operations/tools/quality-patches-tool/usage.html). Le correctif ACSD-50165 est fourni avec [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Lecture connexe

* [[!DNL Quality Patches Tool] > Notes de mise à jour](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) dans le guide des outils Commerce.
* [[!DNL Quality Patches Tool]: recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide des outils Commerce.
