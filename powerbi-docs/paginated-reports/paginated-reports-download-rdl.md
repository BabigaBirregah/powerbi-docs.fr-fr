---
title: Téléchargement du .rdl d’un rapport paginé à partir d’un jeu de données
description: Dans cet article, vous allez apprendre à créer le fichier .rdl d’un rapport paginé Power BI en le téléchargeant à partir d’un jeu de données partagé dans le service Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 10/15/2020
ms.openlocfilehash: c5c8f61a7253da46529a83276366044560d4f030
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297630"
---
# <a name="download-the-rdl-for-a-power-bi-paginated-report-from-a-dataset"></a>Téléchargement du .rdl d’un rapport paginé Power BI à partir d’un jeu de données

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Dans cet article, vous allez apprendre à créer le fichier .rdl d’un rapport paginé Power BI en le téléchargeant à partir d’un jeu de données partagé dans le service Power BI. Les rapports paginés possèdent le format de fichier *.rdl*. Il est possible de créer un fichier .rdl directement à partir d’un jeu de données dans le service Power BI.

1. Accédez au mode Liste de n’importe quel espace de travail, y compris Mon espace de travail. 
1. Sélectionnez **Plus d’options (…)** pour un jeu de données, puis sélectionnez **Télécharger le .rdl**.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-download-rdl.png" alt-text="Capture d’écran de l’option Télécharger le .rdl dans le service Power BI":::
1. Le message qui apparaît indique que des mises à jour de Power BI Report Builder sont nécessaires. Sélectionnez **Télécharger**. 

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-updates.png" alt-text="Capture d’écran de l’installation des mises à jour de Power BI Report Builder":::

    Si vous savez que vous disposez de la dernière version de Power BI Report Builder, sélectionnez **J’ai déjà installé ces mises à jour**.

1. Suivez le processus d’installation de Power BI Report Builder : 

    1. Sélectionnez **Télécharger**.  
    2. Sélectionnez **Ouvrir le fichier** et suivez les étapes de l’Assistant Installation de Power BI Report Builder.

1. Une fois l’installation de Report Builder terminée, revenez au service Power BI et sélectionnez **Télécharger le .rdl**.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-finished-installing.png" alt-text="Capture d’écran de la boîte de dialogue Télécharger le .rdl":::

1. Sélectionnez **Ouvrir le fichier** dans la fenêtre du navigateur.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-open-file.png" alt-text="Capture d’écran de la sélection de l’option Ouvrir le fichier dans un navigateur":::

1. Power BI Report Builder s’ouvre avec un titre généré automatiquement et le fichier .pbix du jeu de données Power BI dans le dossier **Sources de données**. La source de données porte le même nom que le jeu de données Power BI.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-design-canvas.png" alt-text="Capture d’écran de Power BI Report Builder en mode Création":::

    L’aire de conception comporte également un lien vers le cours vidéo [Rapports paginés Power BI en une journée](../learning-catalog/paginated-reports-online-course.md). Si vous ne savez pas encore créer des rapports paginés, ce cours constitue un bon moyen de devenir opérationnel.  Vous pourrez le supprimer lorsque vous commencerez à concevoir votre rapport.

    Vous pouvez maintenant commencer à concevoir votre rapport paginé.
 
## <a name="next-steps"></a>Étapes suivantes 

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)  
- [Tutoriel : Créer un rapport paginé et le charger dans le service Power BI](paginated-reports-quickstart-aw.md)
- [Publier un rapport paginé dans le service Power BI](paginated-reports-save-to-power-bi-service.md)

