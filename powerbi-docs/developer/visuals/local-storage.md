---
title: API de stockage local dans les visuels Power BI de l’analytique incorporée Power BI pour de meilleurs insights via la BI incorporée
description: L’article explique comment utiliser l’API de visuels Power BI pour accéder au stockage local du navigateur. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 01/21/2019
ms.openlocfilehash: abec68c5622d3dcd96746148ed7a6da4f06c8ec0
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888187"
---
# <a name="local-storage-api"></a>API de stockage local

L’API de stockage local est une API qu’un visuel personnalisé peut utiliser pour demander à l’hôte d’enregistrer ou de charger des données à partir du stockage de l’appareil. Elle est isolée dans le sens où il existe une séparation de l’accès de stockage entre les différents types de visuels.

## <a name="sample"></a>Exemple

Si le visuel personnalisé doit augmenter un compteur chaque fois que la méthode de mise à jour est appelée, mais que la valeur du compteur doit également être conservée et ne pas être réinitialisée à chaque démarrage du visuel :

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Limites et problèmes connus

L’API de stockage local n’est pas activée par défaut pour les visuels Power BI. Si vous voulez l’activer pour votre visuel Power BI, envoyez une demande au support technique des visuels Power BI, à l’adresse `pbicvsupport@microsoft.com`.  
**Notez que votre visuel doit être disponible dans [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) et être [certifié](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
