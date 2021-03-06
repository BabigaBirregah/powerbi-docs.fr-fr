---
title: 'DAX : Utiliser COUNTROWS à la place de COUNT'
description: Conseils d’utilisation des fonctions COUNTROWS.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 1a2b8c6450cfd855a0018fb64dd385a0db6e350f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394195"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX : Utiliser COUNTROWS à la place de COUNT

En tant que modeleur de données, vous pouvez parfois avoir besoin d’écrire une expression DAX qui compte les lignes de la table. La table peut être une table de modèle ou une expression qui retourne une table.

Cette condition peut être remplie de deux manières. Vous pouvez utiliser la fonction [COUNT](/dax/count-function-dax) pour compter les valeurs de colonne ou vous pouvez utiliser la fonction [COUNTROWS](/dax/countrows-function-dax) pour compter les lignes de la table. Les deux fonctions aboutissent au même résultat, dans la mesure où la colonne comptée ne contient pas de valeurs BLANK.

La définition de mesure suivante présente un exemple. Elle calcule le nombre de valeurs de colonne **OrderDate**.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

Si la précision de la table **Sales** correspond à une seule ligne par commande et que la colonne **OrderDate** ne contient pas de valeurs BLANK, alors la mesure retourne un résultat correct.

Toutefois, la définition de mesure suivante est une meilleure solution.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Il existe trois raisons pour lesquelles la deuxième définition de mesure est meilleure :

- Elle est plus efficace et elle est donc plus performante.
- Elle ne tient pas compte des valeurs BLANK contenues dans les colonnes de la table.
- L’objectif de la formule est plus clair et parvient à s’autodécrire.

## <a name="recommendation"></a>Recommandation

Lorsque vous avez l’intention de compter les lignes de la table, nous vous recommandons de toujours utiliser la fonction COUNTROWS.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Informations de référence sur DAX (Data Analysis Expressions)](/dax/)
- Parcours d’apprentissage : [Utiliser DAX dans Power BI Desktop](/learn/paths/dax-power-bi/)
- Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)