---
title: Lier des entités entre des flux de données dans Power BI
description: Guide pratique pour lier des entités dans des flux de données dans Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b69b84c7c61227ef7a827722c86f54100bd2f3b7
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51267245"
---
# <a name="link-entities-between-dataflows-in-power-bi-preview"></a>Lier des entités entre des flux de données dans Power BI (préversion)

Grâce aux flux de données dans Power BI, vous disposez d’une source de stockage des données d’organisation dans laquelle les analystes peuvent préparer et gérer leurs données une fois, puis les réutiliser entre les différentes applications analytiques de l’organisation. 

Lorsque vous liez des entités entre des flux de données, vous pouvez réutiliser les entités qui ont déjà été reçues, nettoyées et transformées par d’autres flux de données appartenant à d’autres utilisateurs, sans avoir à conserver ces données. Les entités liées pointent simplement vers les entités dans d’autres flux de données, *sans* copier ou dupliquer les données.

![Entités liées dans Power BI](media/service-dataflows-linked-entities/linked-entities_00.png)

Les entités liées sont **en lecture seule**. Si vous souhaitez créer des transformations pour une entité liée, vous devez créer une nouvelle entité calculée avec une référence à l’entité liée.

## <a name="linked-entity-availability"></a>Disponibilité de l’entité liée

Les entités liées nécessitent un abonnement [Power BI Premium](service-premium.md) à actualiser. Les entités liées sont disponibles dans n’importe quel flux de données sur un espace de travail hébergé sur la capacité Power BI Premium. Il n’existe aucune limitation concernant le flux de données source.

Les entités liées fonctionnent uniquement correctement dans les nouveaux espaces de travail Power BI. Si vous le souhaitez, des [informations supplémentaires sur les nouveaux espaces de travail Power BI](service-create-the-new-workspaces.md) sont disponibles. Pour fonctionner correctement, tous les flux de données liés doivent se trouver dans les nouveaux espaces de travail.

## <a name="how-to-link-entities-between-dataflows"></a>Guide pratique pour lier des entités entre des flux de données

Il existe plusieurs façons de liaison des entités entre des flux de données dans Power BI. Vous pouvez sélectionner **Ajouter des entités liées** à partir de l’outil de création de flux de données, comme illustré dans l’image suivante. 

![Entités liées dans Power BI](media/service-dataflows-linked-entities/linked-entities_00.png)

Vous pouvez également sélectionner **Ajouter des entités liées** à partir de l’option de menu **Ajouter des entités** du service Power BI.

![Entités liées dans Power BI](media/service-dataflows-linked-entities/linked-entities_01.png)

Pour lier des entités, vous devez vous connecter avec vos informations d’identification Power BI.

Une fenêtre **Navigator** s’ouvre et vous permet de choisir un jeu d’entités auquel vous pouvez vous connecter. Les entités affichées sont des entités pour lesquels vous disposez des autorisations, dans tous les espaces de travail de votre locataire Power BI. 

Une fois vos entités liées sélectionnées, elles apparaissent dans la liste des entités de votre flux de données dans l’outil de création, avec une icône spéciale qui les identifie comme des entités liées.

Vous pouvez également afficher le flux de données source à partir des paramètres du flux de données de votre entité liée.

## <a name="refresh-logic-of-linked-entities"></a>Actualiser la logique d’entités liées
La logique d’actualisation par défaut des entités liées varie selon que le flux de données source réside dans le même espace de travail que le flux de données de destination. Les sections suivantes décrivent le comportement de chacun de ces éléments.

### <a name="links-between-workspaces"></a>Liens entre espaces de travail

L’actualisation des liens à partir d’entités de différents espaces de travail se comporte comme une source de données externe. Lorsque le flux de données est actualisé, il extrait les données les plus récentes pour l’entité à partir du flux de données source. Si le flux de données source est actualisé, il n’affecte pas automatiquement les données dans le flux de données de destination.

### <a name="links-in-the-same-workspace"></a>Liens dans le même espace de travail

En cas d’actualisation des données d’un flux de données source, cet événement déclenche automatiquement un processus d’actualisation des entités dépendantes dans tous les flux de données de destination de l’espace de travail, y compris toutes les entités calculées qui en dépendent. Toutes les autres entités du flux de données de destination sont actualisées selon la planification de flux de données. Les entités qui dépendent de plusieurs sources mettent à jour leurs données chaque fois qu’une de leurs sources est mise à jour avec succès.

Il est utile de noter que le processus d’actualisation complet intervient sur-le-champ. Pour cette raison, si l’actualisation du flux de données de destination ne parvient pas à s’actualiser, l’actualisation du flux de données source échoue également.

## <a name="permissions-when-viewing-reports-from-dataflows"></a>Autorisations lors de l’affichage des rapports à partir de flux de données

Lors de la création d’un rapport Power BI comprenant des données basées sur un flux de données, les utilisateurs peuvent voir toutes les entités liées uniquement lorsqu’il accède au flux de données source.

## <a name="limitations-and-considerations"></a>Considérations et limitations

Il existe quelques limitations à prendre en compte lorsque vous travaillez avec des entités liées :

* Il existe un maximum de cinq tronçons de référence
* Les dépendances cycliques d’entités liées ne sont pas autorisées
* Le flux de données doit résider dans un [nouvel espace de travail Power BI](service-create-the-new-workspaces.md)


## <a name="next-steps"></a>Étapes suivantes

Les articles suivants peuvent être utiles lorsque vous créez ou utilisez des flux de données. 

* [Préparation des données en libre-service dans Power BI (préversion)](service-dataflows-overview.md)
* [Créer et utiliser des flux de données dans Power BI](service-dataflows-create-use.md)
* [Utilisation d’entités calculées sur Power BI Premium (préversion)](service-dataflows-computed-entities-premium.md)
* [Utilisation de flux de données avec des sources de données locales (préversion)](service-dataflows-on-premises-gateways.md)
* [Ressources du développeur pour les flux de données Power BI (préversion)](service-dataflows-developer-resources.md)

Pour plus d’informations sur Power Query et l’actualisation planifiée, vous pouvez consulter ces articles :
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Configuration d’une actualisation planifiée](refresh-scheduled-refresh.md)

Pour plus d’informations sur le modèle Common Data Model, vous pouvez lire son article de présentation :
* [Vue d’ensemble du modèle CMD (Common Data Model) ](https://docs.microsoft.com/powerapps/common-data-model/overview)
