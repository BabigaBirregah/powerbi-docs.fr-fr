---
title: Collaborer dans Microsoft Teams avec Power BI
description: À une époque où la dispersion des effectifs se généralise, de plus en plus d’organisations font appel à Microsoft Teams pour permettre à leurs employés de télétravailler tout en se synchronisant les uns avec les autres.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 12/14/2020
ms.openlocfilehash: 7c8fa59521be1cfc8bb25fb04c3904f257fb62be
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926688"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Collaborer dans Microsoft Teams avec Power BI

À une époque où la dispersion des effectifs se généralise, de plus en plus d’organisations font appel à Microsoft Teams pour permettre à leurs employés de télétravailler tout en se synchronisant les uns avec les autres. Cet article présente les possibilités de partage de contenu Power BI interactif et de collaboration dans les canaux et conversations Microsoft Teams. 

- Avec l’onglet **Power BI** pour Microsoft Teams, vous pouvez [incorporer des rapports interactifs dans les canaux et les conversations Microsoft Teams](service-embed-report-microsoft-teams.md). L’onglet Power BI aide vos collègues à trouver les données de votre équipe et à discuter des données dans les canaux de votre équipe. 
- Créez un [aperçu de lien](service-teams-link-preview.md) quand vous collez un lien vers vos rapports, tableaux de bord et applications dans la boîte de message Microsoft Teams. L’aperçu de lien montre des informations sur le lien. 
- Utilisez [Discuter dans Microsoft Teams](service-share-report-teams.md) quand vous consultez des rapports et des tableaux de bord dans le service Power BI pour lancer rapidement des conversations dans Microsoft Teams.
- Utilisez l’application [Power BI dans Microsoft Teams](service-microsoft-teams-app.md) pour ajouter à Microsoft Teams toute l’expérience du service Power BI de base.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Capture d’écran d’un rapport Power BI incorporé dans un canal Microsoft Teams":::

## <a name="requirements"></a>Configuration requise

En général, pour que Power BI fonctionne dans Microsoft Teams, vérifiez les éléments suivants :

- Vos utilisateurs ont une licence Power BI Pro ou que le rapport est contenu dans une [capacité Power BI Premium (référence SKU EM ou P)](../admin/service-premium-what-is.md) avec une licence Power BI.
- Les utilisateurs se sont connectés au service Power BI pour activer leur licence Power BI.
- Les utilisateurs remplissent les conditions requises pour utiliser l’onglet **Power BI** dans Microsoft Teams.

## <a name="grant-access-to-reports"></a>Accorder l’accès aux rapports

L’incorporation d’un rapport dans Microsoft Teams ou l’envoi d’un lien vers un élément n’accorde pas automatiquement aux utilisateurs l’autorisation d’afficher le rapport. Vous devez [permettre aux utilisateurs d’afficher le rapport dans Power BI](service-share-dashboards.md). Vous pouvez utiliser un groupe Microsoft 365 pour votre équipe afin de faciliter la tâche.

> [!IMPORTANT]
> Veillez à passer en revue les utilisateurs qui peuvent afficher le rapport dans le service Power BI et à accorder l’accès à ceux qui ne sont pas répertoriés.

Pour garantir que tous les membres d’une équipe ont accès aux rapports, vous pouvez les placer dans un même espace de travail et accorder au groupe Microsoft 365 pour votre équipe l’accès.

## <a name="share-with-external-users"></a>Partager avec des utilisateurs externes

Vous pouvez intégrer un rapport Power BI dans Teams et le partager avec des utilisateurs externes. Voici la procédure à suivre :

1.  Vous invitez l’utilisateur externe dans l’organisation et il accepte votre invitation. Pour plus d’informations, consultez [Distribuer du contenu Power BI à des utilisateurs invités externes avec Azure Active Directory B2B](../guidance/whitepaper-azure-b2b-power-bi.md).
2.  Accordez à l’utilisateur externe une autorisation sur le rapport. L’attribution d’autorisations individuelles est ce qui fonctionne mieux.
3.  Vérifiez qu’une licence Power BI a été attribuée à l’utilisateur externe. Si le contenu se trouve dans une capacité Premium, l’utilisateur a seulement besoin d’une licence gratuite. Si ce n’est pas le cas, l’utilisateur peut [s’inscrire pour un essai gratuit de Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).

## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

- Power BI ne prend pas en charge les mêmes langues localisées que Microsoft Teams. Par conséquent, vous risquez de ne pas voir la localisation appropriée dans le rapport incorporé.
- Les tableaux de bord Power BI ne peuvent pas être incorporés dans l’onglet **Power BI** pour Microsoft Teams.
- Un utilisateur sans licence Power BI ni autorisation d’accès pour le rapport voit un message « Ce contenu n’est pas disponible ».
- Vous pourriez rencontrer des problèmes si vous utilisez Internet Explorer 10. <!--You can look at the [browsers support for Power BI](../fundamentals/power-bi-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Les [filtres d’URL](service-url-filters.md) ne sont pas pris en charge avec l’onglet **Power BI** pour Microsoft Teams.
- Dans les clouds nationaux, le nouvel onglet **Power BI** n’est pas disponible. Une version plus ancienne peut être disponible, qui ne prend pas en charge la nouvelle expérience ni les rapports dans les applications Power BI.
- Une fois que vous avez enregistré l’onglet, vous ne pouvez pas changer son nom via les paramètres des onglets. Utilisez l’option **Renommer** pour le changer.
- L’authentification unique n’est pas prise en charge pour le service d’aperçu de lien.
- Les aperçus de lien ne fonctionnent pas dans les conversations des réunions ni dans les canaux privés.

## <a name="microsoft-power-platform-in-microsoft-teams"></a>Microsoft Power Platform dans Microsoft Teams

Les autres applications Microsoft Power Platform s’intègrent également à Microsoft Teams.

- [Expérience d’administration de Power Platform](/power-platform/admin/about-teams-environment)
- [Power Automate](/power-automate/teams/overview)
- [Power Apps](/powerapps/teams/overview)
- [Power Virtual Agents](/power-virtual-agents/)

## <a name="next-steps"></a>Étapes suivantes

- [Incorporer du contenu Power BI dans Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Obtenir un aperçu de lien Power BI dans Microsoft Teams](service-teams-link-preview.md)
- [Discuter dans Microsoft Teams directement à partir du service Power BI](service-share-report-teams.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
