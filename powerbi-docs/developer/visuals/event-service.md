---
title: Afficher des événements dans les visuels Power BI de l’analytique incorporée Power BI pour de meilleurs insights via la BI incorporée
description: Les visuels Power BI peuvent notifier Power BI qu’ils sont prêts à être exportés vers PowerPoint ou PDF. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 77ed686b78a96717193e594e9f846d4204d8b5e8
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885082"
---
# <a name="render-events-in-power-bi-visuals"></a>Afficher des événements dans des visuels Power BI

La nouvelle API est constituée de trois méthodes (`started`, `finished` ou `failed`) qui doivent être appelées pendant le rendu.

Quand le rendu démarre, le code de visuel Power BI appelle la méthode `renderingStarted` pour signaler que le processus de rendu a démarré.

Si le rendu s’est terminé avec succès, le code de visuel Power BI appelle immédiatement la méthode `renderingFinished` pour signaler aux écouteurs (principalement *Exporter au format PDF* et *Exporter vers PowerPoint*) que l’image du visuel est prête à être exportée.

Si un problème se produit au cours du processus, le rendu du visuel Power BI échoue. Pour signaler aux écouteurs que le processus de rendu n’a pas été terminé, le code de visuel Power BI doit appeler la méthode `renderingFailed`. Cette méthode fournit également une chaîne facultative pour fournir la raison de l’échec.

## <a name="usage"></a>Usage

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Exemple : Le visuel n’affiche aucune animation

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>Exemple : Le visuel affiche les animations

Si le visuel a des animations ou des fonctions asynchrones pour le rendu, la méthode `renderingFinished` doit être appelée après l’animation ou au sein de la fonction asynchrone.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Rendu des événements pour la certification visuelle

L’une des exigences de la certification des visuels est la prise en charge du rendu des événements par le visuel. Pour plus d’informations, consultez les [critères de certification](power-bi-custom-visuals-certified.md#certification-requirements).