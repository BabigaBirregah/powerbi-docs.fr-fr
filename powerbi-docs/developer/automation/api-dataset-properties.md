---
title: Propriétés de jeu de données Power BI dans l’analytique incorporée Power BI pour de meilleurs insights via la BI incorporée
description: Découvrez les propriétés des API de jeu de données Power BI. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: b4bd173c2f3730a0a6082214afbfdf5760048102
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887681"
---
# <a name="dataset-properties"></a>Propriétés du jeu de données

La version v1 actuelle de l’API de jeux de données permet uniquement de créer un jeu de données avec un nom et une collection de tables. Chaque table a un nom et une collection de colonnes. Chaque colonne a un nom et un type de données. Nous étendons ces propriétés, plus particulièrement avec la prise en charge des mesures et des relations entre les tables. Voici la liste complète des propriétés prises en charge pour cette version :

> [!IMPORTANT]
> Vous pouvez y accéder à la page [Groupes d’opérations de jeux de données](/rest/api/power-bi/datasets).

## <a name="dataset"></a>Dataset

Nom  |Type  |Description  |Lecture seule  |Obligatoire
---------|---------|---------|---------|---------
id     |  Guid       | Identificateur unique à l’échelle du système pour le jeu de données.        | True        | False        
name     | String        | Nom de jeu de données défini par l’utilisateur.        | False        | True        
tables     | Table[]        | Collection de tables.        |  False       | False        
relationships     | Relationship[]        | Collection de relations entre les tables.        | False        |  False  
defaultMode     | String        | Détermine si le jeu de données est envoyé, diffusé en continu ou les deux, avec les valeurs « Push » et « Streaming ».         | False        |  False

## <a name="table"></a>Table de charge de travail

Nom  |Type  |Description  |Lecture seule  |Obligatoire
---------|---------|---------|---------|---------
name     | String        |  Nom de table défini par l’utilisateur. Sert également d’identificateur de la table.       | False        |  True       
colonnes     |  column[]       |  Collection de colonnes.       | False        |  True       
measures     | measure[]        |  Collection de mesures.       | False        |  False       
isHidden     | Boolean        | Si Vrai, la table est masquée dans les outils clients.        | False        | False        

## <a name="column"></a>Colonne

Nom  |Type  |Description  |Lecture seule  |Obligatoire
---------|---------|---------|---------|---------
name     |  String        | Nom de colonne défini par l’utilisateur.        |  False       | True       
dataType     |  String       |  [Types de données EDM](/dotnet/framework/data/adonet/entity-data-model-primitive-data-types) pris en charge et restrictions. Consultez [Restrictions des types de données](#data-type-restrictions).      |  False       | True        
formatString     | String        | Chaîne décrivant la façon dont la valeur doit être mise en forme lorsqu’elle est affichée. Pour en savoir plus sur la mise en forme des chaînes, consultez [Contenu FORMAT_STRING](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents).      | False        | False        
sortByColumn    | String        |   Nom de chaîne d’une colonne dans la même table à utiliser pour trier la colonne en cours.     | False        | False       
dataCategory     | String        |  Valeur de chaîne à utiliser pour la catégorie de données qui décrit les données de cette colonne. Voici certaines valeurs courantes : Address, City, Continent, Country, Image, ImageUrl, Latitude, Longitude, Organization, Place, PostalCode, StateOrProvince, WebUrl       |  False       | False        
isHidden    |  Boolean       |  Propriété qui indique si la colonne est masquée. La valeur par défaut est false.       | False        | False        
summarizeBy     | String        |  Méthode d’agrégation par défaut pour la colonne. Voici les valeurs disponibles : default, none, sum, min, max, count, average, distinctCount     |  False       | False

## <a name="measure"></a>Mesure

Nom  |Type  |Description  |Lecture seule  |Obligatoire
---------|---------|---------|---------|---------
name     | String        |  Nom de mesure défini par l’utilisateur.       |  False       | True        
expression     | String        | Expression DAX valide.        | False        |  True       
formatString     | String        |  Chaîne décrivant la façon dont la valeur doit être mise en forme lorsqu’elle est affichée. Pour en savoir plus sur la mise en forme des chaînes, consultez [Contenu FORMAT_STRING](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents).       | False        | False        
isHidden     | String        |  Si Vrai, la table est masquée dans les outils clients.       |  False       | False       

## <a name="relationship"></a>Relationship

Nom  |Type  |Description  |Lecture seule  |Obligatoire 
---------|---------|---------|---------|---------
name     | String        | Nom de relation défini par l’utilisateur. Sert également d’identificateur de la relation.        | False       | True        
crossFilteringBehavior     | String        |    Direction de filtrage de la relation : OneDirection (par défaut), BothDirections, Automatic       | False        | False        
fromTable     | String        | Nom de la table de clé étrangère.        | False        | True         
fromColumn    | String        | Nom de la colonne de clé étrangère.        | False        | True         
toTable    | String        | Nom de la table de clé primaire.        | False        | True         
toColumn     | String        | Nom de la colonne de clé primaire.        | False        | True        

## <a name="data-type-restrictions"></a>Restrictions des types de données

Ces restrictions s’appliquent à la propriété dataType.

Type de données  |Restrictions  
---------|---------
Int64     |   Valeurs Int64.MaxValue et Int64.MinValue non autorisées.      
Double     |  Les valeurs Double.MaxValue et Double.MinValue ne sont pas autorisées. NAN non pris en charge. + Infinity et - Infinity non pris en charge dans certaines fonctions (par exemple, Min, Max).       
Boolean     |   Vrai ou faux.
Datetime    |   Lors du chargement des données nous quantifions les valeurs avec des fractions de jour en multiples de 1/300ème de seconde (3.33ms).      
String     |  Autorise actuellement jusqu’à 4 000 caractères par valeur de chaîne.
Decimal|précision=28, échelle=4

## <a name="example"></a> Exemple
L’exemple de code suivant inclut un certain nombre de ces propriétés :

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```