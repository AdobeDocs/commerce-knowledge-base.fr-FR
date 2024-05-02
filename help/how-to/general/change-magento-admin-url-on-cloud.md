---
title: Modification de l’URL d’administration sur Adobe Commerce sur l’infrastructure cloud
description: Par défaut, l’URL [Admin Commerce](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) est définie sur *&lt;domain\_name&gt;/admin*. Cet article explique comment modifier l’URL.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Modification de l’URL d’administration sur Adobe Commerce sur l’infrastructure cloud

Par défaut, la variable [Administration de Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) L’URL est définie sur *&lt;domain _name=&quot;&quot;>/admin*. Cet article explique comment modifier l’URL.

## Méthode 1 : modification à l’aide de l’administrateur

Lisez les étapes : [Utilisation d’une URL d’administration personnalisée > Modifier depuis l’administrateur](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) dans notre guide d’utilisation.

## Méthode 2 : ajout de la variable d’environnement ADMIN\_URL

### Environnement d’intégration

Dans la [Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html), ajoutez une nouvelle variable avec :

**Nom :** ADMIN\_URL **Valeur :** nouvelle URL d’administration

* Pour obtenir des instructions détaillées, voir [ajout de variables d’environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) dans notre documentation destinée aux développeurs.
* Voir aussi [variables d&#39;environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) dans notre documentation destinée aux développeurs.

### Lorsque l’évaluation et la production ne sont pas disponibles dans la console cloud

[Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant d’ajouter la variable ADMIN\_URL pour votre environnement d’évaluation ou de production.

Si les environnements d’évaluation et de production sont accessibles à partir de la console cloud, ajoutez la variable d’environnement comme décrit dans la section *Environnement d’intégration* ci-dessus.

### Ajout de variables à l’aide de l’interface de ligne de commande de Cloud

Vous pouvez ajouter la variable ADMIN\_URL à l’aide de la commande d’interface de ligne de commande cloud suivante (pour main) :

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Pour des instructions plus détaillées, reportez-vous à la section [Modification de l’URL d’administration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) dans la rubrique Variables d’administration du guide Commerce on Cloud Infrastructure.

N’oubliez pas que l’utilisation de l’interface de ligne de commande Cloud pour modifier la variable ADMIN\_URL déclenche un redéploiement de l’environnement. Les variables sont héritées par défaut. Pour éviter l’héritage, utilisez les options de commande de l’interface de ligne de commande Cloud pour indiquer que vous ne souhaitez pas que la valeur de la variable soit héritée par les environnements enfants. Voir [Visibilité](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) rubrique à niveau variable dans le guide Commerce on Cloud Infrastructure.
