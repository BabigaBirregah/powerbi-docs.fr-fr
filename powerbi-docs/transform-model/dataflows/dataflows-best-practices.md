---
title: Bonnes pratiques pour les dataflows
description: Collection de liens vers les bonnes pratiques et de conseils pour les dataflows
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 116458c094159cbeeadaf2e955744759e4648220
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097958"
---
# <a name="dataflows-best-practices"></a>Bonnes pratiques pour les dataflows

Les **dataflows** Power BI constituent une solution de préparation des données pour les entreprises, qui permet de disposer d’un écosystème de données prêtes à être consommées, réutilisées et intégrées. Cet article liste les bonnes pratiques et fournit des liens vers d’autres articles et informations pour vous aider à comprendre et utiliser les dataflows au maximum de leur potentiel.

## <a name="dataflows-across-the-power-platform"></a>Dataflows dans Power Platform

Les dataflows peuvent être utilisés sur diverses technologies Power Platform, telles que Power Query, Microsoft Dynamics 365 et d’autres offres Microsoft. Pour plus d’informations sur le fonctionnement des dataflows sur Power Platform, consultez [Utilisation de dataflows dans les produits Microsoft](https://docs.microsoft.com/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365).


## <a name="dataflows-best-practices-table-and-links"></a>Tableau et liens des bonnes pratiques pour les dataflows

Le tableau suivant fournit une collection de liens vers des articles qui décrivent les bonnes pratiques pour la création ou l’utilisation de dataflows. Les liens incluent des informations sur le développement d’une logique métier, le développement de dataflows complexes, la réutilisation de dataflows et le mode de mise à l’échelle de l’entreprise avec vos dataflows.


|**Rubrique**  |**Domaine de conseil**  |**Lien vers un article ou contenu**  |
|---------|---------|---------|
|Power Query     | Trucs et astuces pour tirer le meilleur parti de votre expérience de data wrangling        |[Bonnes pratiques liées à Power Query](https://docs.microsoft.com/power-query/best-practices)        |
|Exploitation des entités calculées     |L’utilisation d’entités calculées dans un dataflow est bénéfique pour les performances.         |[Scénarios d’entités calculées](https://docs.microsoft.com/power-query/dataflows/computed-entities-scenarios)         |
|Développement de dataflows complexes     |Modèles pour le développement de dataflows performants à grande échelle         |[Dataflows complexes](https://docs.microsoft.com/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|Réutilisation des dataflows     |Modèles, conseils et cas d’usage         |[Réutilisation des dataflows](https://docs.microsoft.com/power-query/dataflows/best-practices-reusing-dataflows)         |
|Implémentations à grande échelle     |Utilisation à grande échelle et conseils pour compléter une architecture d’entreprise         |[Entreposage de données à l’aide de dataflows](https://docs.microsoft.com/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|Exploitation du calcul amélioré     |Possibilité d’améliorer les performances des dataflows jusqu’à 25 fois         |[Moteur de calcul avancé](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|Optimisation de vos paramètres de charge de travail     |Tirer le meilleur parti de l’infrastructure de vos dataflows en comprenant les leviers que vous pouvez tirer pour optimiser les performances         |[Configuration de la charge de travail des dataflows](dataflows-premium-workload-configuration.md)         |
|Jointure et développement de tables     |Création de jointures performantes         |[Optimiser les opérations de développement de tables](https://docs.microsoft.com/power-query/optimize-expanding-table-columns)         |
|Instructions de pliage des requêtes     |Accélération des transformations à l’aide du système source         |[Pliage de requêtes](https://docs.microsoft.com/power-query/power-query-folding)         |
|Utilisation du profilage des données     |Comprendre la qualité, la distribution et le profil des colonnes         |[Outils de profilage des données](https://docs.microsoft.com/power-query/data-profiling-tools)         |
|Implémentation de la gestion des erreurs     |Développement de dataflows robustes résistants aux erreurs d’actualisation avec des suggestions         |[Modèles pour les erreurs courantes](https://docs.microsoft.com/power-query/dealing-with-errors)  </br> [Gestion des erreurs complexe](https://docs.microsoft.com/power-query/error-handling)      |
|Utiliser la vue Schéma      |Améliorer l’expérience de création quand vous travaillez avec un tableau large et effectuez des opérations au niveau du schéma         |[Vue Schéma](https://docs.microsoft.com/power-query/schema-view)         |
|Entités liées      |Réutilisation et référencement des transformations         |[Entités liées](https://docs.microsoft.com/power-query/dataflows/linked-entities)         |
|Actualisation incrémentielle      |Charger les données les plus récentes ou changées plutôt qu’effectuer un rechargement complet         |[Actualisation incrémentielle](https://docs.microsoft.com/power-query/dataflows/incremental-refresh)         |
|||


        
## <a name="next-steps"></a>Étapes suivantes

Les articles suivants vous permettront d’en savoir plus sur les dataflows et Power BI :

* [Introduction aux dataflows et à la préparation des données en libre-service](dataflows-introduction-self-service.md)
* [Création d’un flux de données](dataflows-create.md)
* [Configurer et consommer un dataflow](dataflows-configure-consume.md)
* [Fonctionnalités Premium des dataflows](dataflows-premium-features.md)
* [Configuration du stockage de dataflows pour utiliser Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [IA et dataflows](dataflows-machine-learning-integration.md)
* [Considérations et limitations des dataflows](dataflows-features-limitations.md)