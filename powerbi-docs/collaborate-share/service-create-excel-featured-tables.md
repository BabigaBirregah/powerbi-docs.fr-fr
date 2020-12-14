---
title: Définir des tables recommandées dans Power BI Desktop
description: Créez des tables recommandées dans Power BI Desktop pour qu’elles s’affichent dans la galerie Types de données d’organisation d’Excel.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906885"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>Définir des tables recommandées dans Power BI Desktop pour qu’elles s’affichent dans la galerie Types de données d’organisation d’Excel

Dans la galerie Types de données d’Excel, vous pouvez rechercher des données à partir des *tables recommandées* dans vos jeux de données Power BI. Dans cet article, vous allez apprendre à définir des tables comme étant *recommandées* dans vos jeux de données. Ces étiquettes permettent aux utilisateurs d’ajouter plus facilement des données d’entreprise à leurs feuilles Excel. Voici les étapes de base de la définition et du partage de tables recommandées.

1. Vous identifiez les tables recommandées dans vos jeux de données dans Power BI Desktop (cet article)
1. Vous enregistrez ces jeux de données avec les tables recommandées dans l’un des nouveaux espaces de travail. Les créateurs de rapports peuvent créer des rapports avec ces tables recommandées. 
1. Le reste de l’organisation peut se connecter à ces tables recommandées, appelées *types de données* dans Excel, pour disposer de données pertinentes et actualisables. L’article [Accéder aux tables recommandées Power BI dans Excel](service-excel-featured-tables.md) décrit la consommation de ces tables recommandées dans Excel.

> [!NOTE]
> Vous pouvez [promouvoir ou certifier des jeux de données dans Power BI](../collaborate-share/service-endorse-content.md). Cela s’appelle l’*approbation*. Excel hiérarchise les tables des jeux de données approuvés dans la galerie Types de données. Excel liste d’abord les tableaux recommandés dans les jeux de données certifiés, puis les tables des jeux de données promus. Viennent ensuite les tables recommandées des jeux de données approuvés. 

> [!NOTE]
> À partir de la version de décembre 2020 de Power BI Desktop, la création de tables recommandées est disponible par défaut. Si vous utilisez une version antérieure, mettez à niveau Power BI Desktop ou activez la fonctionnalité **Tables recommandées** via **Fichier** > **Options et paramètres** > **Options** > **Fonctionnalités en préversion**.

## <a name="select-a-table"></a>Sélectionner une table

1. Dans Power BI Desktop, accédez à la vue Modèle.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Vue Modèle":::
 
2. Sélectionnez une table et définissez **Est une table proposée** sur **Oui**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Définissez Est une table proposée sur Oui":::

4. Dans **Configurer cette table recommandée**, renseignez les champs requis :

    - Une **Description**. 
        > [!TIP]
        > Démarrez la description par « Table recommandée » pour aider les créateurs de rapports Power BI à identifier la table recommandée.
    - La valeur du champ **Étiquette de ligne** est utilisée dans Excel afin que les utilisateurs puissent facilement identifier la ligne. Elle apparaît en tant que valeur de cellule pour une cellule liée, dans le volet **Sélecteur de données** et dans la carte **Informations**. 
    - La valeur du champ **Colonne clé** fournit l’ID unique de la ligne. Cette valeur permet à Excel de lier une cellule à une ligne spécifique de la table.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Configurer la table recommandée":::

1. Une fois que vous avez publié ou importé le jeu de données dans le service Power BI, la table recommandée s’affiche dans la galerie Types de données d’Excel. Vous et d’autres créateurs de rapports pouvez également créer des rapports basés sur ce jeu de données.

1. Dans Excel : 
    - Excel met en cache la liste de types de données, ce qui vous permet de redémarrer Excel pour voir les tables recommandées qui viennent d’être publiées.
    - Certains jeux de données ne sont pas pris en charge. Les tables recommandées définies dans ces jeux de données n’apparaissent pas dans Excel. Pour plus d’informations, consultez la section suivante, Considérations et limitations.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Voici les limitations actuelles :

- L’intégration est disponible dans Excel, dans le canal actuel.
- Les tables recommandées dans les jeux de données Power BI qui utilisent les fonctionnalités suivantes ne sont pas affichées dans Excel : 

    - Jeux de données DirectQuery.
    - Jeux de données avec une connexion active.

- Excel montre seulement les données dans les colonnes, les colonnes calculées et les mesures définies dans la table recommandée. Les éléments suivants ne sont pas fournis :
   
    - Mesures définies sur les tables associées.
    - Mesures implicites calculées à partir des relations.

- Excel affiche uniquement les tables recommandées (*types de données*) qui sont stockées dans les nouveaux espaces de travail Power BI. Les tables recommandées stockées dans les espaces de travail classiques n’apparaissent pas comme types de données dans Excel. Vous pouvez [Mettre à niveau les espaces de travail classiques vers de nouveaux espaces de travail](service-upgrade-workspaces.md) dans Power BI.

L’expérience Types de données dans Excel est semblable à celle d’une fonction de recherche. Elle prend une valeur de cellule fournie par la feuille Excel et recherche les lignes correspondantes dans les tables Power BI recommandées. L’expérience Recherche présente les comportements suivants :

- La correspondance des lignes est basée sur les colonnes de texte dans la table recommandée. Elle utilise la même indexation que Power BI Q&A, qui est optimisée pour la recherche en langue anglaise. La recherche dans d’autres langues peut ne pas aboutir à des correspondances précises. 
- La plupart des colonnes numériques ne sont pas prises en compte pour la correspondance. Si l’étiquette de ligne ou la colonne clé sont numériques, elles sont incluses pour la correspondance.
- La correspondance est basée sur les correspondances Préfixe et Exacte pour les termes de recherche individuels. La valeur d’une cellule est fractionnée en fonction des espaces ou d’autres caractères d’espacement, comme les tabulations. Chaque mot est alors considéré comme un terme de recherche. Les valeurs de champ de texte d’une ligne sont comparées à chaque terme de recherche pour les correspondances de type Exacte et Préfixe. Une correspondance de préfixe est retournée si le champ de texte de la ligne commence par le terme de recherche. Par exemple, si une cellule contient « Orange County », « orange » et « County » sont des termes de recherche distincts. 

    - Les lignes avec des colonnes de texte dont la valeur correspond exactement à « Orange » ou « County » sont retournées. 
    - Les lignes avec des colonnes de texte dont la valeur commence par « Orange » ou « County » sont retournées. 
    - Il convient de noter que les lignes qui contiennent « orange » ou « county » mais ne commencent pas par ces termes ne sont pas retournées.

- Power BI retourne au maximum 100 suggestions de ligne pour chaque cellule.
- Certains symboles ne sont pas pris en charge.
- La définition ou la mise à jour de la table recommandée n’est pas prise en charge dans le point de terminaison XMLA
- Les fichiers Excel avec un modèle de données peuvent être utilisés pour publier des tables recommandées. Chargez les données dans Power BI Desktop, puis publiez la table recommandée.
- Le changement du nom de la table, d’une étiquette de ligne ou d’une colonne clé de la table recommandée peut impacter les utilisateurs Excel qui ont des cellules liées sur les lignes de la table. 
- Excel affiche le moment où les données ont été récupérées à partir du jeu de données Power BI. Ce moment n’est pas nécessairement l’heure à laquelle les données ont été actualisées dans Power BI ou l’heure du point de données le plus récent dans un jeu de données. Par exemple, imaginons qu’un jeu de données Power BI a été actualisé il y a une semaine, mais que les données sources sous-jacentes dataient d’une semaine quand l’actualisation s’est produite. Les données sont en réalité âgées de deux semaines, mais Excel affiche les données comme ayant été récupérées à la date et à l’heure auxquelles elles ont été extraites puis ajoutées à Excel.
- Pour plus d’informations sur les autres considérations relatives à Excel, consultez [Considérations et limitations](service-excel-featured-tables.md#considerations-and-limitations) dans l’article « Accéder aux tables recommandées Power BI dans Excel ».

## <a name="next-steps"></a>Étapes suivantes

- [Accéder aux tables recommandées Power BI dans Excel](service-excel-featured-tables.md)
- Vous trouverez des informations sur l’utilisation des [types de données Excel depuis Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) dans la documentation Excel.
- Vous avez des questions ? [Essayez la communauté Power BI](https://community.powerbi.com/)

