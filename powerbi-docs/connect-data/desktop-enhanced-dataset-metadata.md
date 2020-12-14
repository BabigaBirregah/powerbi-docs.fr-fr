---
title: Utilisation de métadonnées de jeu de données avancées dans Power BI Desktop
description: Cet article explique comment utiliser des métadonnées de jeu de données avancées dans Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 661e50617094d396e8beb887ac0e4a27c28c2ca7
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906962"
---
# <a name="using-enhanced-dataset-metadata"></a>Utilisation de métadonnées de jeu de données avancées

Lorsque Power BI Desktop crée des rapports, il crée également des métadonnées de jeu de données dans les fichiers PBIX et PBIT correspondants. Auparavant, ces métadonnées étaient stockées dans un format spécifique à Power BI Desktop. Les métadonnées utilisaient des expressions M et des sources de données encodées en base 64. Power BI fait des hypothèses sur la façon dont les métadonnées ont été stockées.

Avec la publication de la fonctionnalité de **métadonnées de jeu de données avancées**, un grand nombre de ces limitations sont supprimées. À l’ouverture, les fichiers PBIX sont automatiquement mis à niveau vers les métadonnées avancées. Avec les **métadonnées de jeu de données avancées**, les métadonnées créées par Power BI Desktop suivent un format similaire à celui des modèles tabulaires Analysis Services, selon le [modèle d’objet tabulaire](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


La fonctionnalité de **métadonnées de jeu de données améliorées** est stratégique et fondamentale. Les fonctionnalités futures de Power BI seront basées sur ses métadonnées. Ces autres fonctionnalités tirent parti des métadonnées de jeu de données améliorées :

- [Lecture/écriture de XMLA](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) pour la gestion des jeux de données Power BI
- Migration des charges de travail Analysis Services vers Power BI pour tirer parti des fonctionnalités de nouvelle génération.

## <a name="limitations"></a>Limites
Avant la prise en charge des métadonnées améliorées, pour les connexions SQL Server, Oracle, Teradata et HANA héritées, Power BI Desktop ajoutait une requête native au modèle de données. Cette requête est utilisée par les modèles de données du service Power BI. Avec la prise en charge des métadonnées améliorées, le modèle de données du service Power BI regénère la requête native au moment de l’exécution. Elle n’utilise pas la requête qui avait été créée par Power BI Desktop. Dans la plupart des cas, cette récupération se résout correctement d’elle-même, mais certaines transformations ne fonctionneront pas sans une lecture des données sous-jacentes. Vous verrez peut-être des erreurs dans des rapports qui fonctionnaient avant. Par exemple, l’erreur va indiquer : 

« Impossible de convertir une requête M de la table « Dimension City » en requête source native. Réessayez plus tard ou contactez le support. Si vous contactez le support, fournissez ces informations. » 

Vous pouvez corriger vos requêtes à trois endroits différents dans Power BI Desktop :

- Quand vous appliquez des modifications ou que vous effectuez une actualisation.
- Dans une barre d’avertissement de l’éditeur Power Query vous informant que l’expression n’a pas pu être pliée pour la source de données.
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="Capture d’écran du message Appliquer les modifications de requête : Nous n’avons pas pu plier l’expression sur la source de données.":::
- Quand vous effectuez des évaluations à l’ouverture d’un rapport pour vérifier si vous avez des requêtes non prises en charge. L’exécution de ces évaluations peut avoir des implications en termes de performances.


## <a name="next-steps"></a>Étapes suivantes

Power BI Desktop permet d’effectuer des tâches très diverses. Pour plus d’informations sur ses fonctionnalités, passez en revue les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](../fundamentals/desktop-what-is-desktop.md)
* [Nouveautés dans Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Vue d’ensemble des requêtes dans Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Types de données dans Power BI Desktop](desktop-data-types.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
