---
title: Ajouter un menu contextuel au visuel Power BI dans l’analytique incorporée Power BI pour de meilleurs insights via la BI incorporée
description: Découvrez comment ajouter un menu contextuel à un visuel Power BI. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1c19ba94588628e002cdb9e65f59bd4182020e1c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888693"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Ajouter un menu contextuel à un visuel Power BI

Vous pouvez utiliser `selectionManager.showContextMenu()` avec les paramètres `selectionId` et une position (comme objet `{x:, y:}`) afin que Power BI affiche un menu contextuel pour votre visuel.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` a été introduit dans Visuals API 2.2.0.

Généralement, cet élément est ajouté en tant qu'événement de clic droit (ou d’appui prolongé sur les appareils tactiles). Le menu contextuel a été ajouté à l’exemple BarChart pour référence :

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
