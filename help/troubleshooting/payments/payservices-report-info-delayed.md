---
title: Données du rapport des services de paiement retardées
description: Cet article explique pourquoi les données de rapport dans les services de paiement peuvent être retardées.
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Données du rapport des services de paiement retardées

Cet article explique pourquoi les données de rapport dans les services de paiement peuvent être retardées.

## Produits et versions concernés

* [Les services de paiement](https://marketplace.magento.com/magento-payment-services.html) sont désormais compatibles avec les versions 2.4.0 à 2.4.4 d’Adobe Commerce.

## Problème

Les données de rapport des services de paiement, pour les rapports d’état de paiement des paiements et des commandes, peuvent ne pas être synchronisées immédiatement.

Une fois que vous avez facturé (capturé) une commande ou émis un avoir pour une commande, par exemple, l’état de la commande peut ne pas être immédiatement disponible.

<u>Étapes à reproduire</u> :

Conditions préalables : une commande est passée à l’aide de la fonctionnalité Services de paiement.

1. Une commande est [facturée](https://docs.magento.com/user-guide/sales/invoice-create.html) (ou [annulée](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) ou [remboursée par l&#39;intermédiaire d&#39;une note de crédit](https://docs.magento.com/user-guide/sales/credit-memos.html)) dans le [Admin](https://docs.magento.com/user-guide/stores/admin.html).
1. Accédez au rapport État du paiement de la commande pour afficher des informations sur cette commande.
1. L’état est `AUTHORIZED`, qui est l’état de la commande avant la facturation ou toute autre action de commande.

   Commerce n’a pas synchronisé les données et les a envoyées aux services de paiement. Par conséquent, le nouvel état de commande n’est pas encore reconnu par le rapport.

>[!NOTE]
>
>Il ne s’agit que d’un cas d’utilisation courant. Il peut y avoir d’autres cas d’utilisation lorsqu’une [action de commande](https://docs.magento.com/user-guide/sales/order-actions.html) se produit et que les données ne sont pas immédiatement disponibles dans le rapport applicable.

<u>Résultat attendu</u> :
Les données du rapport sont renseignées immédiatement après qu’une action a été effectuée sur une commande.

<u>Résultat réel</u> :
Il peut y avoir un délai dans les données de rapport visibles pour les actions de commande qui viennent d’être terminées. Les rapports de paiement peuvent entraîner un délai de 24 à 48 heures. Les rapports d’état des paiements de la commande peuvent être retardés de quelques heures.

## Cause

Deux facteurs affectent ce délai dans les données visibles dans l’administrateur :

* La fréquence à laquelle vous choisissez de synchroniser (exporter et conserver) les données de Commerce, via la configuration [dans l’Admin](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* Période pendant laquelle PayPal publie les données de rapport.

## Solution

Pour les rapports d’état des paiements de la commande :

1. Accédez à **Sales** > **Paiement Services**.
1. Cliquez sur **État des paiements de la commande** pour afficher le tableau des rapports d’état des paiements de la commande.
1. Forcer la resynchronisation en cliquant sur l’icône **Forcer la resynchronisation** dans le coin supérieur droit du tableau des rapports.
1. Vous devriez constater la dernière modification de l’horodatage et les nouvelles transactions chargées dans le tableau de votre rapport.

Pour les rapports de paiement PayPal, le résultat attendu est un délai de 24 à 48h en raison de la dépendance à l’égard de la période de publication des données de PayPal.
