---
title: Créer des rapports rapides dans le service Power BI
description: Il existe une nouvelle façon de créer rapidement des rapports dans le service Power BI. Collez les données directement dans Power BI sur le Web, et Power BI génère automatiquement les visuels pour vous.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 12/16/2020
LocalizationGroup: Reports
ms.openlocfilehash: 689c15994528df253de7d3d1b844ec0ef979d6da
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729857"
---
# <a name="create-quick-reports-in-the-power-bi-service"></a>Créer des rapports rapides dans le service Power BI 

Il existe une nouvelle façon de créer rapidement des rapports dans le service Power BI. Au lieu de télécharger l’application Power BI Desktop et d’importer les données, vous pouvez coller les données directement dans Power BI sur le Web, et Power BI génère automatiquement les visuels pour vous.  

Vous débutez dans la création avec Power BI ? Consultez l’article [Rapports dans Power BI](../consumer/end-user-reports.md) pour obtenir rapidement plus de contexte.

:::image type="content" source="media/service-quick-create-report/quick-create.gif" alt-text="Utilisez l’option Création rapide de Power BI pour créer rapidement un rapport.":::

## <a name="create-a-quick-report"></a>Créer un rapport rapide
Dans le volet de navigation du service Power BI, vous pouvez sélectionner le bouton **Créer** pour ouvrir une page dans laquelle vous pouvez sélectionner votre source de données. Cette option est également accessible à partir du bouton **Nouveau rapport** de la page d’accueil.

:::image type="content" source="media/service-quick-create-report/create-entry-point.png" alt-text="Créez une icône de point d’entrée dans le service Power BI."::: 

Actuellement, nous prenons uniquement en charge la création d’un rapport basé sur un jeu de données existant, ou la saisie ou le collage de données directement dans une table. Au fil du temps, vous verrez d’autres sources, notamment le chargement d’un fichier Excel.  

:::image type="content" source="media/service-quick-create-report/create-source-options.png" alt-text="Ajoutez des données pour créer un rapport, des options de source.":::

Lorsque vous choisissez de saisir ou de coller des données, vous recevez une grille dans laquelle vous pouvez commencer à saisir des données. Vous pouvez également coller des données à l’aide du raccourci Ctrl + V ou du menu contextuel.

:::image type="content" source="media/service-quick-create-report/create-enter-data-window.png" alt-text="Tapez ou collez dans la fenêtre Entrer des données.":::

Vous pouvez utiliser le menu contextuel pour ajouter et supprimer des colonnes. Si vos données collées incluent une ligne d’en-tête, sélectionnez **Utiliser la première ligne pour les en-têtes** pour promouvoir automatiquement la première ligne en ligne d’en-tête. Power BI détecte automatiquement les types de données, mais vous avez la possibilité de les définir manuellement. Sélectionnez le bouton **Type de données** en regard du nom de la colonne. 

:::image type="content" source="media/service-quick-create-report/change-data-type.png" alt-text="Modifiez le type de données de la colonne."::: 

À mesure que vous suivez le processus de création, Power BI crée un nouveau jeu de données pour vous et génère automatiquement un résumé de vos données. Ces visuels générés automatiquement transforment plus rapidement que jamais vos données brutes en insights.  

:::image type="content" source="media/service-quick-create-report/autogenerated-report.png" alt-text="Power BI crée automatiquement des visuels basés sur vos données.":::

Vous pouvez également facilement modifier les données du rapport. Utilisez le volet **Résumer** pour ajouter ou supprimer des champs du rapport. Sélectionnez et désélectionnez des champs pour mettre à jour ce que vous souhaitez mesurer et analyser. Power BI ajoute ou supprime automatiquement des graphiques pour afficher les nouvelles combinaisons.  

Actuellement, vous pouvez consulter un maximum de trois mesures, affichées sous forme de lignes dans le rapport, et quatre catégories, affichées sous forme de colonnes dans le rapport. 

:::image type="content" source="media/service-quick-create-report/summarize-pane.png" alt-text="Modifiez la façon dont Power BI résume les données dans le volet Résumer.":::

Pour afficher un résumé d’un champ d’une autre façon, utilisez le menu contextuel du champ dans le volet **Résumer** pour basculer entre somme, moyenne, maximum, minimum, etc. 

:::image type="content" source="media/service-quick-create-report/summarize-options.png" alt-text="Basculez entre somme, moyenne, maximum, minimum, etc.":::

Vous pouvez enregistrer ce rapport dans l’espace de travail dans lequel vous vous trouviez lorsque vous avez sélectionné pour la première fois l’option **Créer**. À partir de là, vous pouvez le partager, comme n’importe quel autre rapport. La prochaine fois que vous ou une autre personne disposant des autorisations de modification ouvrez le rapport, vous revenez à cette expérience de modification rapide.  

Si vous souhaitez basculer vers une expérience de modification complète, sélectionnez le bouton **Modifier** dans la barre de menus. Sachez toutefois qu’une fois que vous avez enregistré le rapport dans l’expérience de modification complète, vous ne pouvez pas revenir à la vue de modification rapide.  

:::image type="content" source="media/service-quick-create-report/edit-entry-point.png" alt-text="Sélectionnez le bouton Modifier dans la barre de menus.":::

Cette expérience devrait faciliter la création de rapports basés sur vos données et permettre à un tout nouveau groupe d'utilisateurs de profiter de la puissance de la création de rapports. Essayez dès aujourd’hui la nouvelle expérience de création.

## <a name="considerations-and-limitations"></a>Considérations et limitations

### <a name="licenses"></a>Licences

Vous avez besoin de la même licence pour créer un rapport rapide que pour créer un autre rapport dans Power BI. Si vous disposez d’une licence Power BI gratuite et que votre espace de travail est affecté à une capacité Premium, vous pouvez y créer des rapports rapides. Si vous disposez d’une licence Power BI Pro, vous pouvez créer des rapports rapides n’importe où dans le service Power BI. Consultez [Fonctionnalités du service Power BI par type de licence](../fundamentals/service-features-license-type.md) pour plus de détails.


### <a name="get-data-limitations"></a>Limitations relatives à l’option Obtenir des données 

- Si vous utilisez l’option **Coller ou entrer manuellement des données**, il n’existe actuellement aucun moyen de mettre à jour les données ultérieurement. Si vous souhaitez ajouter, modifier ou supprimer des données ultérieurement, vous devez à nouveau parcourir le flux de travail **Créer** et obtenir un nouveau rapport.  
- Si vous avez un fichier CSV ou Excel, vous devez utiliser l’option Coller pour ajouter vos données. Une option de chargement de fichier sera disponible ultérieurement. 
- Lorsque vous copiez des données dans la fenêtre **Entrer des données**, la taille des données que vous collez ne peut pas dépasser 512 ko. 
- Le nom de la table ne peut pas comporter plus de 80 caractères, et les noms des colonnes ne peuvent pas dépasser 512 caractères.  
- Les noms de table et de colonne ne peuvent pas contenir de guillemets doubles ("), de points (.) ou d'espaces blancs de début ou de fin.  

### <a name="model-limitations"></a>Limitations relatives au modèle

Lorsque vous suivez ce processus de création, vous créez un modèle en arrière-plan sur le Web. Ces modèles créés sur le Web sont similaires à ceux créés dans Power BI Desktop, mais ils présentent quelques limitations.

| Fonctionnalité | Statut  | Détails |
|---------|---------|---------|
| ALM | Non prise en charge pour le moment | ALM ne fonctionne pas pour les jeux de données créés via le Web. |
| BYOK (Bring Your Own Key) | Non prise en charge pour le moment | Vous ne pouvez pas utiliser votre propre clé de chiffrement pour les jeux de données créés via le Web. |
| Applications modèles | Non prise en charge pour le moment | Vous ne pouvez pas créer d’applications pour les espaces de travail avec des jeux de données créés via le Web. |  
| API publiques d’administration | Partiellement pris en charge | La plupart des API publiques d’administration sont prises en charge. Toutefois, il existe un problème connu avec l’opération suivante, **Admin - Groups GetGroupsAsAdmin avec les jeux de données développés**. Pour cette opération, les jeux de données créés via le Web sont retournés, mais ContentProviderType n’est pas correctement marqué comme « RealTime ». |

### <a name="report-limitations"></a>Limitations relatives au rapport  

Si vous utilisez l’option **Modifier** pour basculer en mode de modification complète et enregistrer le rapport, vous ne pouvez plus revenir à la vue générée automatiquement avec le volet Résumer. Power BI vous le rappelle lorsque vous sélectionnez **Modifier**.  

:::image type="content" source="media/service-quick-create-report/quick-create-switch-edit-mode.png" alt-text="Basculez du mode de modification au mode de création rapide.":::

## <a name="next-steps"></a>Étapes suivantes

* [Rapports dans Power BI](../consumer/end-user-reports.md)
* D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
