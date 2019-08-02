---
title: Copier des rapports à partir d’autres espaces de travail (préversion) - Power BI
description: Découvrez comment vous pouvez partager un jeu de données avec des utilisateurs au sein de l’organisation. Ils peuvent ensuite générer des rapports basés sur votre jeu de données dans leurs propres espaces de travail.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 2db4c23b50071e387913ed79b4d01daeafb928a4
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2019
ms.locfileid: "67567428"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Copier des rapports à partir d’autres espaces de travail (préversion)

Quand vous trouvez un rapport que vous aimez dans un espace de travail ou une application, vous pouvez en faire une copie et l’enregistrer dans un autre espace de travail. Vous pouvez ensuite modifier ce rapport, en ajoutant ou supprimant des visuels et d’autres éléments. Vous n’avez pas à vous soucier de la création du modèle de données. Il est déjà créé pour vous. En outre, il est beaucoup plus facile de modifier un rapport existant que de démarrer à partir de zéro. Cependant, vous ne pouvez pas publier votre copie du rapport dans une application à partir du nouvel espace de travail. Consultez la liste des autres [considérations et limitations](service-datasets-across-workspaces.md#considerations-and-limitations) dans l’article « Utilisation des jeux de données entre des espaces de travail ».

## <a name="save-a-copy-of-a-report"></a>Enregistrer une copie d’un rapport

1. Dans une application ou un espace de travail, accédez au mode Liste des rapports.

1. Sous **Actions**, sélectionnez **Enregistrer une copie**.

    ![Enregistrer une copie d’un rapport](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Vous voyez uniquement l’icône **Enregistrer une copie** si le rapport se trouve dans un espace de travail de nouvelle expérience et que vous avez des [autorisations de génération](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Même si vous avez accès à l’espace de travail, vous devez disposer des autorisations de génération pour le jeu de données.

3. Dans **Enregistrer une copie de ce rapport**, nommez le rapport, puis sélectionnez l’espace de travail de destination.

    ![Boîte de dialogue Enregistrer une copie](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Vous pouvez enregistrer le rapport dans l’espace de travail actuel ou un autre dans le service Power BI. Vous voyez uniquement les espaces de travail de nouvelle expérience, desquels vous êtes membre.
  
4. Sélectionnez **Enregistrer**.

    Lorsque vous enregistrez une copie du rapport, vous créez une connexion active au jeu de données et vous pouvez ouvrir l’expérience de création de rapports avec le jeu de données complet disponible. Vous n’avez pas effectué de copie du jeu de données. Le jeu de données se trouve toujours dans son emplacement d’origine. Vous pouvez utiliser toutes les tables et mesures du jeu de données dans votre propre rapport. Comme les restrictions de sécurité au niveau des lignes (SNL) sur le jeu de données sont appliquées, vous voyez uniquement les données que vous êtes autorisé à afficher en fonction de votre rôle SNL.

    Power BI crée automatiquement une entrée dans la liste des jeux de données si le rapport est basé sur un jeu de données se trouvant hors de l’espace de travail. L’icône de ce jeu de données est différente de l’icône des jeux de données dans l’espace de travail : ![Icône de jeu de données partagé](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    De cette manière, les membres de l’espace de travail peuvent indiquer les rapports et tableaux de bord qui utilisent des jeux de données se trouvant hors de l’espace de travail. L’entrée affiche des informations sur le jeu de données et quelques actions de sélection.

    ![Actions de jeu de données](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>Afficher les jeux de données associés

Lorsque vous avez un rapport dans votre espace de travail, vous devez peut-être connaître le jeu de données sur lequel il repose.

1. En mode Liste des rapports, sélectionnez **Afficher les éléments associés**.

    ![l’icône Afficher les travaux associés](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. La boîte de dialogue **Contenu associé** affiche tous les éléments associés. Dans cette liste, le jeu de données ressemble à n’importe quel autre. Vous ne pouvez pas savoir qu’il se trouve dans un autre espace de travail. Ce problème est connu.
 
    ![Boîte de dialogue Contenu associé](media/service-datasets-copy-reports/power-bi-dataset-related.png)

## <a name="delete-a-report-and-its-shared-dataset"></a>Supprimer un rapport et son jeu de données partagé

Vous pouvez décider que vous ne voulez plus du rapport et de son jeu de données partagé associé dans l’espace de travail.

1. Supprimez le rapport. Dans la liste des rapports de l’espace de travail, sélectionnez l’icône **Supprimer**.

    ![Icône Supprimer un rapport](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. Dans la liste des jeux de données, vous voyez que les jeux de données partagés n’ont pas d’icône **Supprimer**. Actualisez la page, ou accédez à une autre page et revenez à la liste. Le jeu de données doit avoir disparu. Si ce n’est pas le cas, cochez **Afficher les éléments associés**. Il peut être lié à une autre table de votre espace de travail.

    ![l’icône Afficher les travaux associés](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > Supprimer le jeu de données partagé dans cet espace de travail ne supprime pas le jeu de données. Cette opération supprime simplement la référence à celui-ci.


## <a name="next-steps"></a>Étapes suivantes

- [Utiliser des jeux de données dans des espaces de travail (préversion)](service-datasets-across-workspaces.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)