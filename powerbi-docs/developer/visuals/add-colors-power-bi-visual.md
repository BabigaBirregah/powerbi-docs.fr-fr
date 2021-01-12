---
title: Ajouter des couleurs à vos visuels Power BI dans l’analytique incorporée Power BI pour de meilleurs insights via la BI incorporée
description: Cet article explique comment ajouter des couleurs à vos visuels Power BI et comment gérer des points de données pour un visuel avec des couleurs. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: e6b6fb1dbc1397b93ac12692c8610e6f36d0b8bf
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887980"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Ajouter des couleurs à vos visuels Power BI

Cet article explique comment ajouter des couleurs à vos visuels et comment gérer des points de données pour un visuel à couleurs.

`IVisualHost` expose la couleur comme un de ses services.
L’exemple de code de cet article modifie le [visuel SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
Pour obtenir le code source, consultez [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts).

Pour essayer de créer des visuels, consultez [Développement d’un visuel de carte ronde Power BI](develop-circle-card.md).

## <a name="add-color-to-data-points"></a>Ajouter de la couleur aux points de données

Une couleur différente représente chaque point de données.
Ajoutez la couleur à l’interface `BarChartDataPoint`, comme dans l’exemple suivant :

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>Utiliser le service de palette de couleurs

Le service `colorPalette` gère les couleurs utilisées dans votre visuel.
Une instance du service est disponible sur `IVisualHost`.

Définissez-la dans la méthode `update`.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Affecter une couleur à des points de données

Ensuite, spécifiez `dataPoints`.
Dans cet exemple, chacun des `dataPoints` comprend la valeur, la catégorie et la couleur.
`dataPoints` peut également inclure d’autres propriétés.

Dans `SampleBarChart`, la méthode `visualTransform` encapsule le calcul `dataPoints`.
Cette méthode fait partie du ViewModel de graphique à barres.
Étant donné que la méthode itère à travers le calcul de `dataPoints` dans `visualTransform`, il s’agit de l’emplacement idéal pour attribuer des couleurs, comme dans le code suivant :

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Appliquez ensuite les données de `dataPoints` sur la sélection [d3](https://d3js.org/) `barSelection` à l’intérieur de la méthode `update` :

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les visuels Power BI, consultez [Fonctionnalités et propriétés des visuels Power BI](capabilities.md).

Pour en savoir plus sur le développement de visuels Power BI visuels, consultez [Comment déboguer des visuels Power BI](visuals-how-to-debug.md) et [Résoudre les problèmes de visuels Power BI](power-bi-custom-visuals-troubleshoot.md).
