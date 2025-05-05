---
title: Demande d’amélioration de l’environnement d’intégration - Pro et Starter
description: Si vous êtes un client d’architecture de plan Adobe Commerce on Cloud Infrastructure Pro et que vous utilisez actuellement les environnements d’intégration de taille standard, ou si vous êtes un client d’architecture de plan de démarrage de l’infrastructure cloud d’Adobe Commerce on Cloud et que vous utilisez actuellement l’environnement d’évaluation de taille standard et souhaitez plus d’énergie, vous pouvez demander une mise à niveau vers les environnements d’intégration améliorés, qui offrent environ quatre fois les performances. Cet article sépare les instructions destinées aux clients Pro des clients Starter.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Demande d’amélioration de l’environnement d’intégration - Pro et Starter

Si vous êtes un client d’architecture de plan Adobe Commerce on Cloud Infrastructure Pro et que vous utilisez actuellement les environnements d’intégration de taille standard, ou si vous êtes un client d’architecture de plan de démarrage de l’infrastructure cloud d’Adobe Commerce on Cloud et que vous utilisez actuellement l’environnement d’évaluation de taille standard et souhaitez plus d’énergie, vous pouvez demander une mise à niveau vers les environnements d’intégration améliorés, qui offrent environ quatre fois les performances. Cet article sépare les instructions destinées aux clients Pro des clients Starter.

>[!NOTE]
>
> La mise à niveau vers l’intégration améliorée peut ne pas résoudre tous les problèmes de performances, car elle dépend des exigences de ressources totales de votre installation, y compris les intégrations ou les personnalisations tierces.
>
> Vous devez également vous assurer que vous suivez les bonnes pratiques pour obtenir les meilleures performances dans l’environnement d’intégration, et même qu’il ne s’agit pas d’une solution exhaustive. Reportez-vous à la documentation suivante pour obtenir des conseils : [Architecture Pro](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) et [Architecture de démarrage](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) dans le guide Commerce on Cloud Infrastructure.

## Pro

1. Si vous utilisez Pro, pour effectuer la mise à niveau, vous devez réduire le nombre de branches d’intégration à deux (**la branche d’intégration principale est incluse dans le total**). **Remarque : Ne comptabilisez pas la branche principale dans ce total. La branche principale n’est pas considérée comme une branche d’intégration.** Suivez les étapes de la section [Gestion des branches avec la console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) de notre documentation destinée aux développeurs.
1. Le commerçant doit [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant une mise à niveau vers les environnements d’intégration améliorés, en utilisant la raison de contact &quot;*Demander une modification de configuration cloud*&quot;.
1. L’équipe d’ingénierie client d’Adobe confirme le nombre d’environnements d’intégration et commence la modification.
1. Le marchand sera informé dans le ticket lorsque la mise à niveau sera terminée.
1. Le commerçant redéploie les environnements d’intégration. Suivez les étapes de la section [Fusionner une branche](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) de notre documentation destinée aux développeurs. *Remarque* : le déploiement se produit automatiquement lorsque vous exécutez : <pre>origine push git &lt;branch-name></pre>

Des performances accrues indiquent une mise à niveau réussie vers des environnements d’intégration améliorés.

**Notes** :

* La taille standard et la taille améliorée sont les deux seules tailles disponibles.
* Tous les environnements d’intégration d’un magasin donné ont la même taille : ils ne peuvent pas être dimensionnés indépendamment.
* Si vous avez besoin de plus de deux environnements d’intégration améliorée, consultez votre équipe de compte d’Adobe.

## Starter

1. Les plans de démarrage ne peuvent pas comporter de branches d’intégration : les vendeurs doivent supprimer les environnements d’intégration et ne quitter que l’environnement d’évaluation. Suivez les étapes de la section [Gestion des branches avec la console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) de notre documentation destinée aux développeurs. Le nombre d’environnements disponibles sera réduit afin de permettre un maximum d’un environnement d’intégration.
1. Le commerçant doit [envoyer un ticket d’assistance](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) demandant une mise à niveau vers les environnements d’intégration améliorés, en utilisant la raison de contact *&quot;Demander un changement de configuration cloud&quot;* - **votre environnement d’évaluation est un environnement d’intégration appelé**.
1. L’équipe d’ingénierie client d’Adobe confirme le nombre d’environnements d’intégration et commence la modification.
1. Le marchand sera informé dans le ticket lorsque la mise à niveau sera terminée.
1. Le commerçant redéploie les environnements d’intégration. Suivez les étapes de la section [Fusionner une branche](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) de notre documentation destinée aux développeurs. *Remarque* : le déploiement se produit automatiquement lorsque vous exécutez : <pre>origine push git &lt;branch-name></pre>

Des performances accrues indiquent une mise à niveau réussie vers des environnements d’intégration améliorés.

**Notes** :

* La taille standard et la taille améliorée sont les deux seules tailles disponibles.
* Tous les environnements d’intégration d’un magasin donné ont la même taille : ils ne peuvent pas être dimensionnés indépendamment.
* Si vous avez besoin d’environnements d’intégration au-delà de l’évaluation, consultez votre équipe de compte Adobe.
* Si l’achat est effectué après le 17 septembre 2020, cette amélioration ne sera pas applicable en raison d’environnements d’intégration étendus.
