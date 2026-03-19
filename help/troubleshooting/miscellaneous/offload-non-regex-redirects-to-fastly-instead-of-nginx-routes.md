---
title: Déchargement des redirections non [!DNL regex] vers [!DNL Fastly] au lieu de [!DNL Nginx] (itinéraires)
description: Cette rubrique propose une solution à un problème de performances des redirections standard qui peut se produire lorsque vous déchargez des redirections non [!DNL regex] vers  [!DNL Fastly]  plutôt que  [!DNL Nginx]  dans Adobe Commerce sur l’infrastructure cloud.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Décharger les redirections non [!DNL regex] vers [!DNL Fastly] au lieu de [!DNL Nginx] (itinéraires)

Cette rubrique propose une solution à un problème de performances des redirections standard qui peut se produire lorsque vous déchargez des redirections non [!DNL regex] vers [!DNL Fastly] au lieu de les [!DNL Nginx] dans Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur les infrastructures cloud (toutes versions) `Master/Production/Staging` les environnements utilisant [!DNL Fastly]

## Problème

Dans Adobe Commerce sur les infrastructures cloud, un grand nombre de redirections/réécritures non [!DNL regex] ne peuvent pas être effectuées au niveau de la couche [!DNL Nginx] et peuvent donc entraîner des problèmes de performances.

## Cause

Le fichier `routes.yaml` dans le répertoire `.magento/routes.yaml` définit les itinéraires pour votre Adobe Commerce sur l’infrastructure cloud.

Si la taille de votre fichier `routes.yaml` est de 32 Ko ou plus, vous devez décharger vos redirections/réécritures non [!DNL regex] vers [!DNL Fastly].

Cette couche de [!DNL Nginx] ne peut pas gérer un grand nombre de redirections/réécritures non [!DNL regex], sinon des problèmes de performances se produiront.

## Solution

La solution consiste à décharger ces redirections non [!DNL regex] vers [!DNL Fastly]. Créez un chemin d’erreur générique pour rediriger vers [!DNL Fastly].

Les étapes suivantes expliquent comment placer des redirections sur [!DNL Fastly] au lieu de [!DNL Nginx].

1. Créez un dictionnaire Edge.

   Tout d’abord, vous pouvez utiliser des [[!DNL VCL] fragments de code dans Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html?lang=fr) pour définir un dictionnaire de périphérie. Il contiendra les redirections.

   Quelques mises en garde à ce sujet :

   * [!DNL Fastly] ne pouvez pas effectuer de [!DNL regex] sur les entrées du dictionnaire. C&#39;est juste une correspondance exacte. Pour plus d’informations sur ces limitations, consultez la documentation de [[!DNL Fastly] sur les limitations des dictionnaires Edge](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * [!DNL Fastly] est limité à 1 000 entrées dans un seul dictionnaire. [!DNL Fastly] pouvez augmenter cette limite, mais cela nous amène au troisième avertissement.
   * Chaque fois que vous mettez à jour les entrées et déployez ce [!DNL VCL] mis à jour sur tous les nœuds, le temps de chargement géométrique augmente avec les dictionnaires en expansion, ce qui signifie qu’un dictionnaire de 2 000 entrées se charge en fait 3 à 4 fois plus lentement qu’un dictionnaire de 1 000 entrées. Mais ce problème ne se pose que lorsque vous déployez le [!DNL VCL] (mise à jour du dictionnaire ou modification du code de la fonction [!DNL VCL]).

     Cela n’a aucune incidence sur le temps nécessaire au [!DNL Fastly] de traitement d’une demande ; cela a simplement une incidence sur le temps qu’il [!DNL Fastly] faut pour pousser une nouvelle configuration.

     En règle générale, les modifications de configuration prennent quelques secondes en moyenne, généralement pas plus de 5 à 10 secondes. Ainsi, une multiplication par 2 des éléments du dictionnaire prend plus de 30 secondes pour déployer votre configuration. Une augmentation de 4 fois prendrait près de 2 minutes. Cela nous amène à la quatrième mise en garde.

   * Il y a une limite assez stricte de 10 000 entrées dans un dictionnaire Edge.

   Il est vivement recommandé de consolider votre liste de redirections vers le bas. Vous pouvez utiliser plusieurs dictionnaires, mais sachez simplement que toute mise à jour de votre [!DNL VCL] prendra plusieurs minutes pour être réellement renseignée sur [!DNL Fastly].

1. Comparez les [!DNL URL] au(x) dictionnaire(s).

   Lorsque la recherche [!DNL URL] se produit, la comparaison est effectuée pour appliquer le code d’erreur personnalisé si une correspondance est trouvée.

   Utilisez un autre fragment de code [!DNL VCL] pour ajouter un élément semblable au suivant à `vcl_recv` :

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Ici, nous vérifions si le [!DNL URL] existe dans l’entrée du tableau. Si c’est le cas, nous appelons une erreur de [!DNL Fastly] interne et transmettons à cette erreur le [!DNL URL] de redirection de la table .

1. Gérez la redirection.

   Lorsqu’une correspondance est trouvée, l’action définie pour cette `obj.status` est exécutée, dans ce cas une redirection de déplacement permanent 301.

   Utilisez un dernier fragment de code dans `vcl_error` pour renvoyer les codes d’erreur 301 au client :

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Avec ce bloc, nous vérifions si le code d’erreur transmis par `vcl_recv` correspond, et si c’est le cas, nous définissons l’emplacement sur le message d’erreur transmis, puis modifions le code d’état en 301 et le message en « Déplacé de manière permanente ». À ce stade, la réponse doit être prête à être renvoyée au client.

### Service d’évaluation

>[!WARNING]
>
>Si vous souhaitez tester toutes ces étapes, il est vivement recommandé de configurer un environnement d’évaluation Adobe Commerce. De cette façon, vous pouvez exécuter des tests sur le service [!DNL Fastly] pour vous assurer que tout se comporte comme prévu.

Si vous ne souhaitez pas exécuter un environnement d’évaluation Adobe Commerce, mais que vous souhaitez voir à quoi ressembleraient ces redirections, vous pouvez configurer un compte d’évaluation directement sur [!DNL Fastly].

## Lecture connexe

* [[!DNL Fastly VCL] référence](https://docs.fastly.com/vcl/)
* [Configurer les itinéraires](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html?lang=fr) dans notre documentation destinée aux développeurs
* [Configuration [!DNL Fastly]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=fr) dans notre documentation destinée aux développeurs
* [[!DNL VCL]  aide-mémoire pour l’expression régulière &#x200B;](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) dans notre documentation destinée aux développeurs
* [Recommandations relatives à la modification des tables de base de données](https://experienceleague.adobe.com/fr/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel Commerce Implementation Playbook
