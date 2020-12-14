---
title: Présentation des signets dans les rapports du service Power BI
description: Rubrique de vue d’ensemble de la documentation pour les signets dans le service Power BI.
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/03/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 7aa199547f6cad0b7d4dbfc6b75e9d9e25b2b153
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96578334"
---
# <a name="what-are-bookmarks"></a>Qu’est-ce qu’un signet ?

[!INCLUDE[consumer-appliesto-ynnm](../includes/consumer-appliesto-ynnm.md)]


Les signets capturent la vue actuellement configurée d’une page de rapport, notamment les filtres, les segments et l’état des visuels. Lorsque vous sélectionnez un signet, Power BI vous ramène à cette vue. Il existe deux types de signets : ceux que vous créez et ceux qui sont créés par les *concepteurs* de rapports. Tout utilisateur Power BI peut créer des signets personnels. Toutefois, pour utiliser des signets créés par d’autres personnes, il faut une licence Power BI Pro ou Premium. [Quelle est ma licence ?](end-user-license.md)

## <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Utiliser des signets pour partager des insights et créer des récits dans Power BI 
Les signets ont de nombreuses utilisations. Imaginons que vous ayez découvert un insight très intéressant et que vous souhaitiez en garder une trace. Pour cela, vous pouvez créer un signet afin d’y revenir plus tard. Si vous souhaitez enregistrer votre travail avant de quitter le bureau, vous pouvez là aussi créer un signet. Vous pouvez même créer un signet correspondant à la vue par défaut de votre rapport. Ainsi, chaque fois que vous rouvrez le rapport, c’est cette vue qui s’affiche en premier. 

Vous pouvez également créer une collection de signets, les réorganiser dans l’ordre de votre choix, puis parcourir chaque signet dans le cadre d’une présentation, afin de mettre en avant une série d’insights.  

![Affichez le volet Signets en le sélectionnant dans le ruban.](media/end-user-bookmarks/power-bi-bookmark-icon.png)

Partagez votre rapport avec signets avec des collègues qui disposent également d’un accès en lecture au rapport. La vue avec signet du rapport ne remplace pas le rapport d’origine du concepteur.  Le partage avec des collègues qui ne disposent pas déjà d’un accès en lecture nécessite des autorisations de repartage. Si vous ne parvenez pas à partager votre vue du rapport, contactez le propriétaire du rapport pour demander l’autorisation de repartage.  


### <a name="share-changes"></a>Partager les modifications 
Si vous avez des autorisations de lecture et de repartage, vous pouvez choisir d’inclure vos modifications lorsque vous partagez le rapport.

:::image type="content" source="media/end-user-bookmarks/power-bi-personalize-share-changes.png" alt-text="Partage des modifications":::
 


## <a name="open-bookmarks"></a>Ouvrir des signets
Pour ouvrir le volet Signets, sélectionnez **Signets** > **Afficher d’autres signets** dans la barre de menus. 

![capture d’écran de canevas de rapport avec le volet Signets ouvert.](media/end-user-bookmarks/power-bi-show-bookmarks.png)

Pour revenir à la vue d’origine du rapport, sélectionnez l’icône **Réinitialiser**.

![capture d’écran avec l’icône de restauration sélectionnée](media/end-user-bookmarks/power-bi-revert.png)

### <a name="report-bookmarks"></a>Signets du rapport
Si le *concepteur* de rapports a créé des signets, vous les trouverez sous **Signets du rapport**. Cette page de rapport contient quatre signets : B1, B2, YTD VanArsdel et YTD complet. **YTD complet** est actuellement sélectionné.

> [!NOTE]
> Vous avez besoin de Power BI Pro ou Premium pour voir des rapports partagés. 

![Affichage des signets du rapport](media/end-user-bookmarks/power-bi-bookmark-list.png)

Sélectionnez un signet pour changer de vue de rapport. 

![Vidéo montrant la sélection de signets de rapport.](media/end-user-bookmarks/power-bi-bookmarks.gif)

### <a name="personal-bookmarks"></a>Signets personnels

Si vous pouvez afficher un rapport, vous pouvez également ajouter des signets personnels.  Lorsque vous créez un signet, les éléments suivants sont enregistrés :

* Page actuelle
* Filtres
* Segments, y compris le type de segments (par exemple, liste déroulante ou liste) et l’état des segment
* État de sélection des visuels (par exemple, filtres de mise en surbrillance croisée)
* Ordre de tri
* Emplacement d’exploration
* Visibilité (d’un objet, à l’aide du volet **Sélection**)
* Le mode focus ou **À la une** des objets visibles

Configurez une page de rapport comme vous souhaitez qu’elle apparaisse dans le signet. Dans cet exemple :

1. Nous avons modifié le filtre Date existant dans le volet **Filtres**,
1. modifié le filtre Régions existant dans le volet **Filtres** et
1.  sélectionné un point de données sur le visuel sous forme de diagramme donut, pour un filtrage et une mise en surbrillance croisés dans le canevas du rapport. 

Une fois que votre page de rapport et les visuels sont organisés comment vous le souhaitez, sélectionnez **Ajouter** dans le volet **Signets** pour ajouter un signet. 

![Ajout de signets personnels](media/end-user-bookmarks/power-bi-personal.png)

**Power BI** crée un signet personnel, puis lui donne un nom générique ou celui que vous spécifiez. Vous pouvez *renommer*, *supprimer* ou *mettre à jour* votre signet en sélectionnant les points de suspension en regard de son nom, puis en sélectionnant une action dans le menu qui apparaît.

Une fois le signet créé, affichez-le en le sélectionnant dans le volet **Signets**. 

![Affichez un signet particulier en le sélectionnant.](media/end-user-bookmarks/power-bi-selected.png)


<!--
## Arranging bookmarks
As you create bookmarks, you might find that the order in which you create them isn't necessarily the same order you'd like to present them to your audience. No problem, you can easily rearrange the order of bookmarks.

In the **Bookmarks** pane, simply drag-and-drop bookmarks to change their order, as shown in the following image. The yellow bar between bookmarks designates where the dragged bookmark will be placed.

![Change bookmark order by drag-and-drop](media/desktop-bookmarks/bookmarks_06.png)

The order of your bookmarks can become important when you use the **View** feature of bookmarks, as described in the next section. 

-->

## <a name="bookmarks-as-a-slide-show"></a>Signets en mode diaporama
Pour voir les signets dans l’ordre, sélectionnez **Afficher** dans le volet **Signets** afin de lancer un diaporama.

Le mode **Vue** offre quelques fonctionnalités utiles :

- Le nom du signet apparaît dans la barre de titre de celui-ci, qui apparaît au bas du canevas.
- La barre de titre des signets comporte des flèches permettant de passer au signet suivant ou précédent.
- Vous pouvez quitter le mode **Vue** en sélectionnant **Quitter** dans le volet **Signets** ou la croix (**X**) dans la barre de titre des signets.

![Diaporama des signets](media/end-user-bookmarks/power-bi-view-bookmarks.png)

Lorsque vous êtes en mode **Vue**, vous pouvez fermer le volet **Signets** (en cliquant sur le signe X sur ce volet) pour fournir davantage d’espace pour votre présentation. De plus, en mode **Vue**, tous les visuels sont interactifs et compatibles avec la sélection croisée, comme dans toute autre interaction. 

<!--
## Visibility - using the Selection pane
With the release of bookmarks, the new **Selection** pane is also introduced. The **Selection** pane provides a list of all objects on the current page and allows you to select the object and specify whether a given object is visible. 

![Enable the Selection pane](media/desktop-bookmarks/bookmarks_08.png)

You can select an object using the **Selection** pane. Also, you can toggle whether the object is currently visible by clicking the eye icon to the right of the visual. 

![Selection pane](media/desktop-bookmarks/bookmarks_09.png)

When a bookmark is added, the visible status of each object is also saved based on its setting in the **Selection** pane. 

It's important to note that **slicers** continue to filter a report page, regardless of whether they are visible. As such, you can create many different bookmarks, with different slicer settings, and make a single report page appear very different (and highlight different insights) in various bookmarks.


## Bookmarks for shapes and images
You can also link shapes and images to bookmarks. With this feature, when you click on an object, it will show the bookmark associated with that object. This can be especially useful when working with buttons; you can learn more by reading the article about [using buttons in Power BI](../create-reports/desktop-buttons.md). 

To assign a bookmark to an object, select the object, then expand the **Action** section from the **Format Shape** pane, as shown in the following image.

![Add bookmark link to an object](media/desktop-bookmarks/bookmarks_10.png)

Once you turn the **Action** slider to **On** you can select whether the object is a back button, a bookmark, or a Q&A command. If you select bookmark, you can then select which of your bookmarks the object is linked to.

There are all sorts of interesting things you can do with object-linked bookmarking. You can create a visual table of contents on your report page, or you can provide different views (such as visual types) of the same information, just by clicking on an object.

When you are in editing mode you can use ctrl+click to follow the link, and when not in edit mode, simply click the object to follow the link. 


## Bookmark groups

Beginning with the August 2018 release of **Power BI Desktop**, you can create and use bookmark groups. A bookmark group is a collection of bookmarks that you specify, which can be shown and organized as a group. 

To create a bookmark group, hold down the CTRL key and select the bookmarks you want to include in the group, then click the ellipses beside any of the selected bookmarks, and select **Group** from the menu that appears.

![Create a bookmark group](media/desktop-bookmarks/bookmarks_15.png)

**Power BI Desktop** automatically names the group *Group 1*. Fortunately, you can just double-click on the name and rename it to whatever you want.

![Rename a bookmark group](media/desktop-bookmarks/bookmarks_16.png)

With any bookmark group, clicking on the bookmark group's name only expands or collapses the group of bookmarks, and does not represent a bookmark by itself. 

When using the **View** feature of bookmarks, the following applies:

* If the selected bookmark is in a group when you select **View** from bookmarks, only the bookmarks *in that group* are shown in the viewing session. 

* If the selected bookmark is not in a group, or is on the top level (such as the name of a bookmark group), then all bookmarks for the entire report are played, including bookmarks in any group. 

To ungroup bookmarks, just select any bookmark in a group, click the ellipses, and then select **Ungroup** from the menu that appears. 

![Ungroup a bookmark group](media/desktop-bookmarks/bookmarks_17.png)

Note that selecting **Ungroup** for any bookmark from a group takes all bookmarks out of the group (it deletes the group, but not the bookmarks themselves). So to remove a single bookmark from a group, you need to **Ungroup** any member from that group, which deletes the grouping, then select the members you want in the new group (using CTRL and clicking each bookmark), and select **Group** again. 
-->


### <a name="reset-all-your-changes-to-a-report"></a>Réinitialiser toutes les modifications dans un rapport

Dans le coin supérieur droit de votre canevas de rapport, sélectionnez **Rétablir les valeurs par défaut**. Cela supprime toutes les modifications que vous avez apportées au rapport et revient au dernier affichage du rapport enregistré par l’auteur.

:::image type="content" source="media/end-user-bookmarks/power-bi-personalize-reset-all.png" alt-text="Réinitialisation de toutes les modifications":::



## <a name="limitations-and-considerations"></a>Considérations et limitations
Pour cette préversion de **signets**, vous devez garder à l’esprit les considérations et limitations suivantes.

* La plupart des visuels Power BI doivent fonctionner correctement avec les signets. Si vous rencontrez des problèmes avec les signets et un visuel personnalisé Power BI, contactez le créateur de celui-ci et demandez-lui d’ajouter la prise en charge des signets.    
* Si vous ajoutez un visuel sur une page de rapport après la création d’un signet, le visuel s’affiche dans son état par défaut. Cela signifie également que si vous introduisez un segment dans une page où vous avez précédemment créé des signets, le segment se comporte avec son état par défaut.
* En règle générale, vos signets ne sont pas affectés lorsque le *concepteur* met à jour ou republie un rapport. Toutefois, si le concepteur apporte des modifications majeures au rapport, par exemple, s’il supprime des champs utilisés par un signet, vous recevrez un message d’erreur la prochaine fois que vous tenterez d’ouvrir ce signet. 
* Cette fonctionnalité est prise en charge dans les applications mobiles Power BI pour les tablettes iOS et Android, ainsi que dans l’application Windows Power BI. Elle n’est pas prise en charge dans les applications mobiles Power BI pour les téléphones. Toutefois, les modifications de visuels enregistrées dans un signet personnel au sein du service Power BI sont respectées dans les applications mobiles Power BI.


## <a name="next-steps"></a>Étapes suivantes
[Personnaliser les visuels dans un rapport](end-user-personalize-visuals.md)
