---
title: API d’analytique incorporée Power BI utilisant une stratégie de rétention automatique pour les données en temps réel en vue d’obtenir de meilleurs insights via la BI incorporée
description: Découvrez la stratégie de rétention automatique dans le service Power BI. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 81c975332abc4cb599a7172f1697c1b06ea34eba
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887727"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Stratégie de rétention automatique des données en temps réel

La stratégie de conservation automatique du service Power BI est un paramètre de chaîne de requête qui active une stratégie de conservation par défaut pour nettoyer automatiquement les anciennes données tout en conservant un flux constant de nouvelles données vers votre tableau de bord. La première stratégie de conservation est appelée *FIFO (First in, First out)*. Quand elle est activée, les données sont collectées dans une table jusqu’à atteindre 200 000 lignes. Quand les données dépassent 200 000 lignes, les lignes les plus anciennes sont supprimées du jeu de données. Ceci permet de conserver entre 200 000 et 210 000 lignes contenant seulement les données les plus récentes.  
  
<center>

![stratégie de rétention](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Les stratégies de rétention sont activées lorsque vous créez vos jeux de données pour le première fois. Il vous suffit d’ajouter le paramètre de requête « defaultRetentionPolicy » à votre appel de jeux de données POST et de lui affecter la valeur *basicFIFO*.  

```console
POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}
```
