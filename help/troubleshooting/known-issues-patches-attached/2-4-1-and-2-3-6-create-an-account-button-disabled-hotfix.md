---
title: Adobe Commerce 2.4.1 et 2.3.6 créent un bouton de compte désactivé.
description: Cet article fournit un correctif pour le problème lorsque vous avez du mal à créer un nouveau compte après avoir saisi une valeur incorrecte dans n’importe quel champ du formulaire. Par exemple, lorsque vous saisissez une adresse électronique dans un format incorrect ou que vous laissez les champs de prénom ou de nom vides ou ne saisissez pas de valeur répondant aux exigences en matière de mot de passe. Un correctif permanent sera inclus dans les versions du 1er trimestre (2.4.2, 2.4.1-p1 et 2.3.6-p1).
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1 et 2.3.6 créent un bouton de compte désactivé.

Cet article fournit un correctif pour le problème lorsque vous avez du mal à créer un nouveau compte après avoir saisi une valeur incorrecte dans n’importe quel champ du formulaire. Par exemple, lorsque vous saisissez une adresse électronique dans un format incorrect ou que vous laissez les champs de prénom ou de nom vides ou ne saisissez pas de valeur répondant aux exigences en matière de mot de passe. Un correctif permanent sera inclus dans les versions du 1er trimestre (2.4.2, 2.4.1-p1 et 2.3.6-p1).

## Problème

La variable **Création d’un compte** sur le bouton **Créer un compte** reste désactivée si un acheteur a entré des données non valides. Cela empêche les acheteurs de réessayer de créer un compte après avoir commis une erreur.

<u>Étapes à reproduire</u>:

1. Accédez à **Créer un compte client**.
1. Renseignez les champs du formulaire. Dans le **Password** , valeurs d’entrée qui ne répondent pas aux exigences du mot de passe. Par exemple :
   * Les mots de passe dans la variable **Password** et la variable **Confirmer le mot de passe** ne correspondent pas aux champs.
   * Les mots de passe dans la variable **Password** et la variable **Confirmer le mot de passe** ne sont pas assez longs.
1. Cliquez sur le bouton **Création d’un compte** bouton .

<u>Résultats attendus</u>:

* **Création d’un compte** doit rester actif/activé.
* L’utilisateur doit pouvoir créer un compte.

<u>Résultats réels</u>:

* **Création d’un compte** reste désactivé, même après avoir renseigné tous les champs requis avec des données valides/correctes.
* Le client ne peut pas créer de compte.

## Correctif

Le correctif est joint à cet article. Pour le télécharger, faites défiler l’écran jusqu’à la fin de l’article et cliquez sur le nom du fichier ou cliquez sur le lien suivant : [Téléchargez MC-38509-compositeur.patch](assets/MC-38509-composer.patch.zip)

## Versions Adobe Commerce compatibles :

Le correctif a été créé pour :

* Adobe Commerce sur l’infrastructure cloud 2.3.6 et 2.4.1.
* Adobe Commerce on-premise 2.3.6 et 2.4.1.

Le correctif n’est pas compatible avec les autres versions et éditions d’Adobe Commerce.

## Comment appliquer le correctif

Voir [Comment appliquer un correctif de compositeur fourni par Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) pour obtenir des instructions.

## Lecture connexe

* [GitHub Adobe Commerce > Envoi d’un formulaire de compte de création non valide laisse le bouton d’envoi désactivé.](https://github.com/magento/magento2/issues/30513)
* [Guide de l’utilisateur Adobe Commerce > Prise en main > Création d’un compte](https://docs.magento.com/user-guide/magento/magento-account-create.html)
