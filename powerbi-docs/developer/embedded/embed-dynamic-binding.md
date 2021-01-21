---
title: Connecter un rapport Power BI à un jeu de données à l’aide de la liaison dynamique
description: Découvrez comment incorporer un rapport Power BI à l’aide d’une liaison dynamique dans l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 01/17/2021
ms.openlocfilehash: 0bc33ed37e389b42f5c27f8271cc461eb99e229a
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565812"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Connecter un rapport à un jeu de données à l’aide de la liaison dynamique 

Quand un rapport est connecté à un jeu de données, vous pouvez utiliser la liaison dynamique. La connexion entre le rapport et le jeu de données est appelée *liaison*. Quand la liaison est déterminée au point d’incorporation, et non pas prédéterminée auparavant, la liaison est appelée « liaison dynamique ».

Lors de l’incorporation d’un rapport Power BI à l’aide de la *liaison dynamique*, vous pouvez connecter le même rapport à différents jeux de données en fonction des informations d’identification de l’utilisateur.

Cela signifie que vous pouvez utiliser un rapport pour afficher des informations différentes, en fonction du jeu de données auquel il est connecté. Par exemple, un rapport qui indique les valeurs de vente au détail peut être connecté à différents jeux de données du détaillant et produire des résultats différents, en fonction du jeu de données du détaillant auquel il est connecté.

Le rapport et le jeu de données n’ont pas besoin de se trouver dans le même espace de travail. Les deux espaces de travail (celui contenant le rapport et celui contenant le jeu de données) doivent être affectés à une [capacité](azure-pbie-create-capacity.md).

Dans le cadre du processus d’incorporation, assurez-vous que vous *générez un jeton avec des autorisations suffisantes* et *ajustez l’objet de configuration*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Génération d’un jeton avec des autorisations suffisantes

La liaison dynamique est prise en charge dans les deux scénarios : *Incorporation pour votre organisation* et *Incorporation pour vos clients*. Le tableau ci-dessous décrit les considérations relatives à chaque scénario.

|Scénario  |Propriété des données  |Jeton  |Configuration requise  |
|---------|---------|---------|---------|
|*Incorporation pour votre organisation*    |L’utilisateur possède les données         |Jeton d’accès pour les utilisateurs de Power BI         |L’utilisateur dont le jeton Azure AD est utilisé doit avoir les autorisations appropriées pour tous les artefacts.         |
|*Incorporation pour vos clients*     |L’application possède les données         |Jeton d’accès pour les clients qui n’utilisent pas Power BI         |Doit inclure des autorisations à la fois pour le rapport et le jeu de données lié dynamiquement. Utilisez [l’API pour générer un jeton incorporé pour plusieurs éléments](/rest/api/power-bi/embedtoken/generatetoken), afin de générer un jeton d’incorporation qui prend en charge plusieurs artefacts.         |

## <a name="adjusting-the-config-object"></a>Ajustement de l’objet de configuration

Pour que la liaison dynamique fonctionne, vous devez ajouter `datasetBinding` à l’objet de configuration. Pour savoir comment procéder, consultez [Lier des jeux de données de manière dynamique à un rapport](/javascript/api/overview/powerbi/bind-report-datasets). 

## <a name="next-steps"></a>Étapes suivantes

Si vous débutez avec l’incorporation dans Power BI, suivez ces tutoriels pour découvrir comment incorporer votre contenu Power BI.

>[!div class="nextstepaction"]
>[Incorporer du contenu Power BI dans une application pour vos clients](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Incorporer du contenu Power BI dans une application pour votre organisation](embed-sample-for-your-organization.md)