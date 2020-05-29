---
title: Utiliser DirectQuery avec des dataflows dans Power BI (préversion)
description: Découvrez comment utiliser DirectQuery avec des dataflows dans Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/19/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 9de8c9611b24eaa627b3ddf044f13d36d7b9a3d4
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694570"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Utiliser DirectQuery avec des dataflows dans Power BI (préversion)

Vous pouvez utiliser DirectQuery pour vous connecter directement des dataflows, et ainsi vous connecter directement à votre dataflow sans devoir importer ses données. 

L’utilisation de DirectQuery avec des dataflows apporte les améliorations suivantes à Power BI et à vos processus de dataflows :

* **Éviter les planifications d’actualisation distinctes** : DirectQuery se connecte directement à un dataflow, ce qui élimine la nécessité de créer un jeu de données. Ainsi, l’utilisation de DirectQuery avec vos dataflows signifie que vous n’avez plus besoin de planifications d’actualisation distinctes pour le dataflow et pour le jeu de données pour garantir que vos données sont synchronisées.

* **Filtrage des données** : DirectQuery est pratique pour travailler sur une vue filtrée des données au sein d’un dataflow. Si vous voulez filtrer les données et ainsi travailler sur un sous-ensemble de données plus petit dans votre dataflow, vous pouvez utiliser DirectQuery (et le moteur de calcul) pour filtrer les données du dataflow et utiliser le sous-ensemble filtré dont vous avez besoin.


## <a name="using-directquery-for-dataflows"></a>Utilisation de DirectQuery pour les dataflows

L’utilisation de DirectQuery avec des dataflows est une fonctionnalité en préversion disponible à partir de la version de mai 2020 de Power BI Desktop. 

Il existe également des prérequis pour l’utilisation de DirectQuery avec des dataflows :

* Votre dataflow doit se trouver dans un espace de travail activé pour Power BI Premium
* Le **moteur de calcul** doit être activé. Pour plus d’informations sur le moteur de calcul, consultez [Moteur de calcul amélioré](service-dataflows-enhanced-compute-engine.md).

## <a name="enable-directquery-for-dataflows"></a>Activer DirectQuery pour les dataflows

Pour garantir que votre flux de données est disponible pour un accès par DirectQuery, le moteur de calcul amélioré doit être dans son état optimisé. Pour activer DirectQuery pour les dataflows, définissez l’option **Paramètres du moteur de calcul amélioré** sur **Optimisé**. L’image suivante montre le paramètre correctement sélectionné.

![Activer le moteur de calcul amélioré pour les dataflows](media/service-dataflows-directquery/dataflows-directquery-01.png)

Une fois que vous avez appliqué ce paramètre, actualisez le dataflow pour que l’optimisation prenne effet. 


## <a name="considerations-and-limitations"></a>Considérations et limitations

Il existe quelques limitations connues avec DirectQuery et les dataflows, qui sont décrites dans la liste suivante.

* DirectQuery pour les dataflows ne fonctionne pas avec **la préversion de la fonctionnalité des métadonnées améliorées**. Cette exclusion est censée être supprimée dans une prochaine version mensuelle de Power BI Desktop.
* Pendant la période de préversion de cette fonctionnalité, certains clients peuvent rencontrer des dépassements de délai d’expiration ou des problèmes de performances lors de l’utilisation de DirectQuery avec des dataflows. Des solutions à ces problèmes sont activement recherchées pendant cette période de préversion.


## <a name="next-steps"></a>Étapes suivantes

Les articles suivants sont utiles pour accéder à des informations et à des scénarios supplémentaires lors de l’utilisation de flux de données :

* [Préparation des données en libre-service avec des flux de données](service-dataflows-overview.md)
* [Utilisation d’entités calculées sur Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Utilisation de flux de données avec des sources de données locales](service-dataflows-on-premises-gateways.md)
* [Ressources du développeur pour les flux de données Power BI](service-dataflows-developer-resources.md)
* [Flux de données et intégration à Azure Data Lake (préversion)](service-dataflows-azure-data-lake-integration.md)

Pour plus d’informations sur le modèle Common Data Model, vous pouvez lire son article de présentation :
* [Vue d’ensemble du modèle CMD (Common Data Model) ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [En savoir plus sur le schéma du modèle Common Data Model et sur les entités sur GitHub](https://github.com/Microsoft/CDM)

Articles de Power BI Desktop connexes :

* [Se connecter à des jeux de données dans le service Power BI à partir de Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)

Articles connexes du service Power BI Desktop :
* [Configuration d’une actualisation planifiée](../connect-data/refresh-scheduled-refresh.md)