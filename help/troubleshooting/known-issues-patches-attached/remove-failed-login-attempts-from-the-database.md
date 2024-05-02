---
title: Suppression des tentatives de connexion ayant échoué de la base de données
description: Cet article explique comment supprimer les informations d’identification de connexion ayant échoué préexistantes de la base de données d’infrastructure cloud d’Adobe Commerce sur site et d’Adobe Commerce. Pour les versions 2.2.10+ et 2.3.3+, il vous suffit d’exécuter le script joint. Pour les versions antérieures 2.3.0-2.3.2-p2, vous devez appliquer un correctif pour arrêter la journalisation et exécuter le script joint afin de supprimer les informations d’identification de connexion ayant échoué préexistantes.
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Suppression des tentatives de connexion ayant échoué de la base de données

>[!NOTE]
>
>Cet article a été mis à jour le 13 avril 2020, avec un nouveau script appelé DB\_CLEANUP\_SCRIPT\_v2. Utilisez le script DB\_CLEANUP\_SCRIPT\_v2 joint pour effacer les données de connexion ayant échoué préexistantes dans des tables supplémentaires. Vous devez utiliser DB\_CLEANUP\_SCRIPT\_v2, même si vous avez déjà exécuté DB\_CLEANUP\_SCRIPT\_v1 pour vous assurer que les tables supplémentaires sont nettoyées.

Cet article explique comment supprimer les informations d’identification de connexion ayant échoué préexistantes de la base de données d’infrastructure cloud d’Adobe Commerce sur site et d’Adobe Commerce. Pour les versions 2.2.10+ et 2.3.3+, il vous suffit d’exécuter le script joint. Pour les versions antérieures 2.3.0-2.3.2-p2, vous devez appliquer un correctif pour arrêter la journalisation et exécuter le script joint afin de supprimer les informations d’identification de connexion ayant échoué préexistantes.

## **Produits et versions concernés**

* Ce problème affecte Magento Open Source, Adobe Commerce sur site et Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x et les versions antérieures.
* Les déploiements d’Adobe Commerce 1.x ne sont pas affectés.

## Problème

En 2019, un bogue a été signalé à Adobe Commerce, qui autorisait les échecs de connexion à être consignés dans une base de données dans Adobe Commerce 2.3.x et 2.2.x. En réponse, Adobe Commerce a inclus un correctif pour ce problème dans Adobe Commerce 2.3.3 et 2.2.10 (publié en octobre 2019). Bien que le correctif de ce bogue ait arrêté la journalisation des tentatives de connexion ayant échoué, les informations collectées avant la mise à jour de ces versions actuelles peuvent toujours exister. Ce correctif le plus récent efface les informations de tentatives de connexion qui ont été précédemment enregistrées, le cas échéant.   CVE-2019-8118 est décrit et suivi dans [Vulnérabilités et exposition courantes](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118).

## Solution

Le fait d’utiliser le script joint et le correctif, ou seulement le script, dépend de votre version d’Adobe Commerce :

**Adobe Commerce et versions Magento Open Source 2.3.0-2.3.2-p2**

Pour ces versions, vous devez appliquer le correctif et exécuter le script de nettoyage de base de données joint afin de mettre fin à la journalisation continue et d’éliminer les journaux.

1. Exécutez le correctif du compositeur pour arrêter la journalisation. Ce correctif est joint à l&#39;article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant. [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip). Pour plus d’informations sur l’application du correctif, voir [Comment appliquer un correctif de compositeur fourni par Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) dans notre base de connaissances de soutien.

1. Exécutez maintenant le script pour nettoyer la base de données des tentatives de connexion ayant échoué. Ce script est joint à l’article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant. [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Reportez-vous à [**Exécution du script**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) pour obtenir des instructions.

**Adobe Commerce et versions Magento Open Sources 2.3.3 et ultérieures/2.2.10 et versions ultérieures**<br>
Pour ces versions uniquement, exécutez le script ci-dessous pour effacer les anciens journaux (la journalisation a été précédemment terminée pour ces versions via un correctif publié en octobre 2019). Ce script est joint à l’article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier, ou cliquez sur le lien suivant. [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Reportez-vous à [**Exécution du script**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) pour obtenir des instructions.

**Exécution du script**

Suivez les instructions ci-dessous pour exécuter le script :

1. Put `DB_CLEANUP_SCRIPT_v2.php` dans le répertoire racine de l’installation d’Adobe Commerce ou de Magento Open Source (dans le même répertoire que l’application qui contient `app/bootstrap.php`).
1. Exécutez cette commande dans le terminal : `php DB_CLEANUP_SCRIPT_v2.php` et il lancera le processus de nettoyage de la base de données.

Si vous rencontrez des problèmes lors de l’exécution du script, veuillez [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ou nous envoyer un e-mail à l’adresse [security@magento.com](mailto:security@magento.com).

**Fichiers attachés**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
