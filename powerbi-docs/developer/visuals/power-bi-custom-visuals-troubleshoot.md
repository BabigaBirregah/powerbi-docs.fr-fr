---
title: Résolution des problèmes liés au développement de visuels Power BI dans l’analytique incorporée Power BI pour obtenir de meilleurs insights via la BI incorporée
description: Cet article décrit certains problèmes courants que vous pouvez rencontrer quand vous développez ou créez un visuel Power BI personnalisé. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: troubleshooting
ms.date: 11/06/2018
ms.openlocfilehash: 440bb6648dca1eaa85b697a10e9fd41180c66d7e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888095"
---
# <a name="troubleshoot-power-bi-visuals"></a>Résoudre les problèmes de visuels Power BI

## <a name="debug"></a>Débogage

**Commande Pbiviz introuvable (ou erreurs similaires)**

Quand vous exécutez `pbiviz` dans la ligne de commande de votre terminal, vous devez voir l’écran d’aide. Si ce n’est pas le cas, cela signifie qu’il n’est pas installé correctement. Assurez-vous d’avoir au moins la version 4.0 de NodeJS installée.

**Impossible de trouver le visuel de débogage sous l’onglet Visualisations**

L’élément visuel de débogage ressemble à une icône d’invite sous l’onglet **Visualisations**.

![Sélection du visuel](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Si vous ne le voyez pas, assurez-vous que vous l’avez activé dans les paramètres de Power BI.

> [!NOTE]
> L’élément visuel de débogage est actuellement disponible uniquement dans le service Power BI, pas dans Power BI Desktop ou dans l’application mobile. L’élément visuel empaqueté fonctionne partout.

**Impossible de contacter le serveur d’éléments visuels**

Exécutez le serveur de visuels avec la commande `pbiviz start` dans la ligne de commande de votre terminal à partir de la racine de votre projet de visuel. Si le serveur n’est pas en cours d’exécution, vos certificats SSL n’ont probablement pas été correctement installés.

N’hésitez pas à contacter l’équipe de support des visuels Power BI (pbicvsupport@microsoft.com) si vous avez des questions, des commentaires ou des problèmes.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Questions fréquentes sur les visuels Power BI](power-bi-custom-visuals-faq.md#organizational-power-bi-visuals).