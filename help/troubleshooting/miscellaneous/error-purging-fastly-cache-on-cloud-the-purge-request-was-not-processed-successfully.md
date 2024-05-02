---
title: Erreur lors de la purge du cache Fastly dans Cloud (la requête de purge n’a pas été traitée correctement)
description: "Cet article fournit un correctif pour lorsque vous utilisez une option de purge rapide et que vous recevez l’erreur : *La demande de purge n’a pas été traitée avec succès*. Un service de réseau de diffusion de contenu et de mise en cache est inclus dans Adobe Commerce pour les plans d’infrastructure et les mises en oeuvre du cloud. Si vous tentez d’utiliser une option de purge rapide, et qu’elle n’est pas traitée, des informations d’identification Fastly incorrectes peuvent s’afficher dans votre environnement ou vous avez peut-être rencontré un problème."
exl-id: 568b1f4c-2ccb-4740-a6e4-d227a55fcfe6
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Erreur lors de la purge du cache Fastly dans Cloud (la requête de purge n’a pas été traitée correctement)

Cet article fournit un correctif pour lorsque vous utilisez une option de purge rapide et que vous recevez l’erreur : *La requête de purge n’a pas été traitée avec succès.*. Un service de réseau de diffusion de contenu et de mise en cache est inclus dans Adobe Commerce pour les plans d’infrastructure et les mises en oeuvre du cloud. Si vous tentez d’utiliser une option de purge rapide et qu’elle n’est pas traitée, des informations d’identification Fastly incorrectes peuvent s’afficher dans votre environnement ou vous avez peut-être rencontré un problème.

Ces informations vous aident à vérifier et à tester rapidement les en-têtes de votre site actif et de vos serveurs d’origine.

## Versions affectées

* Adobe Commerce sur l’infrastructure cloud 2.1.X et versions ultérieures
* Fastly 1.2.27 et versions ultérieures

## Problème

La mise en cache fonctionne, mais lorsque vous essayez de la purger, vous recevez une erreur ou elle ne fonctionne pas. L’erreur comprend : &quot;La requête de purge n’a pas été traitée avec succès.&quot;

## Cause

Vous disposez peut-être d’informations d’identification incorrectes définies dans votre environnement ou devez charger des fragments de code VCL.

## Résoudre

### Vérification des informations d’identification rapides

Vérifiez si votre environnement contient l’ID de service et le jeton d’API rapides corrects. Si vous disposez des informations d’identification d’évaluation dans Production, les purges peuvent ne pas être traitées ou traitées correctement.

1. Connectez-vous à votre administrateur Commerce local en tant qu’administrateur.
1. Cliquez sur **Magasins** > Paramètres > **Configuration** > **Avancé** > **Système** et développer **Cache de page complète**.    ![magento_full_page_cache_2.4.1.png](assets/magento_full_page_cache_2.4.1.png)
1. Développez Configuration rapide et vérifiez l’identifiant de service et le jeton d’API rapides pour votre environnement.
1. Si vous modifiez les valeurs, cliquez sur Tester les informations d’identification.

### Vérifier les fragments de code VCL

Si les informations d’identification sont correctes, vous pouvez rencontrer des problèmes avec vos VCL. Pour répertorier et réviser vos VCL par service, saisissez l’appel API suivant dans un terminal :

```
curl -X GET -s https://api.fastly.com/service/<Service ID>/version/<Editable Version #>/snippet -H "Fastly-Key:FASTLY_API_TOKEN"
```

Consultez la liste des VCL. Si vous rencontrez des problèmes avec les VCL par défaut de Fastly, vous pouvez charger à nouveau ou vérifier le contenu selon la variable [VCL par défaut plus rapide](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets). Pour modifier vos VCL personnalisées, voir [Fragments de code VCL personnalisés](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) dans le guide Commerce on Cloud Infrastructure.

## Informations supplémentaires

Dans notre documentation destinée aux développeurs :

* [A propos de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Configuration rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Fragments de code VCL personnalisés](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
