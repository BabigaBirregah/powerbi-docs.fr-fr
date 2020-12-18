---
title: Passer votre application analytique incorporée Power BI en production
description: Découvrez les étapes nécessaires pour passer votre application Power BI en production.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 188974531f7b78e04c2cf0f8072dcef7efe3b888
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098188"
---
# <a name="move-your-embedded-app-to-production"></a>Passer une application incorporée en production

Une fois votre application développée, pour la passer en production, vous allez devoir adosser une capacité à votre espace de travail.

> [!Important]
> Tous les espaces de travail (ceux contenant les rapports ou les tableaux de bord, et ceux contenant les jeux de données) doivent être affectés à une capacité.

## <a name="create-a-capacity"></a>Créer une capacité

En créant une capacité, vous bénéficiez d’une ressource pour vos clients. Vous avez le choix entre deux types de capacités :

* **Power BI Premium** : un abonnement Microsoft 365 au niveau du locataire, disponible dans deux familles de références SKU : *EM* et *P*. Lors de l’incorporation de contenu Power BI, cette solution est appelée *incorporation de Power BI*. Pour plus d’informations sur cet abonnement, consultez [Qu’est-ce que Power BI Premium ?](../../admin/service-premium-what-is.md)

* **Azure Power BI Embedded** : vous pouvez acheter une capacité à partir du [portail Microsoft Azure](https://portal.azure.com). Cet abonnement utilise les références SKU *A*. Pour en savoir plus sur la création d’une capacité Power BI Embedded, consultez [Créer une capacité Power BI Embedded dans le Portail Microsoft Azure](azure-pbie-create-capacity.md).

    > [!NOTE]
    > Les références SKU A ne vous permettent pas d’accéder à du contenu Power BI avec une licence Power BI GRATUITE.

### <a name="capacity-specifications"></a>Spécifications des capacités

Le tableau ci-dessous décrit les ressources et les limites de chaque référence SKU. Pour déterminer la capacité qui correspond le mieux à vos besoins, consultez le tableau [Quelle référence SKU dois-je acheter pour mon scénario ?](./embedded-faq.md#which-solution-should-i-choose)

| Nœuds de capacité | Total des v-cores | Cœurs virtuels backend | RAM (Go) | Cœurs virtuels frontend | DirectQuery/Connexions actives (par seconde) | Parallélisme des actualisations de modèles |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>Tests de développement

Pour les tests de développement, vous pouvez utiliser des jetons d’essai d’incorporation avec une licence Pro. Pour incorporer dans un environnement de production, utilisez une capacité.

Le nombre de jetons d’essai d’incorporation qu’un *principal de service* ou un *utilisateur maître* (un compte maître) peut générer est limité. Utilisez l’API [Fonctionnalités disponibles](/rest/api/power-bi/availablefeatures/getavailablefeatures) pour vérifier le pourcentage de votre utilisation incorporée actuelle. La quantité d’utilisation est affichée par principal de service ou compte principal.

Si vous n’avez plus de jetons d’incorporation pendant les tests, vous devez acheter une [capacité](embedded-capacity.md) Power BI Embedded ou Premium. Avec une capacité, le nombre de jetons d’incorporation que vous pouvez générer n’est pas limité.

## <a name="assign-a-workspace-to-a-capacity"></a>Affecter un espace de travail à une capacité

Après avoir créé une capacité, vous pouvez lui affecter votre espace de travail.

Tous les espaces de travail qui contiennent des ressources Power BI associées au contenu incorporé (notamment les jeux de données, les rapports et les tableaux de bord) doivent être affectés à des capacités. Par exemple, si un rapport incorporé et le jeu de données qui lui est lié se trouvent dans des espaces de travail différents, les deux espaces de travail doivent être affectés à des capacités.

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>Affecter un espace de travail à une capacité en utilisant un principal de service

Pour affecter une capacité à un espace de travail en utilisant un [principal de service](embed-service-principal.md), utilisez l’[API REST Power BI](/rest/api/power-bi/capacities/groups_assigntocapacity). Quand vous utilisez les API REST Power BI, veillez à utiliser l’[ID d’objet du principal de service](embed-service-principal.md).

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>Affecter un espace de travail à une capacité en utilisant un utilisateur maître

Suivez les étapes ci-dessous pour affecter une capacité à un espace de travail en utilisant un **utilisateur maître**.

1. Ouvrez l’espace de travail dans le **service Power BI**, puis sélectionnez 

1. Dans le **service Power BI**, développez les espaces de travail, puis sélectionnez les points de suspension en regard de l’espace de travail que vous utilisez pour incorporer votre contenu. Sélectionnez ensuite **Modifier l’espace de travail**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="Capture d’écran montrant le menu des paramètres de l’espace de travail dans le portail du service Power BI.":::

2. Sélectionnez l’onglet **Premium** et procédez comme suit :

    * Activez **Capacité**.

    * Sélectionnez la capacité que vous avez créée.

    * Sélectionnez **Enregistrer**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="Capture d’écran montrant l’onglet des paramètres Premium de l’espace de travail dans le portail du service Power BI.":::

    Après avoir affecté votre espace de travail à une capacité, un losange s’affiche à côté de celui-ci. 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="Capture d’écran montrant le losange à côté d’un espace de travail avec une capacité Premium dans le portail du service Power BI.":::

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Capacité et références SKU dans l’analytique intégrée de Power BI](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Planification d’une capacité dans l’analytique incorporée de Power BI](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[Considérations relatives à la génération d’un jeton incorporé](generate-embed-token.md)