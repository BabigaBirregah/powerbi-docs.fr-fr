---
ms.openlocfilehash: f22c12ec0ad5bd413f3658704132143c878df1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799837"
---
L’utilisation de **variables** représente une partie extrêmement puissante d’une expression DAX.

![](media/7-4-dax-expressions/dax-variables_1.png)

Vous pouvez définir une variable n’importe où dans une expression DAX, à l’aide de la syntaxe suivante :

    VARNAME = RETURNEDVALUE

Les variables peuvent être de n’importe quel type de données, notamment des tables entières.

N’oubliez pas que chaque fois que vous référencez une variable de votre expression DAX, Power BI doit recalculer sa valeur en fonction de votre définition. C’est pourquoi il est conseillé d’éviter de répéter des variables dans votre fonction.

> Contenu vidéo fourni par [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

