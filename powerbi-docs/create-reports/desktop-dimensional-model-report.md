---
title: 'Tutoriel : Générer un rapport exceptionnel à partir d’un modèle dimensionnel dans Power BI Desktop'
description: Dans ce tutoriel, vous allez partir d’un modèle dimensionnel et créer un rapport de bout en bout en 20 minutes.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 01/11/2021
LocalizationGroup: Reports
ms.openlocfilehash: f5d35d7fc189f055a6f51e493fd313eb31f0564f
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565990"
---
# <a name="tutorial-from-dimensional-model-to-stunning-report-in-power-bi-desktop"></a>Tutoriel : Générer un rapport exceptionnel à partir d’un modèle dimensionnel dans Power BI Desktop 

Dans ce tutoriel, vous allez partir d’un modèle dimensionnel et créer un rapport de bout en bout en 45 minutes.

Vous travaillez chez AdventureWorks et votre responsable souhaite voir un rapport sur vos derniers chiffres de vente. Il vous a demandé un rapport de synthèse de ce qui suit : 

- Quel jour y a-t-il eu le plus de ventes en février 2019 ? 
- Dans quel pays la société rencontre-t-elle le plus de succès ? 
- Quelles sont les catégories de produits et les types de revendeurs dans lesquels l’entreprise doit continuer à investir ? 

À l’aide de notre [exemple de classeur Excel AdventureWorks Sales](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx), nous pouvons générer ce rapport en un rien de temps. Voici à quoi ressemblera le rapport final : 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Rapport AdventureWorks terminé.":::

Vous souhaitez voir le produit fini ? Vous pouvez également télécharger le [fichier .pbix Power BI terminé](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix).

Allons-y ! 

Dans ce tutoriel, vous allez découvrir comment :

> [!div class="checklist"]
> * Préparer vos données avec quelques transformations.
> * Créer un rapport avec un titre, trois visuels et un segment.
> * Publier votre rapport sur le service Power BI pour pouvoir le partager avec vos collègues.

## <a name="prerequisites"></a>Prérequis

- Avant de commencer, vous devez [télécharger Power BI Desktop](../fundamentals/desktop-get-the-desktop.md). 
- Si vous envisagez de publier votre rapport sur le service Power BI et que vous n’êtes pas encore inscrit, [inscrivez-vous pour obtenir un essai gratuit](../fundamentals/service-self-service-signup-for-power-bi.md). 

## <a name="get-data-download-the-sample"></a>Obtenir des données : Télécharger l’exemple 

1. Téléchargez l’[exemple de classeur Excel AdventureWorks Sales](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx). 

1. Ouvrez Power BI Desktop. 

1. Dans la section **Données** du ruban **Accueil**, sélectionnez **Excel**. 

1. Accédez à l’emplacement où vous avez enregistré l’exemple de classeur, puis sélectionnez **Ouvrir**. 

## <a name="prepare-your-data"></a>Préparer vos données 

Dans le volet Navigateur, vous avez la possibilité de *transformer* ou *charger* les données. Le Navigateur fournit un aperçu de vos données pour vous permettre de vérifier que vous disposez de la plage de données appropriée. Les types de données numériques sont en italique. Dans ce tutoriel, nous allons transformer les données avant le chargement.

Sélectionnez toutes les tables, puis choisissez  **Transformer les données**. Veillez à ne pas sélectionner les feuilles (étiquetées *_data*). 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-load-tables.png" alt-text="Chargez les tables dans le navigateur.":::

Vérifiez que les types de données des colonnes correspondent à ceux du tableau suivant. Pour apporter des modifications, sélectionnez une requête, puis une ou plusieurs colonnes.

:::image type="content" source="media/desktop-dimensional-model-report/power-query-change-data-types.png" alt-text="Vérifiez les types de données des colonnes.":::

Sous l’onglet **Accueil**, sélectionnez **Type de données**, puis sélectionnez le type de données approprié dans le tableau.

|Requête  |Colonne  |Type de données  |
|---------|---------|---------|
|Customer  |  CustomerKey | Nombre entier |
|Date | DateKey |    Nombre entier     |
|     | Date | Date      |
|     | MonthKey  | Nombre entier |
|Produit  | ProductKey | Nombre entier  | 
|     | Standard Cost | Nombre décimal  | 
|     | List Price | Nombre décimal  | 
|Reseller  | ResellerKey | Nombre entier  | 
|Sales   | SalesOrderLineKey | Nombre entier  | 
|     | ResellerKey  | Nombre entier  | 
|     | CustomerKey | Nombre entier  | 
|     | ProductKey  | Nombre entier  | 
|     | OrderDateKey | Nombre entier  | 
|     | DueDateKey  | Nombre entier  | 
|     | ShipDateKey | Nombre entier  | 
|     | SalesTerritoryKey | Nombre entier  | 
|     | Order Quantity   | Nombre entier  | 
|     | Unit Price  | Nombre décimal  | 
|     | Extended Amount  | Nombre décimal  | 
|     | Unit Price Discount Pct | Pourcentage  | 
|     | Product Standard Cost | Nombre décimal  | 
|     | Total Product Cost | Nombre décimal  | 
|     | Sales Amount | Nombre décimal  | 
| SalesTerritory  | SalesTerritoryKey | Nombre entier  | 
|  SalesOrder   |  SalesOrderLineKey | Nombre entier  | 

De retour sous l’onglet  **Accueil** , sélectionnez  **Fermer et appliquer**. 

:::image type="content" source="media/desktop-dimensional-model-report/power-query-close-and-apply.png" alt-text="Bouton Fermer et appliquer dans Power Query.":::

## <a name="model-your-data"></a>Modéliser vos données 

Les données que vous avez chargées sont presque prêtes pour la création de rapports. Nous allons maintenant inspecter le modèle de données et apporter quelques modifications. 

Sélectionnez **Vue du modèle** sur la gauche. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-select-model-view.png" alt-text="Sélectionnez Vue du modèle dans Power BI Desktop.":::

Votre modèle de données doit ressembler à l’image suivante, avec chaque table dans un cadre. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-1.png" alt-text="Modèle de données avec lequel commencer.":::

### <a name="create-relationships"></a>Créer des relations

Ce modèle est un *schéma en étoile* classique que vous pouvez voir à partir des entrepôts de données : Il ressemble à une étoile. Le centre de l’étoile est une table de faits. Les tables environnantes sont appelées tables de dimension ; elles sont liées à la table de faits par des relations. La table de faits contient des informations numériques sur les transactions de vente, telles que le montant des ventes et le coût standard du produit. Les dimensions fournissent un contexte qui vous permet entre autres d’analyser les éléments suivants : 

- Quel produit a été vendu... 
- à quel client.. 
- par quel revendeur... 
- dans quel secteur de vente.  

Si vous observez attentivement, vous remarquez que toutes les tables Dimension sont liées à Fact par une relation, à l’exception de la table Date. Nous allons maintenant ajouter des relations à Date. Faites glisser DateKey de la table Date vers OrderDateKey sur la table Sales. Vous avez créé une relation « un-à-plusieurs » de Date à Sales, comme indiqué par le **1** et l’astérisque * (plusieurs) aux deux extrémités de la ligne.  

Il s’agit d’une relation « un-à-plusieurs », car nous avons une ou plusieurs commandes Sales pour une Date donnée. Si chaque date n’avait qu’une seule commande Sales, il s’agirait d’une relation « un-à-un ». La petite flèche au milieu de la ligne indique la « direction de filtrage croisé ». Elle indique que vous pouvez utiliser des valeurs de la table Date pour filtrer la table Sales ; la relation vous permet donc d’analyser le moment où une commande a été passée.  

:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationship.png" alt-text="Relation entre les tables Sales et Date.":::

La table Sales contient plus d’informations sur les dates relatives aux commandes Sales, telles que la date d’échéance et la date d’expédition. Ajoutons maintenant deux relations supplémentaires à la table Date en faisant glisser : 

- DateKey vers DueDateKey 
- DateKey vers ShipDateKey 
    
:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationships-done.png" alt-text="Trois relations entre les tables Sales et Date.":::

Vous remarquez que la première relation, sur OrderDateKey, est active, ce qui est indiqué par une ligne continue. Les deux autres sont inactives, ce qui est indiqué par des lignes en pointillés. Power BI utilise la relation active par défaut pour mettre en relation Sales et Date. Ainsi, une somme de SalesAmount est calculée par date de commande, et non par date d’échéance ou date d’expédition. Vous pouvez influencer ce comportement. Consultez [Crédit supplémentaire : Écrire une mesure en DAX](#extra-credit-write-a-measure-in-dax) plus loin dans ce tutoriel.

### <a name="hide-key-columns"></a>Masquer les colonnes clés

Le schéma en étoile classique contient plusieurs clés qui contiennent les relations entre les faits et les dimensions. Normalement, nous ne souhaitons pas utiliser de colonnes clés dans nos rapports. Nous allons masquer les colonnes clés de la vue, afin que la liste des champs affiche moins de champs et que le modèle de données soit plus facile à utiliser. 

Passez en revue toutes les tables et masquez toutes les colonnes dont le nom se termine par *Key* : 

Sélectionnez l’icône **Œil** en regard de la colonne, puis choisissez **Masquer dans la vue rapport**.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-visible.png" alt-text="Colonne visible avec icône Œil.":::

Vous pouvez également sélectionner l’icône **Œil** en regard de la colonne dans le volet Propriétés.

Les champs masqués ont cette icône, un œil barré d’une ligne. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-hidden.png" alt-text="Champ avec l’icône Œil masqué.":::
 
Masquez ces champs.

|Table de charge de travail  |Colonne  |
|---------|---------|
|Customer  | CustomerKey |
|Date     | DateKey |
|     | MonthKey |
|Produit     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | CustomerKey  |
|     | DueDateKey |
|     | OrderDateKey |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | ShipDateKey        |
| SalesOrder    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |

Votre modèle de données doit maintenant ressembler à celui-ci, avec des relations entre Sales et toutes les autres tables, et tous les champs clés masqués : 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-2-hidden-columns.png" alt-text="Modèle de données avec colonnes clés masquées.":::

### <a name="create-hierarchies"></a>Créer des hiérarchies

Maintenant que notre modèle de données est plus facile à consommer en raison des colonnes masquées, nous pouvons ajouter quelques *hiérarchies* afin de simplifier encore davantage l’utilisation du modèle. Les hiérarchies facilitent la navigation parmi les regroupements. Par exemple, les villes sont dans un état ou une province, qui se trouve dans un pays ou une région. 

Créez les hiérarchies suivantes. 

1. Cliquez avec le bouton droit sur le champ de niveau le plus élevé, ou le moins précis, de la hiérarchie, puis choisissez **Créer une hiérarchie**. 

1. Dans le volet **Propriétés**, définissez le **Nom** de la hiérarchie et définissez les niveaux. 

1. Ensuite, sélectionnez **Appliquer les changements de niveau**. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-hierarchy-properties.png" alt-text="Volet Propriétés de la hiérarchie.":::

Vous pouvez également renommer des niveaux dans une hiérarchie dans le volet Propriétés après les avoir ajoutés. Vous devez renommer les niveaux Year et Quarter de la hiérarchie Fiscal dans la table Date. 

Voici les hiérarchies que vous devez créer.

| Table de charge de travail |Nom de la hiérarchie |Niveaux  |
|---------|---------|---------|
|Customer     | Geography   | Pays-Région  |
|     | | État-Province  |
|     |         | City |
|Row4     |         | Code postal |
|Row5     |         | Client   |
|Date     | Fiscal  | Année (Exercice fiscal)  |
|     |         | Trimestre (Trimestre fiscal) |
|     |         | Month |
|     |         | Date |
| Product  | Produits | Category |
|     |         | Sous-catégorie |
|     |         | Modèle |
|     |         | Product |
| Reseller   | Geography | Pays-Région |
|     |         | État-Province |
|     |         | City  |
|     |         | Code postal  |
|     |         | Reseller |
| SalesOrder  | Sales Orders | Commande client |
|     |         | Sales Order Line |
| SalesTerritory    | Sales Territories | Group |
|     |         | Country |
|     |         | Région |
 
Votre modèle de données doit maintenant ressembler au suivant. Il a les mêmes tables, mais chaque table de dimension contient une hiérarchie : 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-3-added-hierarchies.png" alt-text="Modèle de données avec tables de dimension avec hiérarchies.":::

### <a name="rename-tables"></a>Renommer des tables

Pour terminer la modélisation, nous allons renommer les tables suivantes dans le volet Propriétés : 

|Ancien nom de table  |Nouveau nom de table  |
|---------|---------|
|SalesTerritory    |  Secteur de vente   |
|SalesOrder  |  Commande client   |

Cette étape est nécessaire, car les noms de tables Excel ne peuvent pas contenir d’espaces.

Votre modèle de données final est maintenant prêt.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-4-renamed-tables.png" alt-text="Modèle de données terminé avec tables renommées.":::

## <a name="extra-credit-write-a-measure-in-dax"></a>Crédit supplémentaire : Écrire une mesure en DAX 

L’écriture de *mesures* dans le langage de formule DAX est super puissante pour la modélisation des données. Il y a beaucoup à [apprendre sur DAX dans la documentation de Power BI](/dax/). Pour le moment, nous allons écrire une mesure de base qui calcule le montant total des ventes par date d’échéance sur la commande au lieu de la date de commande par défaut. Cette mesure utilise la [fonction USERELATIONSHIP](/dax/userelationship-function-dax) pour activer la relation entre Sales et Date sur DueDate pour le contexte de la mesure. Elle utilise ensuite [CALCULATE](/dax/calculate-function-dax) pour additionner le montant des ventes dans ce contexte.

1. Sélectionnez Vue de données sur la gauche. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-open-data-view.png" alt-text="Sélectionnez Vue de données sur la gauche.":::

1. Sélectionnez la table Sales dans la liste Champs.

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-select-sales-table.png" alt-text="Sélectionnez la table Sales dans la liste Champs.":::

1. Dans le ruban  **Accueil**, sélectionnez  **Nouvelle mesure**. 

1. Sélectionnez ou tapez cette mesure pour calculer le montant total des ventes par date d’échéance sur la commande au lieu de la date de commande par défaut.

    ```dax
    Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))
    ```

1. Cochez la case pour valider. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-adding-a-dax-measure.png" alt-text="Cochez la case pour valider la mesure DAX.":::

## <a name="build-your-report"></a>Créer votre rapport 

Maintenant que vous avez modélisé vos données, il est temps de créer votre rapport. Accédez à la vue Rapport. Dans le volet Champs à droite figurent les champs du modèle de données que vous avez créé.

Nous allons créer le rapport final, un visuel à la fois. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report-with-numbers.png" alt-text="Rapport terminé, avec des numéros marquant chaque visuel":::

### <a name="visual-1-add-a-title"></a>Visuel 1 : Ajouter un titre 

1. Dans le ruban **Insertion**, sélectionnez **Zone de texte**. Tapez « Rapport de synthèse – Rapport des ventes ». 

1. Sélectionnez le texte que vous avez tapé. Affectez la valeur **20** à la taille de police et appliquez la mise en **Gras**. 

    :::image type="content" source="media/desktop-dimensional-model-report/executive-summary-text-box.png" alt-text="Mettez en forme le texte du rapport de synthèse.":::

1. Dans le volet Visualisations, basculez l’**Arrière-plan** sur **Désactivé**. 

1. Redimensionnez la zone pour qu’elle tienne sur une seule ligne. 

### <a name="visual-2-sales-amount-by-date"></a>Visuel 2 : Montant des ventes par date 

Maintenant, nous allons créer un graphique en courbes pour voir le mois et l’année où le montant des ventes a été le plus élevé.

1. À partir du volet Champs, faites glisser le champ **Sales Amount** de la table **Sales** vers une zone vide sur le canevas de rapport. Par défaut, Power BI affiche un histogramme avec une colonne, Sales Amount. 

1. Faites glisser le champ **Month** à partir de la hiérarchie **Fiscal** dans la table **Date** et déposez-le sur l’histogramme. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year.png" alt-text="Créez un histogramme avec une colonne pour chaque année.":::

1. Dans la section **Champs** du volet Visualisations, supprimez les champs **Year** et **Quarter**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-remove-year-and-quarter.png" alt-text="Dans la section Champs du volet Visualisations, supprimez les champs Year et Quarter.":::

1. Dans le volet Visualisations, choisissez le type de visualisation **Graphique en aires**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-change-to-area.png" alt-text="Remplacez l’histogramme par un graphique en aires.":::

1. Si vous avez ajouté la mesure DAX dans le crédit supplémentaire ci-dessus, ajoutez-la également aux **Valeurs**. 
1. Ouvrez le volet Format, ouvrez Couleurs des données et remplacez la couleur de **Sales Amount by Due Date** par une couleur plus contrastée, telle que le rouge.

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-add-DAX-measure.png" alt-text="Sales Amount by Due Date représentée sous forme de graphique en aires.":::

    Comme vous pouvez le voir, Sales Amount by Due Date est légèrement inférieur à Sales Amount. Cela prouve que le rapport utilise la relation entre les tables Sales et Date qui utilise DueDateKey. 

 

### <a name="visual-3-order-quantity-by-reseller-country"></a>Visuel 3 : Quantité de commandes par pays du revendeur 

Nous allons maintenant créer une carte pour voir dans quel pays les revendeurs ont la quantité de commandes la plus élevée.

1. À partir du volet Champs, faites glisser le champ **Country-Region** de la table **Reseller** vers une zone vide de votre canevas de rapport. Power BI crée une carte. 

1. Faites glisser le champ **Order Quantity** à partir de la table **Sales** et déposez-le sur la carte. Vérifiez que **Country-Region** se trouve dans le puits **Emplacement** et **Order Quantity** dans le puits **Taille**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-order-quantity-by-reseller-country.png" alt-text="Carte de la quantité de commandes par pays/région.":::

### <a name="visual-4-sales-amount-by-product-category-and-reseller-business-type"></a>Visuel 4 : Montant des ventes par catégorie de produit et type de revendeur 

Ensuite, nous allons créer un histogramme pour savoir quels produits sont vendus par quel type de revendeur.

1. Faites glisser les deux graphiques que vous avez créés pour qu’ils soient côte à côte dans la moitié supérieure du canevas. Conservez un peu d’espace sur le côté gauche du canevas. 

1. Sélectionnez une zone vide dans la moitié inférieure de votre canevas de rapport. 

1. Dans le volet Champs, sélectionnez **Sales Amount** à partir de **Sales**, **Product Category** à partir de **Product** et **Business Type** à partir de **Reseller**. 

    Power BI crée automatiquement un histogramme groupé. Changez la visualisation en **Matrice**  : 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-change-to-matrix.png" alt-text="Remplacez l’histogramme groupé par une matrice.":::

1. Avec la matrice toujours sélectionnée, dans le volet Filtres, sous **Business Type**, cliquez sur **Sélectionner tout**, puis décochez la case **[Not Applicable]** . 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-filter-not-applicable.png" alt-text="Excluez le type d’entreprise Not Applicable.":::

1. Faites glisser la matrice afin qu’elle soit suffisamment large pour remplir l’espace sous les deux graphiques du haut. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-increase-width.png" alt-text="Élargissez la matrice pour qu’elle remplisse le rapport.":::

1. Dans le volet Mise en forme de la matrice, ouvrez la section **Mise en forme conditionnelle** et activez les **Barres de données**. Sélectionnez **Contrôles avancés** et définissez une couleur plus claire pour la barre positive. Sélectionnez **OK**. 

1. Augmentez la largeur de la colonne Sales Amount pour qu’elle couvre l’ensemble de la zone. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-add-databars.png" alt-text="Matrice avec barres de données pour Sales Amount.":::

Il semble que les vélos aient un montant de ventes plus élevé et que les revendeurs à valeur ajoutée (Value Added Resellers) vendent le plus, suivis de près par les entrepôts (Warehouses). Pour les pièces (Components), les entrepôts vendent plus que les revendeurs à valeur ajoutée. 

 

### <a name="visual-5-fiscal-calendar-slicer"></a>Visuel 5 : segment de calendrier Fiscal 

Les segments sont un outil précieux pour filtrer les visuels d’une page de rapport à une sélection spécifique. Ici, nous pouvons créer un segment pour examiner en détail les performances de chaque mois, trimestre et année. 

1. Dans le volet Champs, sélectionnez la hiérarchie **Fiscal** à partir de la table **Date** et faites-la glisser vers la zone vide à gauche du canevas. 

1. Dans le volet Visualisations , choisissez **Segment**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer.png" alt-text="Ajoutez un segment de calendrier de ventes au rapport.":::

1. Dans la section Champs du volet Visualisations, supprimez **Quarter** et **Date** afin qu’il ne reste que **Year** et **Month**. 
 
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer-remove-quarter-and-date.png" alt-text="Supprimez Quarter et Date du segment Fiscal.":::

Maintenant, si votre responsable demande à voir uniquement les données d’un mois spécifique, vous pouvez utiliser le segment pour basculer d’une année à une autre ou entre les mois de chaque année. 

## <a name="extra-credit-format-the-report"></a>Crédit supplémentaire : Mettre en forme le rapport 

Si vous souhaitez appliquer une légère mise en forme à ce rapport pour le rendre un peu plus attrayant, voici quelques étapes simples à effectuer. 

### <a name="theme"></a>Thème 

- Dans le ruban  **Vue**, sélectionnez **Thèmes**, puis remplacez le thème par  **Executive**. 

    :::image type="content" source="media/desktop-dimensional-model-report/formatting-report-change-theme.png" alt-text="Choisissez le thème Executive.":::

### <a name="spruce-up-the-visuals"></a>Embellir les visuels 

Apportez les modifications suivantes sous l’onglet  **Format** dans le volet Visualisations. 

:::image type="content" source="media/desktop-dimensional-model-report/formatting-report-formatting-pane.png" alt-text="Capture d’écran de l’onglet Format dans le volet Visualisations.":::

**Visuel 2, Sales Amount by Date**

1. Sélectionnez Visuel 2, Sales Amount by Date. 
1. Dans la section  **Titre**, si vous n’avez pas ajouté la mesure DAX, remplacez le texte **Titre** par « Montant des ventes par date de commande ». 

    Si vous avez ajouté la mesure DAX, remplacez **Texte du titre** par « Montant des ventes par date de commande / échéance ». 

1. Affectez la valeur  **16 pt** à la **Taille du texte**. 
1. Basculez **Ombre** sur **Activé**. 

**Visuel 3, Quantité de commandes par pays du revendeur**

1. Sélectionnez Visuel 3, Quantité de commandes par pays du revendeur. 
1. Dans la section  **Styles de carte**, changez le  **Thème** en **Nuances de gris**. 
1. Dans la section  **Titre**, remplacez **Texte du titre** par « Quantité de commandes par pays du revendeur ».
1. Affectez la valeur  **16** pt à la **Taille du texte**. 
1. Basculez **Ombre** sur **Activé**.  

**Visuel 4, Montant des ventes par catégorie de produit et type de revendeur**

1. Sélectionnez Visuel 4, Montant des ventes par catégorie de produit et type de revendeur. 
1. Dans la section  **Titre**, remplacez **Texte du titre** par « Montant des ventes par catégorie de produit et type de revendeur ».
1. Affectez la valeur  **16** pt à la **Taille du texte**. 
1. Basculez **Ombre** sur **Activé**. 

**Visuel 5, segment de calendrier fiscal**

1. Sélectionnez Visuel 5, segment de calendrier Fiscal.
1. Dans la section  **Contrôles de sélection**, basculez  **Afficher l’option « Tout sélectionner »** sur **Activé**. 
1. Dans la section  **En-tête de segment**, affectez la valeur  **16 pt** à **Taille du texte**. 

### <a name="add-a-background-shape-for-the-title"></a>Ajouter une forme d’arrière-plan pour le titre 

1. Dans le ruban  **Insérer**, sélectionnez **Formes** > **Rectangle**. 
1. Placez-le en haut de la page et étirez-le pour qu’il occupe toute la largeur de la page et la hauteur du titre. 
1. Dans le volet **Format de la forme**, dans la section  **Ligne**, affectez la valeur  **100%** à la  **Transparence**. 
1. Dans la section **Remplissage**, remplacez **Couleur de remplissage** par **Couleur de thème 5 #6B91C9 (bleu)** . 
1. Sous l’onglet  **Format**, sélectionnez  **Reculer** > **Mettre en arrière-plan**. 
1. Sélectionnez le texte du visuel 1, le titre, et remplacez la **Couleur de la police** par **Blanc**. 

## <a name="finished-report"></a>Rapport terminé 

Sélectionnez **FY2019** dans le segment.

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Votre rapport final.":::

En résumé, ce rapport répond aux principales questions de votre responsable : 

- Quel jour y a-t-il eu le plus de ventes en février 2019 ? 
    Le 25 février, avec un montant de ventes de $253 915,47. 

- Dans quel pays la société rencontre-t-elle le plus de succès ? 
    Aux États-Unis, avec 132 748 commandes. 

- Quelles sont les catégories de produits et les types de revendeurs dans lesquels l’entreprise doit continuer à investir ? 
    L’entreprise doit continuer à investir dans la catégorie Bikes et dans les types de revendeurs Value Added Reseller et Warehouse. 

## <a name="save-your-report"></a>Enregistrer votre rapport 

- Dans le menu **Fichier**, sélectionnez **Enregistrer**. 


## <a name="publish-to-the-power-bi-service-to-share"></a>Publier sur le service Power BI en vue du partage 

Pour partager votre rapport avec votre responsable et vos collègues, publiez-le sur le service Power BI. Quand vous partagez avec des collègues disposant d’un compte Power BI, ils peuvent interagir avec votre rapport, mais ne peuvent pas enregistrer les modifications.

1. Dans Power BI Desktop, dans le ruban **Accueil**, sélectionnez **Publier**. 
1. Vous devrez peut-être vous connecter au service Power BI. Si vous n’avez pas encore de compte, [demandez un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web). 

1. Sélectionnez une destination, par exemple Mon espace de travail dans le service Power BI >  **Sélectionner**. 

1. Sélectionnez **Ouvrir « nom_de_votre_fichier » dans Power BI**. Votre rapport s’ouvre dans le navigateur. 

1. Sélectionnez **Partager** en haut du rapport pour le partager avec d’autres utilisateurs.

## <a name="next-steps"></a>Étapes suivantes 

- Télécharger le [fichier .pbix Power BI terminé](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)
- En savoir plus sur [DAX et la modélisation de données dans Power BI Desktop](/learn/modules/dax-power-bi-models/)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
