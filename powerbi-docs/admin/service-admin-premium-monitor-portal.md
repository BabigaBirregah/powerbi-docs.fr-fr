---
title: Superviser les capacités Power BI Premium avec le portail d’administration
description: Utilisez le portail d’administration Power BI pour superviser vos capacités Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: b6f6b819b5c31f655d0c0dc43d8852cb34b5a7a2
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512053"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Superviser les capacités dans le portail d’administration

L’onglet **Intégrité** de la zone **Paramètres de capacité** dans le portail d’administration fournit un résumé des métriques concernant votre capacité et les charges de travail activées.  

![Onglet Intégrité de la capacité dans le portail](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Si vous avez besoin de métriques plus complètes, utilisez l’application [Métriques de capacité Power BI Premium](service-admin-premium-monitor-capacity.md). L’application fournit des fonctionnalités d’exploration et de filtrage, et les métriques les plus détaillées pour quasiment tous les aspects affectant les performances de capacité. Pour en savoir plus, consultez [Superviser les capacités Premium avec l’application](service-admin-premium-monitor-capacity.md).

> [!IMPORTANT]
> Si votre capacité Power BI Premium subit une utilisation intensive des ressources entraînant des problèmes de performances ou de fiabilité, vous pouvez recevoir des e-mails de notification pour identifier et résoudre le problème. Il peut s’agir d’un moyen simplifié de dépanner les capacités surchargées. Pour plus d’informations, consultez les [notifications de capacité et de fiabilité](service-interruption-notifications.md#capacity-and-reliability-notifications).

> [!NOTE]
> Une nouvelle version de Power BI Premium a récemment été publiée. Celle-ci, appelée **Premium Gen2**, est actuellement en préversion. Premium Gen2 vise à simplifier la gestion des capacités Premium et à réduire la charge de gestion. Pour plus d’informations, consultez [Power BI Premium Generation 2 (préversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="system-metrics"></a>Métriques du système

Sous l’onglet **Intégrité**, au niveau le plus élevé, l’utilisation du processeur et l’utilisation de la mémoire fournissent un aperçu rapide des métriques les plus importantes pour la capacité. Ces métriques sont cumulatives et incluent toutes les charges de travail activées pour la capacité.

| **Métrique** | **Description** |
| --- | --- |
| UTILISATION DU PROCESSEUR | Utilisation moyenne du processeur, en pourcentage par rapport au total disponible. |
| UTILISATION DE LA MÉMOIRE | Utilisation moyenne de la mémoire en gigaoctets (Go).|

## <a name="workload-metrics"></a>Métriques de charge de travail

Pour chaque charge de travail activée pour la capacité. L’utilisation du processeur et l’utilisation de la mémoire sont affichées.

| **Métrique** | **Description** |
| --- | --- |
| UTILISATION DU PROCESSEUR | Utilisation moyenne du processeur, en pourcentage par rapport au total disponible. |
| UTILISATION DE LA MÉMOIRE | Utilisation moyenne de la mémoire en gigaoctets (Go).|

### <a name="detailed-workload-metrics"></a>Métriques de charge de travail détaillées

Chaque charge de travail présente des métriques supplémentaires. Le type des métriques indiquées dépend de la charge de travail. Pour voir les métriques détaillées d’une charge de travail, cliquez sur la flèche de développement (bas).

![Développement de l’intégrité de la charge de travail](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Dataflows

##### <a name="dataflow-operations"></a>Opérations de dataflow

| **Métrique** | **Description** |
| --- | --- |
| Nombre total | total des actualisations pour chaque flux de données. |
| Nombre de succès | Total des actualisations réussies pour chaque dataflow.|
| Durée moyenne (min) | durée moyenne d’actualisation du flux de données, en minutes |
| Durée maximale (min) | durée de l’actualisation la plus longue en cours d’exécution pour le flux de données, en minutes. |
| Temps d’attente moyen (min) | délai moyen entre l’heure planifiée et le début d’une actualisation du flux de données, en minutes. |
| Temps d’attente maximal (min) | délai d’attente maximal du flux de données, en minutes.  |

#### <a name="datasets"></a>Jeux de données

##### <a name="refresh"></a>Actualiser

| **Métrique** | **Description** |
| --- | --- |
| Nombre total | nombre total d’actualisations pour chaque jeu de données. |
| Nombre de succès | Total des actualisations réussies pour chaque jeu de données. |
| Nombre d’échecs | Total des actualisations ayant échoué pour chaque jeu de données. |
| Taux de réussite  | Nombre d’actualisations réussies divisé par le total des actualisations pour mesurer la fiabilité. |
| Durée moyenne (min) | durée moyenne d’actualisation du jeu de données, en minutes.  |
| Durée maximale (min) | durée de l’actualisation la plus longue en cours d’exécution pour le jeu de données, en minutes. |
| Temps d’attente moyen (min) | délai moyen entre l’heure planifiée et le début d’une actualisation du jeu de données, en minutes. |
| Temps d’attente maximal (min) | délai d’attente maximal du jeu de données, en minutes. |

##### <a name="query"></a>Requête

| **Métrique** | **Description** |
| --- | --- |
| Nombre total | Nombre total de requêtes exécutées pour le jeu de données. |
| Durée moyenne (ms) |durée moyenne des requêtes pour le jeu de données, en millisecondes|
| Durée maximale (ms) |Durée de la requête dont l’exécution est la plus longue dans le jeu de données, en millisecondes. |
| Temps d'attente moyen (ms) |Temps d’attente moyen des requêtes pour le jeu de données, en millisecondes. |
| Temps d’attente maximal (ms) |Durée de la requête à l’attente la plus longue dans le jeu de données, en millisecondes. |

##### <a name="eviction"></a>Expulsion

| **Métrique** | **Description** |
| --- | --- |
| Nombre de modèles | Nombre total d’évictions de jeux de données pour cette capacité. Quand une capacité est confrontée à une sollicitation de la mémoire, le nœud supprime un ou plusieurs jeux de données de la mémoire. Les jeux de données qui sont inactifs (ceux pour lesquels aucune opération d’interrogation ou d’actualisation n’est en cours d’exécution) sont supprimés en premier. Ensuite, l’ordre d’éviction est basé sur une mesure dite « dernier récemment utilisé (LRU) ». |

#### <a name="paginated-reports"></a>Rapports paginés

##### <a name="report-execution"></a>Exécution du rapport

| **Métrique** | **Description** |
| --- | --- |
| Nombre d’exécutions  | Nombre de fois où le rapport a été exécuté et consulté par les utilisateurs.|

##### <a name="report-usage"></a>Utilisation du rapport

| **Métrique** | **Description** |
| --- | --- |
| Nombre de succès | Nombre de fois où le rapport a été consulté par un utilisateur. |
| Nombre d’échecs |Nombre de fois où le rapport a été consulté par un utilisateur.|
| Nombre de lignes |nombre de lignes de données dans le rapport. |
| Durée d’extraction de données (ms) |délai moyen nécessaire pour récupérer des données pour le rapport, en millisecondes. De longs délais peuvent indiquer des requêtes lentes ou d’autres problèmes au niveau de la source de données.  |
| Durée de traitement (ms) |délai moyen nécessaire pour traiter les données pour un rapport, en millisecondes. |
| Durée de rendu (ms) |délai moyen nécessaire pour afficher un rapport dans le navigateur, en millisecondes. |

> [!NOTE]
> Les métriques détaillées de la charge de travail de l’**IA** ne sont pas encore disponibles.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez compris comment surveiller les capacités de Power BI Premium, vous pouvez en savoir plus sur l’optimisation des capacités.

> [!div class="nextstepaction"]
> [Optimisation des capacités Power BI Premium](service-premium-capacity-optimize.md)


Introduite par Power BI, l’offre en préversion Power BI Premium Gen2 apporte les améliorations suivantes à l’expérience Power BI Premium :
* Performances
* Licences par utilisateur
* Mise à l’échelle supérieure
* Métriques améliorées
* Mise à l’échelle automatique
* Charge de gestion réduite

Pour plus d’informations sur Power BI Premium Gen2, consultez [Power BI Premium Generation 2 (préversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).