---
title: "Adobe Commerce 2.4.2 B2B : modèle de courrier électronique ne mettant pas à jour le courrier électronique"
description: Cet article décrit un problème connu d’Adobe Commerce 2.4.2 B2B en raison duquel la mise à jour de certaines informations dans un modèle de courrier électronique n’est pas mise à jour dans les courriers électroniques. Ce problème a un impact sur le contenu des emails, tel que les informations du client, les taux de change, le symbole de devise, la modification du modèle de courrier électronique, etc. Aucune solution n’est disponible actuellement, mais une solution est disponible au bas de cet article.
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B : modèle de courrier électronique ne mettant pas à jour le courrier électronique

Cet article décrit un problème connu d’Adobe Commerce 2.4.2 B2B en raison duquel la mise à jour de certaines informations dans un modèle de courrier électronique n’est pas mise à jour dans les courriers électroniques. Ce problème a un impact sur le contenu des emails, tel que les informations du client, les taux de change, le symbole de devise, la modification du modèle de courrier électronique, etc. Aucune solution n’est disponible actuellement, mais une solution est disponible au bas de cet article.

## Produits et versions concernés

* Adobe Commerce on-premise 2.4.2
* Infrastructure cloud Adobe Commerce 2.4.2
* B2B 1.3.1

## Problème

<u>Étapes à reproduire</u> :

1. L’administrateur de la société crée un bon de commande (bon de commande) dans le front-end.
1. Cochez l&#39;email Approuvé automatiquement . Le **nom du client** / **taux de change** doit être des valeurs attendues.
1. Modifiez le symbole de devise (**Magasins > Configuration > Configuration de devise > Options de devise**) dans le nom de l’administrateur et de l’administrateur de la société sur la page Compte client .
1. L’administrateur client crée un autre bon de commande dans Admin.
1. Cochez l&#39;email Approuvé automatiquement .

<u>Résultats attendus :</u>

Le nom du client et le symbole monétaire sont modifiés dans les courriers électroniques et leurs nouvelles valeurs sont définies comme prévu.

<u>Résultats réels</u> :

Le nom du client et le symbole monétaire ne sont pas modifiés dans les courriers électroniques et possèdent leurs valeurs précédentes.

## Solution

Exécutez manuellement la tâche cron ou le consommateur pour propager les nouvelles informations.

## Lecture connexe

* [Gérer les files d’attente de messages](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html) dans notre documentation destinée aux développeurs.
