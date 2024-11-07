---
title: 'MDVA-39605 : Redis cache TTL (date d’expiration) a une valeur incorrecte'
description: Le correctif MDVA-39605 résout le problème en raison duquel le délai d’expiration (TTL) du cache des redis a une valeur incorrecte. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 est installé. L’ID de correctif est MDVA-39605. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605 : Redis cache TTL (date d’expiration) avec une valeur incorrecte

Le correctif MDVA-39605 résout le problème en raison duquel le délai d’expiration (TTL) du cache des redis a une valeur incorrecte. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 est installé. L’ID de correctif est MDVA-39605. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La valeur TTL (date d’expiration) du cache Redis est incorrecte.

<u>Étapes à reproduire</u> :

Pour tester le correctif, videz le cache et ouvrez un produit configurable sur le storefront. Ouvrez ensuite un terminal (console) et procédez comme suit :

1. Exécutez la commande : `redis-cli`.
1. Exécutez `KEYS "*PRICE"` (il ne doit y avoir qu’une seule clé dans le résultat, par exemple `zc:ti:e54_PRICE`). Copiez la clé.
1. Exécutez `SMEMBERS` suivi de la clé de l’étape précédente (par exemple, `SMEMBERS zc:ti:e54_PRICE`). Copiez une clé du résultat (par exemple, e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Exécutez `KEYS "*<key>"` avec le nom de clé de l’étape précédente pour obtenir le nom de clé complet (par exemple, `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Le résultat ne doit contenir qu’une seule clé (par exemple, `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Comme vous pouvez le constater, le nom de la clé complète est simplement le nom de la clé avec le préfixe &quot;`zc:k:`&quot;. Copiez maintenant le nom complet de la clé.
1. Exécutez `HGETALL` suivi du nom de clé complet de l’étape 4 pour vérifier la valeur. La valeur doit contenir les données sérialisées des produits associés d’un produit configurable associé.
1. Exécutez `TTL` suivi du nom complet de la clé de l&#39;étape 4 pour vérifier si la clé a une expiration. Le résultat doit être différent de **-1** et **-2** et doit être d’environ 2592000 (30 jours). Bien que l’expiration définie dans le code soit d’un an, la bibliothèque Redis utilisée dans Adobe Commerce a une limite d’expiration maximale (hard max) de 2592000.

<u>Résultats attendus</u> :

La limite d’expiration est de 2592000

<u>Résultats réels</u> :

La limite d&#39;expiration est définie sur **-1** ou **-2**.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [Guide de mise à jour logicielle > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) dans notre documentation destinée aux développeurs.
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) dans notre documentation destinée aux développeurs.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) dans notre base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) dans notre base de connaissances de support.

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à la section [Correctifs disponibles dans QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de notre documentation destinée aux développeurs.
