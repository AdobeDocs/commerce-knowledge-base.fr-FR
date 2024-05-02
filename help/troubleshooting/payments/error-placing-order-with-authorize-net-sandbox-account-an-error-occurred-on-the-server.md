---
title: Erreur lors du placement de la commande avec le compte Authorize.net Sandbox (une erreur s’est produite sur le serveur)
description: Cet article fournit un correctif pour le message d’erreur "*Une erreur s’est produite sur le serveur*" lors du placement d’une commande à l’aide de Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Erreur lors du placement de la commande avec le compte Authorize.net Sandbox (une erreur s’est produite sur le serveur)

Cet article fournit un correctif pour &quot;*Une erreur s’est produite sur le serveur*&quot; message d’erreur lors du placement d’une commande à l’aide d’Authorize.Net Direct Post.

>[!WARNING]
>
>**Avis d’obsolescence**
>
>En raison de la directive sur le service de paiement [PSD2](https://docs.magento.com/user-guide/v2.3/stores/compliance-payment-services-directive.html) et l’évolution continue de nombreuses API, Authorize.Net risque de devenir obsolète et de ne plus être compatible avec la sécurité à l’avenir. C’est pourquoi il est désormais obsolète. Nous vous recommandons de le désactiver dans votre configuration Adobe Commerce et de passer à la [Extension de Commerce Marketplace](https://marketplace.magento.com/extensions.html).
>
>**Cette intégration est supprimée de la version Adobe Commerce 2.4.0 et a été abandonnée des versions actuelles de la version 2.3.**
>
>Pour plus d’informations sur la transition sécurisée à partir des intégrations de paiement obsolètes, voir notre [DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problème

Placement d’une commande à l’aide de [Authorize.Net Direct Post](https://docs.magento.com/user-guide/v2.3/payment/authorize-net-direct-post.html) Un compte Sandbox génère un message d’erreur :

>>
&quot;Une erreur s’est produite sur le serveur. Veuillez essayer de remettre de l&#39;ordre&quot;

## Cause 1 : le mode test est activé

Cela ne semble pas évident, mais le fichier Authorize.net **Mode test** doit être défini sur **Non** même lors du test avec le compte Sandbox.

## Solution 1 : désactiver le mode Test

1. Accédez à **Magasins** > **Configuration** > **Ventes** > **Méthodes de paiement** > **Autres modes de paiement** > **Authorize.net Publication directe**.
1. Définir **Mode test** à &quot;Non&quot; (désélectionnez **Utiliser la valeur système**, puis sélectionnez &quot;Non&quot; dans le menu).
1. Cliquez sur **Enregistrer la configuration**.

![allow-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Cause 2 : URL incorrectes

Les paramètres Authorize.net peuvent contenir des adresses URL incorrectes pour les ressources critiques Authorize.Net.

## Solution 2 : fournir des URL correctes

* **URL de la passerelle :**   `https://test.authorize.net/gateway/transact.dll`
* **URL des détails de transaction :**   `https://apitest.authorize.net/xml/v1/request.api`
* **Référence d’API :**   `https://developer.authorize.net/api/reference/`

## Si rien n’a été fait, obtenez les informations de débogage.

Si le placement d’une commande avec Authorize.net échoue avec une valeur non informative *&quot;Quelque chose s&#39;est mal passé&quot;* erreur, vérifiez Adobe Commerce `debug.log`.

### Transact.dll

Au cas où la variable `debug.log` est vide, vérifiez que la variable **transact.dll** réponse dans la console de votre navigateur web :

1. Ouvrez la console.
1. Avant de passer une commande, accédez à la **Réseau** et sélectionnez **Conserver le journal**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtrage des réponses par **transact.dll** pour afficher un message de réponse avec une erreur possible.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
