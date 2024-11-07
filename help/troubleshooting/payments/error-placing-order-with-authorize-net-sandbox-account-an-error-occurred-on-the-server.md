---
title: Erreur lors du placement de la commande avec le compte Authorize.net Sandbox (une erreur s’est produite sur le serveur)
description: Cet article fournit un correctif pour le message d’erreur "*Une erreur s’est produite sur le serveur*" lors du placement d’une commande à l’aide de Authorize.Net Direct Post.
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Erreur lors du placement de la commande avec le compte Authorize.net Sandbox (une erreur s’est produite sur le serveur)

Cet article fournit un correctif pour le message d’erreur &quot;*Une erreur s’est produite sur le serveur*&quot; lors du placement d’une commande à l’aide d’Authorize.Net Direct Post.

>[!WARNING]
>
>**Avis d’obsolescence**
>
>En raison de la directive [PSD2](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive) du service de paiement et de l’évolution constante de nombreuses API, Authorize.Net risque de devenir obsolète et de ne plus être conforme à la sécurité à l’avenir. Pour cette raison, il est désormais obsolète et nous vous recommandons de le désactiver dans votre configuration Adobe Commerce et de passer à l’ [extension de Commerce Marketplace](https://marketplace.magento.com/extensions.html) correspondante.
>
>**Cette intégration est supprimée de la version Adobe Commerce 2.4.0 et a été abandonnée des versions actuelles de 2.3.**
>
>Pour plus d’informations sur la transition sécurisée d’intégrations de paiement obsolètes, consultez notre [blog de développement](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445).

## Problème

Le placement d’une commande à l’aide du compte sandbox [Authorize.Net Direct Post](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/error-placing-order-with-authorize-net-sandbox-account-an-error-occurred-on-the-server) provoque un message d’erreur :

>>
&quot;Une erreur s’est produite sur le serveur. Veuillez essayer de remettre de l&#39;ordre&quot;

## Cause 1 : le mode test est activé

Cela ne semble pas évident, mais le paramètre **Testing Mode** de Authorize.net doit être défini sur **Non** même lors du test avec le compte Sandbox.

## Solution 1 : désactiver le mode Test

1. Accédez à **Magasins** > **Configuration** > **Ventes** > **Méthodes de paiement** > **Autres méthodes de paiement** > **Authorize.net Direct Post**.
1. Définissez **Mode test** sur &quot;Non&quot; (désélectionnez **Utiliser la valeur système**, puis sélectionnez &quot;Non&quot; dans le menu).
1. Cliquez sur **Enregistrer la configuration**.

![authorized-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## Cause 2 : URL incorrectes

Les paramètres Authorize.net peuvent contenir des adresses URL incorrectes pour les ressources critiques Authorize.Net.

## Solution 2 : fournir des URL correctes

* **URL de passerelle :**   `https://test.authorize.net/gateway/transact.dll`
* **URL des détails de transaction :**   `https://apitest.authorize.net/xml/v1/request.api`
* **Référence d’API :**   `https://developer.authorize.net/api/reference/`

## Si rien n’a été fait, obtenez les informations de débogage.

Si le placement d’une commande avec Authorize.net échoue avec une erreur non informative *&quot;Quelque chose s’est mal passé&quot;*, vérifiez l’Adobe Commerce `debug.log`.

### Transact.dll

Si `debug.log` est vide, vérifiez la réponse **transact.dll** dans la console de votre navigateur web :

1. Ouvrez la console.
1. Avant de passer une commande, accédez à l’onglet **Réseau** et sélectionnez **Conserver le journal**.    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. Filtrez les réponses par **transact.dll** pour afficher un message de réponse avec une erreur possible.    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
