---
title: "Présentation des packs de contenu d’organisation dans Power BI"
description: "Consultez les informations relatives à la réalisation de packages de vos propres tableaux de bord, rapports, classeurs Excel et jeux de données, que vous pouvez partager avec vos collègues dans des packs de contenu d’organisation."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maggies
ms.openlocfilehash: 7ea0fbf09196af9ffecaf5ae54ea0754fdd44a0b
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Présentation des packs de contenu d’organisation dans Power BI
> [!NOTE]
> Avez-vous déjà entendu parler des nouvelles *applications*? Les applications sont la nouvelle méthode pour distribuer du contenu à un large public dans Power BI. Nous recommandons d’utiliser des applications plutôt que des packs de contenu d’organisation ou des espaces de travail en lecture seule. En savoir [plus sur les applications](service-install-use-apps.md).
> 
> 

Vous distribuez régulièrement des rapports par courrier électronique à votre équipe ? Essayez cette opération à la place : faites des packages de vos tableaux de bord, rapports, classeurs Excel et jeux de données, et partagez-les avec votre équipe sous forme de *pack de contenu d’organisation*. Les packs de contenu que vous créez sont faciles à trouver par votre équipe, car ils sont regroupés dans AppSource. Dans la mesure où ils font partie de Power BI, ils bénéficient de toutes les fonctionnalités de Power BI, notamment l’exploration interactive des données, de nouveaux éléments visuels, les Questions et réponses, l’intégration à d’autres sources de données, l’actualisation des données, et bien plus encore.

![](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

La création de packs de contenu est différente du partage de tableaux de bord ou de la collaboration sur ces derniers dans un espace de travail d’application. Pour déterminer l’option la plus adaptée à votre situation, consultez [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md). 

Dans AppSource, vous pouvez parcourir ou rechercher les packs de contenu publiés à l’ensemble de l’organisation, à des groupes de distribution ou de sécurité, ainsi qu’à des [groupes Office 365 auxquels vous appartenez](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9). Si vous n’êtes pas membre d’un groupe spécifique, vous ne voyez pas les packs de contenu partagés avec ce groupe. Tous les membres du groupe ont le même accès en lecture seule aux données des packs de contenu, rapports, classeurs et tableaux de bord (sauf s’il s’agit d’une source de données SQL Server Analysis Services (SSAS), auquel cas vos privilèges sont hérités avec la source de données).

Les tableaux de bord, rapports et classeurs Excel sont en lecture seule. Toutefois, vous pouvez copier les tableaux de bord et les rapports pour vous en servir comme point de départ afin de créer votre propre version personnalisée du pack de contenu.

> [!NOTE]
> Les packs de contenu d’organisation sont disponibles seulement si vos collègues et vous-même disposez de [Power BI Pro](service-free-vs-pro.md).
> 
> 

## <a name="what-is-appsource"></a>Qu’est-ce qu’*AppSource* ?
La publication d’un pack de contenu d’organisation l’ajoute à AppSource.  Ce dépôt centralisé permet à des membres de parcourir et de découvrir facilement des tableaux de bord, des rapports et des jeux de données publiés pour eux.  

* Pour afficher AppSource, sélectionnez **Obtenir les données** > **Mon organisation** > **Obtenir**.

En savoir plus sur [la recherche et l’ouverture des packs de contenu d’organisation](service-organizational-content-pack-find-and-open.md).

## <a name="the-life-cycle-of-an-organizational-content-pack"></a>Cycle de vie d’un pack de contenu d’organisation
Tout utilisateur Power BI Pro peut créer et publier des packs de contenu d’organisation, et y accéder. Seul le créateur du pack de contenu peut modifier le classeur et le jeu de données, planifier l’actualisation et le supprimer.

Le cycle de vie ressemble à ceci :

1. Dans Power BI Pro, Nate crée un pack de contenu et le publie dans le groupe de distribution Marketing. Les paramètres d’actualisation sont hérités avec le jeu de données et peuvent être modifiés uniquement par Nate.
   
   > [!NOTE]
   > Si Nate crée le pack de contenu au sein d’un [espace de travail Power BI](service-create-distribute-apps.md) auquel il appartient, même s’il quitte cet espace de travail, d’autres utilisateur de l’espace de travail Power BI peuvent en prendre possession.
   > 
   > 
2. Nate envoie un message au groupe de distribution, en lui donnant des informations sur le nouveau pack de contenu.
3. Dans Power BI Pro, Jane, un membre du groupe de distribution Marketing, recherche ce pack de contenu et s’y connecte dans AppSource. Elle en possède maintenant une copie en lecture seule.  Elle sait qu’il est en lecture seule, car dans le volet de navigation gauche, une icône de partage est affichée à gauche du nom du tableau de bord et du nom des rapports. Quand elle sélectionne le tableau de bord, une icône de verrou indique à Jane qu’elle consulte un tableau de bord de pack de contenu. 
4. Par exemple, elle décide de le personnaliser. Elle dispose maintenant de sa propre copie du tableau de bord et des rapports. Son travail n’affecte pas la source, le pack de contenu d’origine ou d’autres membres du groupe de distribution. Elle travaille maintenant sur sa propre copie du tableau de bord et des rapports.
5. Nate apporte des mises à jour au tableau de bord, puis publie une nouvelle version du pack de contenu.
   
   * Julio, un autre membre du groupe de distribution, n’a pas personnalisé le pack de contenu d’origine. Les nouvelles modifications sont automatiquement appliquées à sa version du pack de contenu.  
   * Jane a personnalisé le pack de contenu. Elle reçoit une notification indiquant qu’il existe une nouvelle version.  Elle peut accéder à AppSource et obtenir le pack de contenu mis à jour sans perdre sa version personnalisée. Elle a désormais 2 versions : sa version personnalisée et le pack de contenu mis à jour.
6. Par exemple, Nate modifie les paramètres de sécurité. Julio et Jane n’ont plus accès au contenu. Supposons par exemple qu’ils sont supprimés du groupe de distribution Marketing.
   
   * Julio n’a pas personnalisé le pack de contenu d’origine : le contenu est donc automatiquement supprimé. 
   * Jane a personnalisé le pack de contenu. La prochaine fois qu’elle ouvre le tableau de bord, toutes les vignettes provenant du pack de contenu d’origine ont disparu, mais les vignettes qu’elle a épinglées à partir d’autres rapports (qu’elle a toujours l’autorisation d’utiliser) sont toujours présentes. Les rapports et le jeu de données associés ne sont plus disponibles (et n’apparaissent pas dans son volet de navigation gauche).
7. Ou bien, Nate supprime le pack de contenu.
   
   * Julio n’a pas personnalisé le pack de contenu d’origine : le contenu est donc automatiquement supprimé. 
   * Jane a personnalisé le pack de contenu. La prochaine fois qu’elle ouvre le tableau de bord, toutes les vignettes provenant du pack de contenu d’origine ont disparu, mais les vignettes qu’elle a épinglées à partir d’autres rapports sont toujours présentes. Les rapports et le jeu de données associés ne sont plus disponibles (et n’apparaissent pas dans son volet de navigation gauche).

## <a name="data-security"></a>Sécurité des données
Tous les membres d’un groupe de distribution ont les mêmes autorisations sur les données que le créateur du pack de contenu. Les jeux de données tabulaires locaux SSAS (SQL Server Analysis Services) sont la seule exception. Étant donné que les rapports et les tableaux de bord se connectent en direct au modèle SSAS local, les informations d’identification de chaque membre du groupe de distribution sont utilisées pour déterminer les données auxquelles celui-ci peut accéder.

## <a name="next-steps"></a>Étapes suivantes
* [Créer et publier un pack de contenu d’organisation](service-organizational-content-pack-create-and-publish.md)
* [Créer et distribuer une application dans Power BI](service-create-distribute-apps.md) 
* [Power BI – Concepts de base](service-basic-concepts.md)
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
