---
title: "Problème connu d’Adobe Commerce 2.4.0 : échec des tests d’intégration"
description: Cet article fournit un correctif pour le problème Adobe Commerce 2.4.0 où les tests d’intégration échouent car la déclaration de "Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()" n’est pas compatible avec PHPUnit 9 utilisé pour la version 2.4.0.
exl-id: 8e0ca2da-81d9-4561-a009-593240f46e41
feature: Integration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Problème connu d’Adobe Commerce 2.4.0 : échec des tests d’intégration

Cet article fournit un correctif pour le problème Adobe Commerce 2.4.0 où les tests d’intégration échouent car la déclaration de `Dotdigitalgroup\Email\Test\Integration\Model\Sync\Importer\ImporterFailedTest::setUp()` n’est pas compatible avec PHPUnit 9, qui est utilisé pour la version 2.4.0.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Problème

<u>Étapes à reproduire</u>

Exécutez les tests d’intégration 2.4.0.

<u>Résultat attendu</u>

Les tests réussissent.

<u>Résultat réel</u>

*Erreur fatale PHP : la déclaration de Dotdigitalgroup\\Email\\Test\\Integration\\Model\\Sync\\Importer\\ImporterFailedTest::setUp() doit être compatible avec PHPUnit\\Framework\\TestCase::setUp(): void dans /var/www/vendor/dotmailer/dotmailer-magento2-extension/Test/Integration/Model/Sync/Importer/ImporterFailedTest.php en ligne 36*

## Solution

Appliquez le correctif fourni dans cet article.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant :

[BUNDLE-2684-composer.patch](assets/BUNDLE-2684-composer.patch.zip)

### Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.4.0
* Adobe Commerce on-premise 2.4.0

## Comment appliquer le correctif

Pour obtenir des instructions, reportez-vous à la section [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de support.

## Fichiers attachés
