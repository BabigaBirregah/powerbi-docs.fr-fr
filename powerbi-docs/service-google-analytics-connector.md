---
title: "Service tiers : connecteur Google Analytics pour Power BI Desktop"
description: "Service tiers : connecteur Google Analytics pour Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: a419a057405f56f452a53b21276fe5e4f6a4f851
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="google-analytics-connector-for-power-bi-desktop"></a>Connecteur Google Analytics pour Power BI Desktop
> [!NOTE]
> Le pack de contenu et le connecteur Google Analytics de Power BI Desktop s’appuient sur l’API Core Reporting de Google Analytics. Par conséquent, les fonctionnalités et la disponibilité peuvent varier au fil du temps.
> 
> 

Vous pouvez vous connecter aux données Google Analytics à l’aide du connecteur **Google Analytics**. Pour vous connecter aux données, procédez comme suit :

1. Dans **Power BI Desktop**, sélectionnez **Obtenir des données** dans l’onglet de ruban **Accueil**.
2. Dans la fenêtre **Obtenir des données** , sélectionnez **Autre** parmi les catégories du volet gauche.
3. Sélectionnez **Google Analytics** dans les sélections du volet droit.
4. Au bas de la fenêtre, sélectionnez **Se connecter**.  
   ![](media/service-google-analytics-connector/tps_googleanalytics_1.png)

Une boîte de dialogue s’affiche, expliquant, entre autres éclaircissements, que le connecteur est un service tiers et que la disponibilité et les fonctionnalités de celui-ci peuvent changer avec le temps.  
![](media/service-google-analytics-connector/tps_googleanalytics_2.png)

Quand vous sélectionnez **Continuer**, vous êtes invité à vous connecter à Google Analytics.  
![](media/service-google-analytics-connector/tps_googleanalytics_3.png)

Quand vous entrez vos informations d’identification, une boîte de dialogue vous informe que Power BI souhaite avoir un accès hors connexion. Voici comment utiliser **Power BI Desktop** pour accéder à vos données Google Analytics.  

Lorsque vous acceptez, **Power BI Desktop** indique que vous êtes actuellement connecté.  
![](media/service-google-analytics-connector/tps_googleanalytics_5.png)

Sélectionnez **Se connecter** pour connecter vos données Google Analytics à **Power BI Desktop** et charger les données.  
![](media/service-google-analytics-connector/tps_googleanalytics_6.png)

## <a name="changes-to-the-api"></a>Modifications apportées à l’API
Nous nous efforçons de publier des mises à jour en fonction des modifications. Toutefois, il se peut que l’API soit modifiée d’une manière qui affecte les résultats des requêtes que nous générons. Dans certains cas, certaines requêtes peuvent ne plus être prises en charge. En raison de cette dépendance, nous ne pouvons pas garantir les résultats de vos requêtes lors de l’utilisation de ce connecteur.

Pour plus d’informations sur les modifications apportées à l’API Google Analytics, consultez le [journal des modifications](https://developers.google.com/analytics/devguides/changelog)
