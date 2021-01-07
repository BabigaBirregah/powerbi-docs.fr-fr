---
title: Discuter dans Microsoft Teams directement à partir du service Power BI
description: Vous pouvez partager des tableaux de bord et des rapports Power BI directement dans Microsoft Teams à partir du service Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 12/14/2020
ms.openlocfilehash: fde06eaa3b2dd44b91e8a47981ac4e9fecba5af3
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721406"
---
# <a name="chat-in-microsoft-teams-directly-from-the-power-bi-service"></a>Discuter dans Microsoft Teams directement à partir du service Power BI

Vous pouvez discuter des tableaux de bord, des rapports et des visuels Power BI directement dans Microsoft Teams à partir du service Power BI. Utilisez la fonctionnalité **Discuter dans Teams** pour démarrer rapidement des conversations quand vous consultez des rapports et des tableaux de bord dans le service Power BI.

## <a name="requirements"></a>Configuration requise

Pour utiliser la fonctionnalité **Discuter dans Teams** dans Power BI, vérifiez que votre administrateur Power BI n’a pas désactivé le paramètre de locataire **Partager dans Teams** dans le portail d’administration Power BI. Ce paramètre permet aux organisations de masquer les boutons **Discuter dans Teams**. Consultez l’article sur le [portail d’administration Power BI](../admin/service-admin-portal.md#share-to-teams) pour plus d’informations.

Pour plus d’informations sur l’interaction entre Power BI et Microsoft Teams, et notamment pour connaître d’autres conditions à remplir, consultez [Collaboration dans Microsoft Teams avec Power BI](service-collaborate-microsoft-teams.md).

## <a name="chat-about-power-bi-content-in-microsoft-teams"></a>Discuter au sujet d’un contenu Power BI dans Microsoft Teams

Suivez ces étapes pour partager des liens vers des rapports, des tableaux de bord et des visuels dans le service Power BI et discutez d’un contenu par le biais de conversations et de canaux Microsoft Teams.

1. Sélectionnez une de ces options :

   * **Discuter dans Teams** dans la barre d’action d’un tableau de bord ou d’un rapport :

       ![Capture d’écran du bouton Converser dans Teams dans la barre d’action.](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * **Discuter dans Teams** dans le menu contextuel d’un visuel spécifique :
    
      ![Capture d’écran du bouton Converser dans Teams dans le menu contextuel d’un visuel.](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. Dans la boîte de dialogue **Partager dans Microsoft Teams**, sélectionnez l’équipe ou le canal qui doit recevoir le lien. Vous pouvez entrer un message si vous le souhaitez. Vous serez peut-être invité à vous connecter au préalable à Microsoft Teams.

    ![Capture d’écran de la boîte de dialogue Partager dans Microsoft Teams avec les informations et le message](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. Sélectionnez **Partager** pour envoyer le lien.
    
1. Le lien est ajouté aux conversations existantes ou démarre une nouvelle conversation.

    ![Capture d’écran de la conversation Microsoft Teams avec un lien vers un élément Power BI](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. Sélectionnez le lien pour ouvrir l’élément dans le service Power BI.

1. Si vous avez utilisé le menu contextuel pour un objet visuel spécifique, ce dernier est mis en surbrillance à l’ouverture du rapport.

    ![Capture d’écran du rapport Power BI ouvert avec un visuel spécifique mis en surbrillance](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

- Un utilisateur sans licence Power BI ni autorisation d’accès pour le rapport voit un message « Ce contenu n’est pas disponible ».
- Les boutons **Discuter dans Teams** peuvent ne pas fonctionner si votre navigateur utilise des paramètres de confidentialité stricts. Utilisez l’option **Vous avez une difficulté ? Essayer d’ouvrir dans une nouvelle fenêtre** si la boîte de dialogue ne s’ouvre pas correctement.
- **Discuter dans Teams** n’inclut pas d’aperçu de lien.
- Les aperçus de lien et les boutons **Discuter dans Teams** n’accordent pas aux utilisateurs l’autorisation d’afficher l’élément. Les autorisations doivent être gérées séparément.
- Le bouton **Discuter dans Teams** n’est pas disponible dans les menus contextuels visuels quand un auteur de rapport définit **Plus d’options** sur **Désactiver** pour le visuel.
- Pour d’autres problèmes, consultez la section [Problèmes connus et limitations](service-collaborate-microsoft-teams.md#known-issues-and-limitations) de l’article « Collaborer dans Microsoft Teams ».

## <a name="next-steps"></a>Étapes suivantes

- [Collaborer dans Microsoft Teams avec Power BI](service-collaborate-microsoft-teams.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
