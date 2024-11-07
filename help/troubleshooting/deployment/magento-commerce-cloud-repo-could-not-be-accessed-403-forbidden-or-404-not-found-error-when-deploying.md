---
title: "Impossible d’accéder à Adobe Commerce sur le référentiel cloud : erreur 403 Forbidden ou 404 Not Found lors du déploiement"
description: "Cet article explique comment résoudre l’erreur de déploiement ayant échoué dans l’infrastructure cloud d’Adobe Commerce comme suit :"
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# Impossible d’accéder à Adobe Commerce sur le référentiel cloud : erreur 403 Forbidden ou 404 Not Found lors du déploiement

Cet article explique comment résoudre l’erreur de déploiement ayant échoué dans l’infrastructure cloud d’Adobe Commerce comme suit :

&quot;*Impossible d’accéder à l’URL https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; : HTTP/1.1 403 Forbidden* &quot;. Ou le fichier &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot; n’a pas pu être téléchargé (HTTP/1.1 404 Not Found)*&quot;.

## Produits et versions concernés

* Adobe Commerce sur l’infrastructure cloud 2.2.x, 2.3.x et 2.4.x

## Problème

Message d’erreur sur le déploiement indiquant que l’URL du référentiel n’a pas été accessible.

<u>Étapes à reproduire</u>

Déclenchez le déploiement manuellement ou en effectuant une fusion, une notification push ou une synchronisation de votre environnement.

<u>Résultat réel</u>

Le déploiement est bloqué. Dans le journal des erreurs de déploiement de l’interface utilisateur de projet, un message d’erreur semblable à ce qui suit s’affiche :

*&quot;Impossible d’accéder à l’URL &quot;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39;&quot; : HTTP/1.1 \[403 Forbidden or 404 Not Found\]&quot;*.

(Cliquez sur l’icône &quot;Échec&quot; dans l’interface utilisateur du projet pour afficher le journal.)

<u>Résultat attendu</u>

Le déploiement est terminé avec succès.

## Cause

L’erreur est due au fait que les clés d’autorisation (clés d’accès) ne sont pas valides, ne sont pas spécifiées ou ne sont pas correctement spécifiées.

Voici quelques raisons pour lesquelles les clés ne sont pas valides :

* Vous avez généré les clés à l’aide de votre compte partagé.
* Votre licence a été précédemment révoquée en raison de problèmes de paiement.

>[!NOTE]
>
>Si vous constatez que cela est dû à un problème de facturation ou de contrat non valide, veuillez contacter votre équipe de compte d’Adobe pour obtenir des instructions pour résoudre ce problème. Une fois votre licence réactivée, vos droits d’assistance et de déploiement seront restaurés.

## Solution

Procédez comme suit pour résoudre le problème à l’aide des clés d’autorisation (voir les sections ci-dessous pour plus d’informations sur chaque étape) :

1. Procurez-vous les clés d’autorisation valides (ignorez cette option si vous êtes absolument certain que votre clé est valide).
1. Ajoutez la valeur keys dans la variable `env:COMPOSER_AUTH` (ou assurez-vous que la valeur correcte est bien présente) et vérifiez si les clés sont spécifiées de manière cohérente dans la variable au niveau du projet et de l’environnement, ainsi que dans le fichier `auth.json` (s’il existe) dans la racine du projet.
1. Mettez à jour ou supprimez `auth.json` pour disposer d’un seul emplacement où la clé est configurée, si les valeurs des clés d’autorisation ne sont pas spécifiées ou ont une autre valeur.

### 1. Obtention de clés d’autorisation valides

Si vous utilisiez les clés créées sous le compte partagé, vous devez contacter le propriétaire de la licence Adobe Commerce qui vous fournit l’accès et lui demander de générer les clés pour vous.

Si votre licence a été précédemment révoquée en raison de problèmes de paiement et que vous avez résolu ces problèmes et que votre licence a été renouvelée, vous devez [générer les nouvelles clés d’authentification](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html).

### 2. Ajoutez la valeur keys dans la variable env:COMPOSER\_AUTH et vérifiez si les mêmes clés sont spécifiées dans auth.json.

Consultez les instructions et les informations connexes dans [Préparation de votre système existant](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview) et [Ajout de clés d’authentification](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview) dans notre documentation destinée aux développeurs.

### 3. Mise à jour ou suppression du fichier auth.json

Vous trouverez ci-dessous une description détaillée de la mise à jour de vos clés d’autorisation :

1. Connectez-vous à l’ordinateur sur lequel votre Adobe Commerce se connecte à l’aide des clés SSH de l’infrastructure cloud.
1. Connectez-vous à votre projet : `magento-cloud login`
1. Créez une branche pour mettre à jour le code (dans l’exemple suivant, le nom de la branche est `auth` créé à partir de la branche principale) :     `magento-cloud environment:branch auth master`
1. Modifiez le répertoire racine du projet.
1. Facultatif : supprimez le `auth.json` si vous préférez et continuez à [étape 9](#step9).
1. Ouvrez `auth.json` dans un éditeur de texte.

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. Ajoutez les clés d’authentification correctes.
1. Enregistrez vos modifications et quittez l’éditeur de texte.
1. Validez et fusionnez vos modifications :

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. Attendez que le projet soit déployé.
