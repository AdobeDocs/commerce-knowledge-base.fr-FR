---
title: Mise à jour de sécurité critique requise pour une action urgente disponible pour Adobe Commerce (APSB26-146)
description: Adobe a publié le bulletin de sécurité APSB26-146 concernant CVE-2026-75650, une vulnérabilité « jour zéro » dans Adobe Commerce. Découvrez comment appliquer le correctif et faire pivoter les informations d’identification.
autotag-review: '2026-09-07T17:27:44.037Z'
TQID: 'https://experienceleague.adobe.com/ADVRRn85--ZgWtPdi4qA49fsDPVW976N4MYWp26taho'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: bd989d82-1e15-4534-88db-f1f51dd77ffaid: c32adafa-ed01-4b31-997e-2413013911b0
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: f7808502de47b7cc307415600422f360db4b802e
workflow-type: tm+mt
source-wordcount: 841
ht-degree: 0%

---


# Action urgente requise : mise à jour de sécurité critique disponible pour Adobe Commerce (APSB26-146)

>[!IMPORTANT]
>
>Il s’agit d’une mise à jour urgente liée au CVE-2026-75650. Adobe sait que CVE-2026-75650 a été exploité dans le ciblage sauvage des commerçants Adobe Commerce.

Le 7 septembre, Adobe a publié une mise à jour de sécurité critique concernant Adobe Commerce et Magento Open Source. Adobe a pris conscience d’une vulnérabilité « jour zéro » dans Adobe Commerce et a publié une mise à jour de sécurité (APSB26-146) pour la résoudre. La vulnérabilité peut permettre à un attaquant non authentifié d’exécuter du code arbitraire sur une installation affectée (CVE-2026-75650).

Adobe a publié le bulletin de sécurité APSB26-146, qui corrige cette vulnérabilité. Le bulletin est disponible ici :

[Mise à jour de sécurité disponible pour Adobe Commerce | APSB26-146](https://helpx.adobe.com/security/products/magento/apsb26-146.html)

Cet article explique comment appliquer le correctif pour les versions actuelles et antérieures d’Adobe Commerce et de Magento Open Source.

## Description

Produits et versions concernés :

Versions d’Adobe Commerce :

* 2.4.9-2026-août et versions antérieures
* 2.4.8-2026-août et versions antérieures
* 2.4.7-2026-août et versions antérieures
* 2.4.6-2026-août et versions antérieures
* 2.4.5-2026-août et versions antérieures
* 2.4.4-2026-août et versions antérieures

Versions B2B d’Adobe Commerce :

* 1.5.3-2026-août et versions antérieures
* 1.5.2-2026-août et versions antérieures
* 1.4.2-2026-août et versions antérieures
* 1.3.4-2026-août et versions antérieures
* 1.3.3-2026-août et versions antérieures

Versions de Magento Open Source :

* 2.4.9-2026-août et versions antérieures
* 2.4.8-2026-août et versions antérieures
* 2.4.7-2026-août et versions antérieures
* 2.4.6-2026-août et versions antérieures

## Résolution

### Solution pour Adobe Commerce sur Cloud, Adobe Commerce sur site et Magento Open Source

Pour aider à résoudre la vulnérabilité des produits et versions affectés, vous devez appliquer le correctif VULN-39341 (en fonction de votre version) et faire pivoter vos clés de chiffrement.

Remarque : ce correctif a été testé uniquement pour les versions répertoriées ci-dessous. Il peut fonctionner sur d’autres versions prises en charge, mais cela n’a pas été officiellement vérifié.

Versions d’Adobe Commerce :

* 2.4.9-2026-août
* 2.4.8-2026-aug
* 2.4.7-2026-aug
* 2.4.6-2026-aug
* 2.4.5-2026-aug
* 2.4.4-2026-aug

Versions B2B d’Adobe Commerce :

* 1.5.3-2026-aug
* 1.5.2-2026-aug
* 1.4.2-2026-aug
* 1.3.4-2026-aug
* 1.3.3-2026-août

Versions de Magento Open Source :

* 2.4.9-2026-août
* 2.4.8-2026-aug
* 2.4.7-2026-aug
* 2.4.6-2026-aug

### Lien du correctif

Appliquez le correctif suivant à la version du produit affectée :

* [Télécharger le correctif VULN-39341-composer-patches.zip](https://repo.magento.com/patch/VULN-39341-composer-patches.zip)

### Application du correctif

Décompressez le fichier et consultez [Comment appliquer un correctif de compositeur fourni par Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) dans notre base de connaissances d’assistance pour obtenir des instructions.

### Vérifiez que le correctif est appliqué (Adobe Commerce sur les commerçants cloud uniquement).

Étant donné qu’il n’est pas possible de déterminer facilement si le problème a été corrigé, il est recommandé de vérifier si le correctif CVE-2026-75650 a bien été appliqué.

Pour ce faire, procédez comme suit, en prenant l’`VULN-39341_Hotfix_COMPOSER.patch` de fichier comme exemple :

1. [Installation de l’outil de correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage).
1. Exécutez la commande :

`vendor/bin/magento-patches -n status | grep "39341\|Status"`

1. Vous devriez voir une sortie similaire à celle-ci, où cet exemple VULN-39341 renvoie le statut Appliqué :

| ID | Titre | Catégorie | Origine | Statut | Détail |
|---|---|---|---|---|---|
| S.O. | .../m2-hotfixes/VULN-39341_Hotfix_COMPOSER.patch | Autres frais | Local | Appliqué | Type de correctif : personnalisé |

### Faire pivoter les informations d’identification après l’application du correctif

Pour résoudre complètement ce problème, faites pivoter non seulement votre clé de chiffrement, mais toutes les informations d’identification qui peuvent avoir été chiffrées ou exposées à l’aide de celle-ci, y compris les informations d’identification de serveur, d’API et d’intégration.

>[!NOTE]
>
>La clé de chiffrement est utilisée pour chiffrer les jetons d’intégration, les informations d’identification de la passerelle de paiement et les jetons d’automatisation dotés de privilèges système. La rotation seule de la clé de chiffrement n’invalide pas les informations d’identification qui peuvent déjà avoir été exposées. Faites pivoter toutes les informations d’identification associées à leur source (par exemple, au niveau de la passerelle de paiement ou du service tiers), et pas seulement dans Commerce.

Pour faire pivoter les informations d’identification, procédez comme suit :

1. Appliquez le correctif.
1. Activez le mode de maintenance.
1. Désactivez l’exécution cron (commande Commerce on Cloud : `vendor/bin/ece-tools cron:disable`).
1. [Rotation des clés de chiffrement](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key?lang=en).
1. Faites pivoter tous les mots de passe utilisateur du panneau d’administration.
1. Désactivez et régénérez tous les jetons d’intégration REST/SOAP/GraphQL (**[!UICONTROL System]** > **[!UICONTROL Extensions]** > **[!UICONTROL Integrations]**).
1. rotation des secrets clients OAuth pour toutes les applications tierces connectées ;
1. rotation des informations d’identification de l’API de passerelle de paiement au niveau du fournisseur (Stripe, Braintree, Adyen, PayPal, etc.) ;
1. Rotation des informations d’identification de base de données.
1. Faites pivoter les clés SSH/de déploiement et les informations d’identification de compte de service avec privilège cron ou système.
1. Faites pivoter les clés d’API pour les extensions tierces intégrées de frais d’expédition, de taxes et autres.
1. Videz le cache.
1. Activez l’exécution cron (commande Commerce on Cloud : `vendor/bin/ece-tools cron:enable`).
1. Désactivez le mode de maintenance.

### Mises à jour de sécurité

Mises à jour de sécurité disponibles pour Adobe Commerce :

* [Bulletin de sécurité d’Adobe (APSB26-146)](https://helpx.adobe.com/security/products/magento/apsb26-146.html)
* [Dernières mises à jour de sécurité disponibles pour Adobe Commerce](https://helpx.adobe.com/security/products/magento.html)

### Lecture connexe

[Activation ou désactivation du mode de maintenance](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode?lang=en) dans le Guide d’installation d’Adobe Commerce
