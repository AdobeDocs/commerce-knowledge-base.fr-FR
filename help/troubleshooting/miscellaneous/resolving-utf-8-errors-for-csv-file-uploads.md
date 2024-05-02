---
title: Résolution des erreurs UTF-8 pour les chargements de fichiers CSV
description: Cet article fournit un correctif pour lorsque vous recevez le message d’erreur "Les fichiers CSV doivent utiliser le codage UTF-8". Ce message d’erreur signifie que le fichier que vous essayez de télécharger contient des caractères interdits ou des caractères interdits. Bien que le codage UTF-8 autorise [la majorité des caractères](https://www.fileformat.info/info/charset/UTF-8/list.htm), certains ne sont pas compatibles avec Magento BI.
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Résolution des erreurs UTF-8 pour les chargements de fichiers CSV

Cet article fournit un correctif pour lorsque vous recevez le message d’erreur &quot;Les fichiers CSV doivent utiliser le codage UTF-8&quot;. Ce message d’erreur signifie que le fichier que vous essayez de télécharger contient des caractères interdits ou des caractères interdits. Tandis que le codage UTF-8 autorise [la majorité des caractères](https://www.fileformat.info/info/charset/UTF-8/list.htm), certains ne sont pas compatibles avec Magento BI.

Pour résoudre le problème, vous devez modifier le codage du fichier. La réenregistrement du fichier avec le codage approprié résout généralement le problème, mais sachez que vous pouvez perdre certaines informations (par exemple, les caractères interdits peuvent être supprimés) lors de cette opération.

Nous vous recommandons d’utiliser [Sublimer le texte](https://www.sublimetext.com/2) pour enregistrer et coder le fichier.

1. Ouvrez votre fichier dans Microsoft Excel, Google Docs, Apple Numbers ou votre programme de votre choix.
1. Cliquez sur &#x200B; &#x200B; **Fichier** > **Enregistrer sous** &#x200B; &#x200B; et choisissez le  **Valeurs séparées par des virgules (.csv)** format pour enregistrer le fichier.
1. Ouvrez le fichier CSV dans Sublime Text.
1. Dans le texte sous-jacent, accédez à &#x200B; &#x200B; **Fichier** > **Enregistrer avec codage** > **UTF-8\* &#x200B;** . Le fichier CSV sera alors enregistré avec le codage UTF-8.    ![csv_file_UTF-8_sublime_3.2.2_magento_BI.png](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [Chargement des données](https://docs.magento.com/mbi/data-analyst/importing-data/connecting-data/using-file-uploader.html) (dans notre guide d’utilisation) vers un nouveau tableau dans Magento BI.
