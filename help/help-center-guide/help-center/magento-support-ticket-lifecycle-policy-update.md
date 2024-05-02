---
title: Mise à jour de la stratégie de cycle de vie des tickets du support Adobe Commerce
description: Cet article fournit des informations sur la mise à jour de la stratégie de cycle de vie des tickets d’assistance Adobe Commerce.
exl-id: c3fbcb4a-107f-48b3-afed-b9a0c5d0425c
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Mise à jour de la stratégie de cycle de vie des tickets du support Adobe Commerce

Cet article fournit des informations sur la mise à jour de la stratégie de cycle de vie des tickets d’assistance Adobe Commerce.

Le tableau suivant illustre les scénarios mis à jour. Vous trouverez des détails sur chaque scénario dans la section ci-dessous.

<table>
 <tbody>
 <tr>
 <td class="wysiwyg-text-align-center"> </td>
 <td class="wysiwyg-text-align-center"><strong>État du ticket</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Jours pour "résoudre"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Jours jusqu’à "Fermé"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Délai de notification</strong></td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>L’ingénieur fournit une solution</strong></td>
 <td class="wysiwyg-text-align-center">"En attente de votre réponse"</td>
 <td class="wysiwyg-text-align-center">3</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Jours 3 et 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Informations en attente du client</strong></td>
 <td class="wysiwyg-text-align-center">"En attente de votre réponse"</td>
 <td class="wysiwyg-text-align-center">N/A</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Jours 1, 3 et 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Le client définit sur "résolu" ou demande à l’ingénieur de définir sur "résolu".</strong></td>
 <td class="wysiwyg-text-align-center">"Résolu"</td>
 <td class="wysiwyg-text-align-center">Immédiat</td>
 <td class="wysiwyg-text-align-center">1</td>
 <td class="wysiwyg-text-align-center">Jour 1</td>
 </tr>
 </tbody>
 </table>

## Scénarios détaillés

### Lorsqu’un ingénieur fournit une solution

1. Une fois qu’une solution est fournie au client, l’ingénieur définit le statut du ticket sur &quot;En attente de votre réponse&quot;.
1. Si le client ne répond pas pendant 3 jours après la modification de l’état à &quot;En attente de réponse&quot;, le ticket est déplacé vers &quot;Résolu&quot; et le client est informé.
1. Si le client ne répond pas pendant 6 jours après la modification de l’état à &quot;En attente de réponse&quot;, le ticket est fermé et le client est informé.

### Lorsque des informations supplémentaires sont requises d’un client

1. Si une mise à jour du client est requise, l’ingénieur définit le ticket sur &quot;En attente de votre réponse&quot;.
1. Les notifications sont envoyées au client les 1er et 3 jours pour demander le suivi du client.
1. Si le client ne répond pas pendant 6 jours après la modification de l’état à &quot;En attente de réponse&quot;, le ticket est fermé et le client est informé.

### Billet défini sur &quot;Résolu&quot; par un client

Lorsqu’un ticket est défini sur &quot;Résolu&quot; par un client, il est fermé dans la journée et le client est informé.

### Le client demande à l’assistance de fermer le ticket.

Lorsqu’un client demande à l’assistance Adobe Commerce de fermer le ticket, il est fermé dans la journée et le client en est informé.

## Lecture connexe

* [Envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
* [Le lien &quot;Envoyer un ticket&quot; ne s’affiche pas sur la page de démarrage du centre d’aide Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#no-submit-link)
* [Formulaire d’envoi de ticket : le marchand ne s’affiche pas dans la liste déroulante Organisation .](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)
