---
title: 'Décharger non-[!DNL regex] redirige vers [!DNL Fastly] au lieu de [!DNL Nginx] (routes)'
description: Cette rubrique suggère une solution à un problème de performances de redirection classique que vous pouvez rencontrer lorsque vous déchargez des redirections non-[!DNL regex] vers [!DNL Fastly] au lieu de [!DNL Nginx] dans Adobe Commerce sur l’infrastructure cloud.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Décharger les redirections non-[!DNL regex] vers [!DNL Fastly] au lieu de [!DNL Nginx] (itinéraires)

Cette rubrique suggère une solution à un problème de performances de redirection classique que vous pouvez rencontrer lorsque vous déchargez des redirections non-[!DNL regex] vers [!DNL Fastly] au lieu de [!DNL Nginx] dans Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l&#39;infrastructure cloud (toutes versions) `Master/Production/Staging` environnements exploitant [!DNL Fastly]

## Problème

Dans Adobe Commerce sur l’infrastructure cloud, un grand nombre de redirections/réécritures non-[!DNL regex] ne peuvent pas être effectuées sur la couche [!DNL Nginx], ce qui peut entraîner des problèmes de performances.

## Cause

Le fichier `routes.yaml` du répertoire `.magento/routes.yaml` définit les itinéraires de votre Adobe Commerce sur l’infrastructure cloud.

Si la taille de votre fichier `routes.yaml` est supérieure ou égale à 32 Ko, vous devez décharger vos redirections/réécritures non-[!DNL regex] vers [!DNL Fastly].

Cette couche [!DNL Nginx] ne peut pas gérer un grand nombre de redirections/réécritures non [!DNL regex], sinon des problèmes de performances se produiront.

## Solution

La solution consiste à décharger ces redirections non-[!DNL regex] vers [!DNL Fastly] à la place. Créez un chemin d’erreur générique pour la redirection vers [!DNL Fastly].

Les étapes suivantes expliquent comment placer des redirections sur [!DNL Fastly] au lieu de [!DNL Nginx].

1. Créez un dictionnaire Edge.

   Tout d’abord, vous pouvez utiliser des [[!DNL VCL] fragments de code dans Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) pour définir un dictionnaire Edge. Elle contient les redirections.

   Voici quelques mises en garde :

   * [!DNL Fastly] ne peut pas faire [!DNL regex] sur les entrées du dictionnaire. Ce n&#39;est qu&#39;une correspondance exacte. Pour plus d’informations sur ces limites, consultez la documentation de [[!DNL Fastly] sur les limites du dictionnaire Edge](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * [!DNL Fastly] est limitée à 1 000 entrées dans un seul dictionnaire. [!DNL Fastly] peut étendre cette limite, mais cela conduit à la troisième mise en garde.
   * Chaque fois que vous mettez à jour les entrées et déployez qui a mis à jour [!DNL VCL] sur tous les noeuds, il y a une augmentation du temps de chargement géométrique avec l’extension des dictionnaires, ce qui signifie qu’un dictionnaire d’entrée de 2 000 chargera 3 x 4 x 4 x plus lentement qu’un dictionnaire d’entrée de 1 000. Mais ce n’est un problème que lorsque vous déployez [!DNL VCL] (mise à jour du dictionnaire ou modification du code de la fonction [!DNL VCL]).

     Cela n’a aucune incidence sur le temps nécessaire au traitement d’une requête par [!DNL Fastly] ; cela a un impact sur le temps nécessaire à [!DNL Fastly] pour pousser une nouvelle configuration.

     En règle générale, les modifications de configuration prennent quelques secondes en moyenne, généralement pas plus de 5 à 10 secondes. Par conséquent, une augmentation de 2 fois des éléments du dictionnaire prend jusqu’à 30 secondes pour que votre configuration soit déployée. Une augmentation de 4 fois prendrait près de 2 minutes. Cela nous amène à la quatrième mise en garde.

   * Il y a une limite assez stricte de 10 000 entrées dans un dictionnaire de périphérie.

   Il est vivement recommandé de consolider votre liste de redirections. Vous pouvez utiliser plusieurs dictionnaires, mais sachez que toute mise à jour que vous apportez à votre [!DNL VCL] prendra plusieurs minutes pour être renseignée dans [!DNL Fastly].

1. Comparez le [!DNL URL] au(x) dictionnaire(s).

   Lorsque la recherche [!DNL URL] se produit, la comparaison est effectuée pour appliquer le code d’erreur personnalisé si une correspondance est trouvée.

   Utilisez un autre extrait de code [!DNL VCL] pour ajouter à `vcl_recv` un élément du type :

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Ici, nous vérifions si le [!DNL URL] existe dans l’entrée de la table. Si c&#39;est le cas, nous allons appeler une erreur interne [!DNL Fastly] et transmettre à cette erreur la redirection [!DNL URL] depuis la table.

1. Gérez la redirection.

   Lorsqu’une correspondance est trouvée, l’action est effectuée qui est définie pour cet `obj.status`, dans ce cas une redirection de déplacement permanente 301.

   Utilisez un fragment de code final dans `vcl_error` pour renvoyer les codes d’erreur 301 au client :

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Avec ce bloc, nous vérifions si le code d’erreur transmis à partir de `vcl_recv` correspond. Si c’est le cas, nous définirons l’emplacement sur le message d’erreur transmis, puis changerons le code d’état à 301 et le message à &quot;Déplacé définitivement&quot;. À ce stade, la réponse doit être prête à revenir au client.

### Service d’évaluation

>[!WARNING]
>
>Si vous souhaitez essayer toutes ces étapes, il est vivement recommandé de configurer un environnement d’évaluation Adobe Commerce. Ainsi, vous pouvez exécuter des tests sur le service [!DNL Fastly] pour vous assurer que tout se comporte comme prévu.

Si vous ne souhaitez pas exécuter un environnement d’évaluation Adobe Commerce, mais que vous souhaitez voir à quoi ressembleraient ces redirections, vous pouvez configurer un compte intermédiaire directement sur [!DNL Fastly].

## Lecture connexe

* [[!DNL Fastly VCL] reference](https://docs.fastly.com/vcl/)
* [Configuration des itinéraires](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) dans notre documentation destinée aux développeurs
* [Configuration [!DNL Fastly]](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans notre documentation destinée aux développeurs
* [[!DNL VCL] Aide-mémoire pour les expressions régulières](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) dans notre documentation destinée aux développeurs
* [ Bonnes pratiques pour la modification des tables de base de données](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) dans le manuel de mise en oeuvre de Commerce
