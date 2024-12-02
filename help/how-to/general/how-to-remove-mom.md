---
title: Comment supprimer Magento Order Management (MOM)
description: Cet article explique comment supprimer le système de Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Comment supprimer Magento Order Management (MOM)

1. Désactivez l&#39;intégration MOM en suivant les étapes de la section [Désactiver ou activer l&#39;intégration](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Désactivez le module MOM en suivant les étapes de la section [Désinstallation des modules](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Pour extraire des données de commande complètes, nous proposons l’API . Pour en savoir plus, consultez la section [Référentiel de commandes](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) dans notre Adobe | Documents OMS Magento, qui couvrent les informations de commande (order_repository). Utilisez la [section des spécifications](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) dans notre Adobe | Documents OMS Magento pour utiliser d’autres API pour extraire différents types d’informations.
