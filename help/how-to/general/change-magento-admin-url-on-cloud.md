---
title: Modifier l’URL d’administrateur sur Adobe Commerce sur l’infrastructure cloud
description: Par défaut, l’URL [Commerce Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin) est définie sur *&lt;domaine\_name&gt;/admin*. Cet article explique comment modifier l’URL.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Modifier l’URL d’administrateur sur Adobe Commerce sur l’infrastructure cloud

Par défaut, l’URL [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) est définie sur *&lt;domaine\_name>/admin*. Cet article explique comment modifier l’URL.

## Méthode 1 : modification à l’aide de l’administrateur

Lisez les étapes suivantes : [Utilisation d’une URL d’administration personnalisée > Modification à partir de l’administration](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) dans notre guide de l’utilisateur.

## Méthode 2 : ajouter la variable d’environnement ADMIN\_URL

### Environnement d’intégration

Dans la [console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html), ajoutez une nouvelle variable avec :

**Nom:** ADMIN\_URL **Valeur:** nouvelle URL d’administration

* Pour obtenir des instructions détaillées, consultez [ajout de variables d’environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) dans notre documentation destinée aux développeurs.
* Reportez-vous également à [variables d’environnement](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) dans notre documentation destinée aux développeurs.

### Lorsque les environnements d’évaluation et de production ne sont pas disponibles dans la console Cloud

[Envoyez un ticket d’assistance](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) en demandant à ajouter la variable ADMIN\_URL pour votre environnement d’évaluation ou de production.

Si l’évaluation et la production sont accessibles à partir de la console cloud, ajoutez la variable d’environnement comme décrit dans la section *Environnement d’intégration* ci-dessus.

### Ajouter des variables à l’aide de l’interface de ligne de commande Cloud

Vous pouvez ajouter la variable ADMIN\_URL à l’aide de la commande d’interface de ligne de commande Cloud suivante (pour la variable principale ) :

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Pour obtenir des instructions plus détaillées, reportez-vous à [Modifier l’URL d’administration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) dans la rubrique Variables d’administration du guide Commerce sur les infrastructures cloud.

N’oubliez pas que l’utilisation de l’interface de ligne de commande Cloud pour modifier la variable ADMIN\_URL déclenche un redéploiement de l’environnement. Les variables peuvent être héritées par défaut. Pour empêcher l’héritage, utilisez les options de commande de l’interface de ligne de commande Cloud pour indiquer que vous ne souhaitez pas que la valeur de variable héritée par les environnements enfants. Reportez-vous à la rubrique [Visibilité](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) dans Niveaux de variable dans le guide Commerce sur les infrastructures cloud.
