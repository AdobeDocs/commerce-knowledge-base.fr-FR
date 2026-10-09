---
title: Comment supprimer Magento Order Management (MOM)
description: Cet article explique comment supprimer le système Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%
---
# Comment supprimer Magento Order Management (MOM)

1. Désactivez l’intégration MOM en suivant les étapes décrites dans [Désactiver ou activer l’intégration](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Désactivez le module MOM en suivant les étapes décrites dans [Désinstaller les modules](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Pour extraire des données de commande complètes, nous proposons l’API . Pour en savoir plus, consultez la section [Référentiel de commandes](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) dans notre documentation Adobe | Magento OMS, qui couvre les informations de commande (order_repository). Utilisez la [section des spécifications](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) de nos documents Adobe | Magento OMS pour utiliser d’autres API afin d’extraire différents types d’informations.
