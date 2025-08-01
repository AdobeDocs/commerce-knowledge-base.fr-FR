---
title: Erreur 404 sur toutes les pages en raison d’un problème d’évaluation du contenu
description: Cet article fournit un correctif pour le problème d’Adobe Commerce On-premise et d’Adobe Commerce sur l’infrastructure cloud où vous obtenez une erreur 404 lors de l’accès à une page de storefront ou au [!UICONTROL Commerce Admin].
exl-id: 62d8ba6e-8550-4e1e-8e8d-8f319c92778a
feature: CMS, Catalog Management, Categories, Page Content, Staging
role: Developer
source-git-commit: 48f06a90108842e00745b75db2f56a320704faf5
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Erreur 404 sur toutes les pages en raison d’un problème d’évaluation du contenu

Cet article fournit un correctif pour le problème d’Adobe Commerce On-premise et d’Adobe Commerce sur l’infrastructure cloud où vous obtenez une erreur 404 lors de l’accès à une page de storefront ou au [!UICONTROL Commerce Admin].

## Produits et versions concernés

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Adobe Commerce sur les infrastructures cloud 2.2.x, 2.3.x

## Problème

>[!NOTE]
>
>Cet article ne s’applique pas à la situation dans laquelle vous obtenez une erreur 404 lors de la tentative de [prévisualisation de la mise à jour de l’évaluation](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/guide-overview#preview-the-scheduled-change). Si vous rencontrez ce problème, ouvrez un ticket d’assistance [support](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

L’accès à une page de storefront ou à Admin entraîne l’erreur 404 (la page « Oups, notre méchant... ») après l’exécution d’opérations avec des mises à jour planifiées pour les ressources de contenu de magasin à l’aide de [Évaluation du contenu](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html) (mises à jour pour les ressources de contenu de magasin planifiées à l’aide du module [Magento\_Évaluation](https://developer.adobe.com/commerce/php/module-reference/)). Par exemple, vous avez peut-être supprimé un produit avec une mise à jour planifiée ou supprimé la date de fin de la mise à jour planifiée.

Une ressource de contenu de magasin comprend les éléments suivants :

* Produit
* Catégorie
* Règle de prix de catalogue
* Règle de prix du panier
* Page CMS
* Bloc CMS
* Widget

Certains scénarios sont abordés dans la section Cause ci-dessous.

## Cause

La table `flag` de la base de données (DB) contient des liens non valides vers la table `staging_update`.

Le problème est lié à l’évaluation du contenu. Vous trouverez ci-dessous deux scénarios particuliers ; notez qu’il peut y avoir d’autres situations qui déclenchent le problème.

**Scénario 1 :** suppression d’une ressource de contenu de magasin qui :

* a une mise à jour planifiée avec l’évaluation de contenu
* la mise à jour comporte une date de fin (c’est-à-dire la date d’expiration après laquelle la ressource mise à jour revient à sa version précédente)
* la date de fin de la mise à jour est passée

Dans le même temps, le problème peut ne pas se produire si une ressource supprimée ne dispose pas d’une date de fin pour la mise à jour planifiée.

**Scénario 2 :** suppression de la date/l’heure de fin d’une mise à jour planifiée.

### Déterminer si votre problème est lié

Pour déterminer si le problème que vous rencontrez est celui décrit dans cet article, exécutez la requête de base de données suivante :

```sql
   SELECT f.flag_data >'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists
   -> FROM flag f
   -> LEFT JOIN staging_update su
   -> ON su.id = f.flag_data >'$.current_version'
   -> WHERE flag_code = 'staging';
```

Si la requête renvoie une table où `update_exists` valeur est « 0 », un lien non valide vers la table `staging_update` existe dans votre base de données et les étapes décrites dans la [section Solution](#solution) aideront à résoudre le problème. Voici un exemple de résultat de la requête avec `update_exists` valeur égale à « 0 » :

![update_exists_0.png](assets/update_exists_0.png)

Si la requête renvoie une table où `update_exists` valeur est « 1 » ou un résultat vide, cela signifie que votre problème n’est pas lié aux mises à jour d’évaluation. Voici un exemple de résultat de la requête avec `update_exists` valeur égale à « 1 » :

![updated_exists_1.png](assets/updates_exist_1.png)

Dans ce cas, vous pouvez vous reporter au [dépanneur de site en panne](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27152) pour obtenir des idées de dépannage.

## Solution

1. Exécutez la requête suivante pour supprimer le lien non valide vers la table `staging_update` :

   ```sql
   DELETE FROM flag WHERE flag_code = 'staging';
   ```

1. Patientez jusqu’à ce que la tâche [!DNL cron] s’exécute (s’exécute en cinq minutes si elle est correctement configurée) ou exécutez-la manuellement si vous n’avez pas [!DNL cron] configuration.

Le problème doit être résolu immédiatement après la correction du lien non valide. Si le problème persiste, [envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).

## Lecture connexe

[Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
