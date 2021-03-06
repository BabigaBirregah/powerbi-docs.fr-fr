---
title: Contrôle de version du modèle de données Power BI dans l’analytique incorporée Power BI pour de meilleurs insights via la BI incorporée
description: Modèle de données exposé par un service OData. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 0c645774f7af1a8575ca3c755a74fd65b652031a
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887704"
---
# <a name="data-model-versioning"></a>Gestion de versions du modèle de données

Le modèle de données exposé par un service OData, comme le modèle de données Power BI, définit un contrat entre le service OData et ses clients. Les services sont autorisés à étendre leur modèle seulement dans la mesure où ils n’empêchent pas les clients existants de fonctionner. Des modifications qui les empêchent de fonctionner, comme la suppression de propriétés ou le changement du type de propriétés existantes, nécessitent qu’une nouvelle version du service soit fournie à une URL racine de service différente pour le nouveau modèle.  
  
Les ajouts de modèle de données suivants sont considérés comme sûrs et ne nécessitent pas de services pour le contrôle de version de leur point d’entrée.  
  
* Ajout d’une propriété qui accepte la valeur Null ou qui a une valeur par défaut ; si elle a le même nom qu’une propriété dynamique existante, elle doit avoir le même type (ou type de base) que la propriété dynamique existante  
* Ajout d’une propriété de navigation qui accepte la valeur Null ou qui a une valeur de collection ; si elle a le même nom qu’une propriété de navigation dynamique existante, elle doit avoir le même type (ou type de base) que la propriété de navigation dynamique existante  
* Ajout d’un nouveau type d’entité au modèle  
* Ajout d’un nouveau type complexe au modèle  
* Ajout d’un jeu d’entités  
* Ajout d’un nouveau singleton  
* Ajout d’une action, d’une fonction, d’une importation d’action ou d’une importation de fonction
* Ajout d’un paramètre d’action qui accepte la valeur Null  
* Ajout d’une définition de type ou d’une énumération  
* Ajout d’une annotation à un élément de modèle qui n’a pas besoin d’être reconnu par le client pour interagir correctement avec le service  
  
Les clients ***DOIVENT** _ être préparés au fait que les services apportent de telles modifications incrémentielles à leur modèle. En particulier, les clients doivent être préparés à recevoir des propriétés et types dérivés non définis précédemment par le service.  
  
Les services _ *_NE DOIVENT PAS_** modifier leur modèle de données en fonction de l’utilisateur authentifié. Si le modèle de données est dépendant de l’utilisateur ou du groupe d’utilisateurs, toutes les modifications DOIVENT être sécurisées selon la définition donnée dans cette section lors de la comparaison entre le modèle complet et le modèle visible par les utilisateurs disposant d’autorisations restreintes.  
  
Pour plus d’informations sur les normes de modèle de données OData, consultez [OData Version 4.0 partie 1 : protocole et erratum 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).  
  
## <a name="see-also"></a>Voir aussi
[Vue d’ensemble de l’API REST Power BI](/rest/api/power-bi/)