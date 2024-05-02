---
title: Redirection HTTP vers HTTPS pour toutes les pages d’Adobe Commerce sur l’infrastructure cloud (Forcer TLS)
description: Activez la fonctionnalité **Forcer TLS** du service Fastly dans l’administrateur Commerce afin d’activer la redirection HTTP/HTTPS globale pour toutes les pages de votre Adobe Commerce sur la boutique d’infrastructures cloud.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Redirection HTTP vers HTTPS pour toutes les pages d’Adobe Commerce sur l’infrastructure cloud (Forcer TLS)

Activez le **Forcer TLS** fonctionnalité de l’administrateur Commerce permettant d’activer la redirection HTTP/HTTPS globale pour toutes les pages de votre Adobe Commerce sur la boutique d’infrastructure cloud.

Cet article fournit des détails [étapes](#steps), un aperçu rapide de la fonction Forcer TLS , des versions affectées et des liens vers la documentation connexe.

## Étapes {#steps}

### Étape 1 : configuration des URL sécurisées {#step-1-configure-secure-urls}

Au cours de cette étape, nous définissons les URL sécurisées du magasin. Si c’est déjà fait, accédez à [Étape 2 : activation de Forcer TLS](#step-2-enable-force-tls).

1. Connectez-vous à l’administrateur Commerce.
1. Accédez à **Magasins** > **Configuration** > **Général** > **Web**.
1. Développez l’objet **URL de base (sécurisées)** .    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. Dans le **URL de base sécurisée** , spécifiez l’URL HTTPS de votre magasin.
1. Définissez la variable **Utilisation d’URL sécurisées sur Storefront** et la variable **Utilisation d’URL sécurisées sur l’administrateur** à **Oui**.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. Cliquez sur **Enregistrer la configuration** dans le coin supérieur droit pour appliquer les modifications.

**Documentation connexe dans notre guide d’utilisation :**   [URL de magasin](https://docs.magento.com/m2/ee/user_guide/stores/store-urls.html).

### Étape 2 : activation de Forcer TLS {#step-2-enable-force-tls}

1. Dans l’administrateur de Commerce, accédez à **Magasins** > **Configuration** > **Avancé** > **Système**.
1. Développez l’objet **Cache de page complète** , puis **Configuration rapide**, puis **Configuration avancée**.
1. Cliquez sur le bouton **Forcer TLS** bouton .    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. Dans la boîte de dialogue qui apparaît, cliquez sur **Télécharger**.    ![magento-admin_force-tls-confirmation-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. Une fois la boîte de dialogue fermée, assurez-vous que l’état actuel de Forcer TLS s’affiche comme **enabled**.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**Documentation Fastly connexe :**   [Guide Forcer TLS](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) pour Adobe Commerce 2.

## À propos de Forcer TLS

TLS (Transport Layer Security) est un protocole pour les connexions HTTP sécurisées qui remplace son prédécesseur moins sécurisé : le protocole SSL (Secure Socket Layer).

La fonctionnalité Forcer TLS de manière rapide vous permet de forcer toutes les requêtes non chiffrées entrantes pour les pages de votre site vers TLS.

>>
Cela fonctionne en renvoyant une *301 Déplacé définitivement* réponse à toute requête non chiffrée, qui redirige vers l’équivalent TLS. Par exemple, si vous effectuez une requête pour *http://www.example.com/foo.jpeg* redirige vers *https://www.example.com/foo.jpeg*.

[Sécuriser les communications](https://docs.fastly.com/guides/securing-communications/) (documentation rapide)

## Versions affectées

* **Adobe Commerce sur l’infrastructure cloud :**
   * version : 2.1.4 et ultérieure
   * plans : architecture du plan de démarrage d’Adobe Commerce sur l’infrastructure cloud et architecture du plan Adobe Commerce sur l’infrastructure cloud Pro (y compris Pro Legacy)
* **Fastly :** 1.2.4

## Aucune modification n’est nécessaire dans routes.yaml

Pour activer la redirection HTTP/HTTPS sur **all** Pages de votre magasin, il n’est pas nécessaire d’ajouter les pages à la variable `routes.yaml` fichier de configuration : l’activation de l’option Forcer TLS globalement pour l’ensemble de votre magasin (à l’aide de l’administrateur Commerce) est suffisante.

## Documentation rapide connexe

* [Guide Forcer TLS pour Adobe Commerce 2](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [Forcer une redirection TLS](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [Sécuriser les communications](https://docs.fastly.com/guides/securing-communications/)
