---
title: 'Adobe Commerce 2.4.2 B2B : modèle d’e-mail ne mettant pas à jour l’e-mail'
description: Cet article décrit un problème B2B Adobe Commerce 2.4.2 connu en raison duquel la mise à jour de certaines informations d’un modèle d’e-mail n’est pas effectuée dans les e-mails. Ce problème affecte les contenus d’e-mail tels que les informations client, les taux de change, le symbole de devise, la modification du modèle d’e-mail, etc. Aucune solution n’est disponible pour le moment, mais une solution de contournement se trouve au bas de cet article.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B : modèle d’e-mail ne mettant pas à jour l’e-mail

Cet article décrit un problème B2B Adobe Commerce 2.4.2 connu en raison duquel la mise à jour de certaines informations d’un modèle d’e-mail n’est pas effectuée dans les e-mails. Ce problème affecte les contenus d’e-mail tels que les informations client, les taux de change, le symbole de devise, la modification du modèle d’e-mail, etc. Aucune solution n’est disponible pour le moment, mais une solution de contournement se trouve au bas de cet article.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.2
* Adobe Commerce cloud infrastructure 2.4.2
* B2B 1.3.1

## Problème

<u>Procédure à suivre </u> :

1. Le responsable d’administration de l’entreprise crée un bon de commande dans le serveur frontal.
1. Vérifiez l’e-mail d’approbation automatique . Le **nom du client** / **taux de change** doit être une valeur attendue.
1. Modifiez le symbole de devise (**Magasins > Configuration > Configuration de la devise > Options de devise**) dans Nom de l’administrateur et de l’administrateur de la société sur la page Compte client.
1. L’administrateur du client crée un autre bon de commande dans l’administrateur.
1. Vérifiez l’e-mail d’approbation automatique .

<u>Résultats attendus :</u>

Le nom du client ou de la cliente et le symbole monétaire sont modifiés dans les e-mails et leurs nouvelles valeurs sont celles attendues.

<u>Résultats réels</u> :

Le nom du client ou de la cliente et le symbole monétaire ne sont pas modifiés dans les e-mails et conservent leurs valeurs précédentes.

## Solution

Exécutez manuellement la tâche cron ou le client pour propager les nouvelles informations.

## Lecture connexe

* [Gérer les files d’attente de messages](https://experienceleague.adobe.com/fr/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues) dans notre documentation destinée aux développeurs.
