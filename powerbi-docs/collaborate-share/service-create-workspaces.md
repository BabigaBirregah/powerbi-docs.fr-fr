---
title: Créer des espaces de travail classiques dans Power BI
description: 'Découvrez comment créer des espaces de travail classiques : collections de tableaux de bord, rapports et rapports paginés conçus pour fournir des métriques clés pour votre organisation.'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 01/12/2021
LocalizationGroup: Share your work
ms.openlocfilehash: 0ff0d072bd36c7e49a7ce6d450b7a35410caa94f
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98227304"
---
# <a name="create-classic-workspaces-in-power-bi"></a>Créer des espaces de travail classiques dans Power BI

Dans Power BI, vous pouvez créer des *espaces de travail*, qui sont des endroits où collaborer avec des collègues pour créer et affiner des collections de tableaux de bord, de rapports et de rapports paginés. Power BI propose deux types d’espaces de travail : les *classiques*, ceux d’origine, et les nouveaux. Cet article explique comment créer un espace de travail classique.

**Le saviez-vous ?** Power BI offre une nouvelle expérience de l’espace de travail, qui est désormais l’expérience par défaut. Consultez [Organiser le travail dans les nouveaux espaces de travail ](service-new-workspaces.md) pour plus d’informations sur les nouveaux espaces de travail. Prêt à migrer votre espace de travail classique ? Consultez [Mettre à niveau les espaces de travail classiques vers de nouveaux espaces de travail dans Power BI](service-upgrade-workspaces.md) pour plus d’informations.

Quand vous créez un espace de travail classique, vous créez un groupe Microsoft 365 associé sous-jacent. Toute l’administration des espaces de travail se fait dans Microsoft 365. Vous pouvez ajouter des collègues à ces espaces de travail en tant que membres ou administrateurs. Dans l’espace de travail, vous pouvez tous collaborer sur des tableaux de bord, des rapports et d’autres articles que vous prévoyez de publier pour un public plus large. Toutes les personnes que vous ajoutez à un espace de travail doivent avoir une licence Power BI Pro.

## <a name="video-apps-and-workspaces"></a>Vidéo : Applications et espaces de travail
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-classic-workspace-based-on-a-microsoft-365-group"></a>Créer un espace de travail classique basé sur un groupe Microsoft 365

Quand vous créez un espace de travail, il est basé sur un groupe Microsoft 365.

[!INCLUDE [powerbi-service-create-app-workspace](../includes/powerbi-service-create-app-workspace.md)]

Quand vous le créez, vous devez attendre environ une heure pour qu’il se propage à Microsoft 365.

### <a name="add-an-image-to-your-microsoft-365-workspace-optional"></a>Ajouter une image à votre espace de travail Microsoft 365 (facultatif)
Par défaut, Power BI crée un petit cercle de couleur pour votre application, contenant les initiales de celle-ci. Vous pouvez le personnaliser avec une image. Pour ajouter une image, vous avez besoin d’une licence Exchange Online.

1. Sélectionnez **Espaces de travail**, sélectionnez **Plus d’options** (...) en regard du nom de l’espace de travail, puis choisissez **Membres**. 
   
     ![Sélectionner les membres de l’espace de travail](media/service-create-workspaces/power-bi-workspace-old-members.png)
   
    Le compte Microsoft 365 Outlook pour l’espace de travail s’ouvre dans une nouvelle fenêtre de navigateur.
2. Sélectionnez le crayon **Modifier**.
   
     ![Icône de crayon Microsoft 365](media/service-create-workspaces/power-bi-workspace-old-edit-group.png)
3. Sélectionnez l’image d’appareil photo et recherchez l’image que vous souhaitez utiliser.
   
     ![Sélectionner l’image d’appareil photo](media/service-create-workspaces/power-bi-workspace-old-camera.png)

     Les images peuvent être des fichiers .png, .jpg ou .bmp. Leur taille de fichier peut être importante, jusqu’à 3 Mo. 

4. Sélectionnez **OK**, puis **Enregistrer**.
   
    L’image remplace le cercle de couleur dans la fenêtre Microsoft 365 Outlook.
   
     ![Image personnalisée](media/service-create-workspaces/power-bi-workspace-old-new-image.png)
   
    Après quelques minutes, l’image apparaît également dans l’application dans Power BI.

## <a name="add-content-to-your-workspace"></a>Ajouter du contenu à votre espace de travail

Une fois que vous avez créé un espace de travail, vous pouvez y ajouter du contenu. Cela s’apparente à l’ajout de contenu à Mon espace de travail, sauf que les autres personnes au sein de l’espace de travail peuvent également en voir le contenu et travailler dessus. Une différence importante est que, lorsque vous avez terminé, vous pouvez publier le contenu en tant qu’application. Quand vous visualisez du contenu de la liste de contenu dans un espace de travail, le nom de l’espace de travail apparaît en tant que propriétaire.

### <a name="connect-to-third-party-services-in-workspaces"></a>Se connecter à des services tiers dans des espaces de travail

Des applications sont fournies pour tous les services tiers pris en charge par Power BI, ce qui facilite l’obtention de données auprès des services que vous utilisez, comme Microsoft Dynamics CRM, Salesforce ou Google Analytics. Vous pouvez publier des applications d’organisation pour donner aux utilisateurs les données dont ils ont besoin.

Dans les espaces de travail classiques, vous pouvez également vous connecter avec des packs de contenu d’organisation et des applications tierces comme Microsoft Dynamics CRM, Salesforce ou Google Analytics. Les packs de contenu d’organisation sont en cours de dépréciation. C’est donc le bon moment pour mettre à niveau vos packs de contenu vers des applications, si vous n’avez pas encore commencé à le faire. Consultez la section sur la feuille de route de mise à niveau de l’espace de travail dans le billet de blog intitulé [Announcing Power BI admins can upgrade classic workspaces](https://powerbi.microsoft.com/blog/announcing-power-bi-admins-can-upgrade-classic-workspaces-and-roadmap-update/) pour connaître la chronologie.

## <a name="distribute-an-app"></a>Distribuer une application

Si vous voulez distribuer du contenu officiel à un large public au sein de votre organisation, vous pouvez publier une application à partir de votre espace de travail.  Quand le contenu est prêt, vous choisissez les tableaux de bord et les rapports que vous voulez publier, puis vous les publiez en tant qu’*application*. Vous pouvez créer une application à partir de chaque espace de travail.

La liste Applications dans le volet de navigation présente toutes les applications que vous avez installées. Vos collègues peuvent obtenir votre application de différentes manières. 
- Ils peuvent rechercher et installer votre application à partir de Microsoft AppSource.
- Vous pouvez leur envoyer un lien direct. 
- Vous pouvez l’installer automatiquement dans les comptes Power BI de vos collègues si l’administrateur Power BI vous y autorise. 

Les utilisateurs voient automatiquement le contenu d’application mis à jour après la publication d’une mise à jour depuis votre espace de travail. Vous pouvez contrôler la fréquence à laquelle les données sont actualisées en définissant la planification de l’actualisation dans les jeux de données utilisés par le contenu de l’application dans votre espace de travail. Pour plus d’informations, consultez [Publier une application à partir des nouveaux espaces de travail dans Power BI](service-create-distribute-apps.md).

## <a name="power-bi-classic-apps-faq"></a>Forum aux questions sur les applications Power BI classiques

### <a name="how-are-apps-different-from-organizational-content-packs"></a>En quoi les applications diffèrent-elles des packs de contenu d’organisation ?
Les applications sont l’évolution des packs de contenu d’organisation, qui sont dépréciés. C’est donc le bon moment pour mettre à niveau vos packs de contenu vers des applications, si vous n’avez pas encore commencé à le faire. Consultez la section sur la feuille de route de mise à niveau de l’espace de travail dans le billet de blog intitulé [Announcing Power BI admins can upgrade classic workspaces](https://powerbi.microsoft.com/blog/announcing-power-bi-admins-can-upgrade-classic-workspaces-and-roadmap-update/) pour connaître la chronologie. 

* Quand des utilisateurs professionnels installent un pack de contenu, celui-ci perd son identité groupée : il s’agit simplement d’une liste de tableaux de bord et de rapports entremêlés avec d’autres tableaux de bord et rapports. En revanche, les applications conservent leur regroupement et leur identité même après installation. Les utilisateurs peuvent ainsi continuer à y accéder facilement au fil du temps.
* Vous pouvez créer plusieurs packs de contenu à partir de tout espace de travail, mais une application a une relation un-à-un avec son espace de travail. 
* Vous ne pouvez pas consommer ou créer de packs de contenu dans les nouveaux espaces de travail.

Consultez les [différences entre les espaces de travail nouveaux et classiques](service-new-workspaces.md#new-and-classic-workspace-differences) pour comparer les deux. 

## <a name="next-steps"></a>Étapes suivantes
* [Installer et utiliser des applications dans Power BI](service-create-distribute-apps.md)
- [Créer de nouveaux espaces de travail](service-create-the-new-workspaces.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
