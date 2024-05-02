---
title: Décharger les redirections non regex vers Fastly au lieu de Nginx (itinéraires)
description: Cette rubrique suggère une solution à un problème de performances de redirection classique que vous pouvez rencontrer lorsque vous déchargez des redirections non regex vers Fastly au lieu de Nginx dans Adobe Commerce sur l’infrastructure cloud.
exl-id: 8b22d25d-0865-4d21-b275-d344ba8748f2
feature: Routes
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Décharger les redirections non regex vers Fastly au lieu de Nginx (itinéraires)

Cette rubrique suggère une solution à un problème de performances de redirection classique que vous pouvez rencontrer lorsque vous déchargez des redirections non regex vers Fastly au lieu de Nginx dans Adobe Commerce sur l’infrastructure cloud.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud (toutes versions) `Master/Production/Staging` les environnements exploitant rapidement

## Problème

Dans Adobe Commerce sur l’infrastructure cloud, un grand nombre de redirections/réécritures non regex ne peuvent pas être effectuées sur la couche Nginx, ce qui peut entraîner des problèmes de performances.

## Cause

La variable `routes.yaml` dans le fichier `.magento/routes.yaml` définit les itinéraires de votre Adobe Commerce sur l’infrastructure cloud.

Si la taille de la variable `routes.yaml` de 32 Ko ou plus, vous devez décharger vos redirections/réécritures non regex vers Fastly.

Ce calque Nginx ne peut pas gérer un grand nombre de redirections/réécritures non regex, sinon des problèmes de performances se produiront.

## Solution

La solution consiste à décharger ces redirections non regex vers Fastly à la place. Créez un chemin d’erreur générique vers lequel rediriger rapidement.

Les étapes suivantes expliquent comment placer des redirections à la place de Nginx.

1. Créez un dictionnaire Edge.

   Tout d’abord, vous pouvez utiliser [Fragments de code VCL dans Adobe Commerce](/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) pour définir un dictionnaire Edge. Elle contient les redirections.

   Voici quelques mises en garde :

   * Fastly ne peut pas effectuer d&#39;expression régulière sur les entrées du dictionnaire. Ce n&#39;est qu&#39;une correspondance exacte. Pour plus d’informations sur ces limites, voir [Limites du dictionnaire à la périphérie de la documentation Fastly](https://docs.fastly.com/guides/edge-dictionaries/about-edge-dictionaries#limitations-and-considerations).
   * Fastly est limitée à 1000 entrées dans un seul dictionnaire. Rapidement, cette limite peut être étendue, mais cela conduit à la troisième mise en garde.
   * Chaque fois que vous mettez à jour les entrées et déployez ce VCL mis à jour sur tous les noeuds, il y a une augmentation du temps de chargement géométrique avec l’extension des dictionnaires, ce qui signifie qu’un dictionnaire d’entrée de 2 000 chargera 3 x 4 x plus lentement qu’un dictionnaire d’entrée de 1 000. Mais ce n’est un problème que lorsque vous déployez VCL (mise à jour du dictionnaire ou modification du code de fonction VCL).

     Cela n’a aucune incidence sur le temps nécessaire au traitement rapide d’une demande ; cela a un impact sur le temps nécessaire à la publication rapide d’une nouvelle configuration.

     En règle générale, les modifications de configuration prennent quelques secondes en moyenne, généralement pas plus de 5 à 10 secondes. Par conséquent, une augmentation de 2 fois des éléments du dictionnaire prend jusqu’à 30 secondes pour que votre configuration soit déployée. Une augmentation de 4 fois prendrait près de 2 minutes. Cela nous amène à la quatrième mise en garde.

   * Il y a une limite assez stricte de 10 000 entrées dans un dictionnaire de périphérie.

   Il est vivement recommandé de consolider votre liste de redirections. Vous pouvez utiliser plusieurs dictionnaires, mais n’oubliez pas que toute mise à jour que vous apportez à votre VCL prendra plusieurs minutes pour être renseignée de manière très rapide.

1. Comparez l’URL au(x) dictionnaire(s).

   Lorsque la recherche d’URL se produit, la comparaison permet d’appliquer le code d’erreur personnalisé en cas de correspondance.

   Utilisez un autre fragment de code VCL pour ajouter quelque chose comme ceci à `vcl_recv`:

   ```
        declare local var.redir-path STRING;
        set var.redir-path = table.lookup(redirects, std.tolower(req.url), "");
   
        if (var.redir-path != "") {
          error 912 var.redir-path;
        }
   ```

   Ici, nous vérifions si l&#39;URL existe dans l&#39;entrée du tableau. Si c’est le cas, nous appelons une erreur interne Fastly et nous transmettons à cette erreur l’URL de redirection à partir de la table.

1. Gérez la redirection.

   Lorsqu’une correspondance est trouvée, l’action est entreprise et définie pour celle-ci. `obj.status`, dans ce cas, une redirection 301 de déplacement permanent.

   Utilisation d’un fragment de code final dans `vcl_error` pour renvoyer les codes d’erreur 301 au client :

   ```
     if (obj.status == 912) {
        set obj.http.location = obj.response;
        set obj.status = 301;
        set obj.response = "Moved Permanently";
        return(deliver);
          }
   ```

   Avec ce bloc, nous vérifions si le code d’erreur est transmis à partir de `vcl_recv` correspond à et, si tel est le cas, nous définirons l’emplacement sur le message d’erreur transmis, puis changeons le code d’état à 301 et le message à &quot;Déplacé définitivement&quot;. À ce stade, la réponse doit être prête à revenir au client.

### Service d’évaluation

>[!WARNING]
>
>Si vous souhaitez essayer toutes ces étapes, il est vivement recommandé de configurer un environnement d’évaluation Adobe Commerce. Ainsi, vous pouvez exécuter des tests sur le service Fastly afin de vous assurer que tout se comporte comme prévu.

Si vous ne souhaitez pas exécuter un environnement d’évaluation Adobe Commerce, mais que vous souhaitez voir à quoi ressembleraient ces redirections, vous pouvez configurer un compte d’évaluation directement sur Fastly.

## Lecture connexe

* [Référence VCL très rapide](https://docs.fastly.com/vcl/)
* [Configuration des itinéraires](/docs/commerce-cloud-service/user-guide/configure/routes/routes-yaml.html) dans notre documentation destinée aux développeurs.
* [Configuration rapide](/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) dans notre documentation destinée aux développeurs.
* [Aide-mémoire pour les expressions régulières VCL](https://docs.fastly.com/en/guides/vcl-regular-expression-cheat-sheet) dans notre documentation destinée aux développeurs.
