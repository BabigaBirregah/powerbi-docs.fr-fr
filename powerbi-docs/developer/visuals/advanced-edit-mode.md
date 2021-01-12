---
title: Mode d’édition avancée dans les visuels Power BI de l’analytique incorporée Power BI pour de meilleurs insights via la BI incorporée
description: Cet article explique comment définir des contrôles d’interface utilisateur avancés dans les visuels Power BI. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 02f02f23d3dfd7ec514e17d1bab17be715e9cd7d
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889130"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Mode d’édition avancé dans les visuels Power BI

Si vous souhaitez inclure des contrôles d’interface utilisateur avancés dans votre visuel Power BI, vous pouvez utiliser le mode d’édition avancé. Quand vous êtes en mode d’édition de rapport, vous sélectionnez un bouton **Modifier** pour définir le mode d’édition sur **Avancé**. Le visuel peut utiliser l’indicateur `EditMode`pour déterminer s’il doit afficher ce contrôle d’interface utilisateur.

Par défaut, le visuel ne prend pas en charge le mode d’édition avancé. Si un comportement différent est requis, vous pouvez le spécifier explicitement dans le fichier *capabilities.json* du visuel, en définissant la propriété `advancedEditModeSupport`.

Les valeurs possibles sont les suivantes :

- `0` - NotSupported

- `1` - SupportedNoAction

- `2` - SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>Entrer le mode d’édition avancé

Un bouton **Modifier** s’affiche dans les cas suivants :

* La propriété `advancedEditModeSupport` est définie dans le fichier *capabilities.json* sur `SupportedNoAction` ou `SupportedInFocus`.

* Le visuel est affiché en mode d’édition de rapport.

Si la propriété `advancedEditModeSupport` n’est pas spécifiée dans le fichier *capabilities.json*, ou si elle y est définie sur `NotSupported`, le bouton **Modifier** n’est pas affiché.

![Passer au mode Édition](media/advanced-edit-mode/edit-mode.png)

Quand vous sélectionnez **Modifier**, le visuel obtient un appel update() où EditMode est défini sur `Advanced`. Selon la valeur qui est définie dans le fichier *capabilities.json*, les actions suivantes se produisent :

* `SupportedNoAction` : aucune action supplémentaire n’est requise par l’hôte.
* `SupportedInFocus` : l’hôte affiche le visuel en mode Focus.

## <a name="exit-advanced-edit-mode"></a>Quitter le mode d’édition avancé

Le bouton **Retour au rapport** est affiché dans le cas suivant :

* La propriété `advancedEditModeSupport` est définie dans le fichier *capabilities.json* sur `SupportedInFocus`.
