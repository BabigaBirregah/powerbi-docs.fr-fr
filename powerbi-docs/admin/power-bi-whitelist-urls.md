---
title: Ajout des URL Power BI à la liste verte
description: Cet article présente les points de terminaison d’URL et les ports à ajouter sur liste verte pour bénéficier d’une connectivité à Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: 1495400a59d8250f407a5f7415a550871501e4e3
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96577506"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>Ajout des URL Power BI à la liste verte
[//]: # "suparnap, miwehnia et natham sont les contacts pour la gestion de cette liste"

Le service Power BI exige une connectivité à Internet. Les points de terminaison qui figurent dans les tableaux de cet article doivent être accessibles aux clients qui utilisent le service Power BI.

Pour utiliser le service Power BI, vous devez être en mesure de vous connecter aux points de terminaison marqués **obligatoires** dans les tableaux ci-dessous et aux points de terminaison marqués **obligatoires** sur les sites liés. Si le lien vers un site externe fait référence à une section spécifique, vous devez seulement passer en revue les points de terminaison de cette section.

Les points de terminaison marqués **facultatifs** peuvent également être ajoutés aux listes vertes pour que des fonctionnalités spécifiques puissent fonctionner.

Avec le service Power BI, seul le port TCP 443 doit être ouvert pour les points de terminaison listés.

Les caractères génériques (*) représentent tous les niveaux sous le domaine racine, et nous utilisons N/A quand les informations ne sont pas disponibles. La colonne **Destination(s)** comporte les noms de domaine et des liens vers des sites externes, qui contiennent des informations complémentaires sur les points de terminaison.

>[!Important]
>Les informations figurant dans les tableaux ci-dessous ne s’appliquent pas à Power BI Allemagne, à Power BI Chine géré par 21Vianet ni à Power BI US Government. Pour plus d’informations sur la communication entre les services cloud, consultez [Connexion entre les services cloud Azure du secteur public et les services cloud Azure globaux](service-govus-overview.md#connect-government-and-global-azure-cloud-services).

## <a name="authentication"></a>Authentification

Power BI dépend des points de terminaison obligatoires dans les sections relatives à l’authentification et à l’identité Microsoft 365. Pour utiliser Power BI, vous devez être en mesure de vous connecter aux points de terminaison dans le site lié ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** Authentification et identité | Consultez la documentation pour connaître les [URL Microsoft 365 et Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online).  | N/A |

## <a name="general-site-usage"></a>Utilisation générale du site

Pour l’utilisation générale de Power BI, vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** API de back-end | api.powerbi.com | TCP 443 |
| 2 | **Obligatoire :** API de back-end | *.analysis.windows.net | TCP 443 |
| 3 | **Obligatoire :** API de back-end | *.pbidedicated.windows.net | TCP 443 |
| 4 | **Obligatoire :** Réseau de distribution de contenu (CDN) | content.powerapps.com | TCP 443 |
| 5 | **Obligatoire :** Intégration de Microsoft 365 | Consultez la documentation pour connaître les [URL Microsoft 365 et Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/A |
| 6 | **Obligatoire :** Portail | *.powerbi.com | TCP 443 |
| 7 | **Obligatoire :** Données de télémétrie du service | dc.services.visualstudio.com | TCP 443 |
| 8 | **Facultatif :** Messages d’information | dynmsg.modpim.com | TCP 443 |
| 9 | **Facultatif :** Sondages NPS | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administration

Pour effectuer des fonctions d’administration dans Power BI, vous devez être en mesure de vous connecter aux points de terminaison des sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** Pour la gestion des utilisateurs et la consultation des journaux d’audit | Consultez la documentation pour connaître les [URL Microsoft 365 et Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/A |
| | | |

## <a name="getting-data"></a>Obtention de données

Pour obtenir des données auprès de sources de données spécifiques, comme OneDrive, vous devez être en mesure de vous connecter aux points de terminaison dans le tableau ci-dessous. L’accès à des domaines Internet et URL supplémentaires peut être nécessaire pour les sources de données spécifiques utilisées dans votre organisation.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** AppSource (applications internes ou externes dans Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Facultatif :** Se connecter et obtenir des données pour les packs de contenu | Dépend des packs de contenu utilisés | Dépend des packs de contenu utilisés |
| 3 | **Facultatif :** Importation de fichiers à partir de OneDrive - Personnel | Consultez le site [URL et ports nécessaires pour OneDrive](/onedrive/required-urls-and-ports) | N/A |
| 4 | **Facultatif :** Vidéo du tutoriel Power BI en 60 secondes | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Facultatif :** Sources de données de streaming PubNub | Consultez la [documentation de PubNub](https://support.pubnub.com/hc/en-us/categories/360004336832-PubNub-101) | N/A |
| | | |

## <a name="dashboard-and-report-integration"></a>Intégration des tableaux de bord et des rapports

Power BI dépend de certains points de terminaison pour prendre en charge vos tableaux de bord et vos rapports. Vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** Intégration d’Excel | Consultez la documentation pour connaître les [URL des services communs Microsoft 365 et Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/A |
| | | |

## <a name="power-bi-visuals"></a>Visuels Power BI

Power BI dépend de certains points de terminaison pour voir et accéder aux visuels Power BI. Vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** Importer un visuel personnalisé à partir de l’interface de Place de marché ou d’un fichier | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Facultatif :** Bing Maps | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Facultatif :** PowerApps | Consultez la [section Services requis](/powerapps/maker/canvas-apps/limits-and-config#required-services) sur site de la configuration système requise pour PowerApps | N/A |
| 4 | **Facultatif :** Visio | Consultez la documentation relatives aux [URL des services communs Microsoft 365 et Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), ainsi qu’à [SharePoint Online et OneDrive Entreprise](/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business). | N/A |
| | | |

## <a name="related-external-sites"></a>Sites externes connexes

Power BI établit des liaisons vers d’autres sites connexes. Ces sites hébergent la documentation, le support, les demandes de nouvelles fonctionnalités, etc. L’accès à ces sites n’a pas d’incidence sur les fonctionnalités de Power BI. Il est donc facultatif de les ajouter aux listes vertes.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Facultatif :** Site de la Communauté | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Facultatif :** Site de documentation | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Facultatif :** Site de téléchargement (pour Power BI Desktop, etc.) | download.microsoft.com | TCP 443 |
| 4 | **Facultatif :** Redirections externes | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Facultatif :** Site des commentaires sur les idées| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Facultatif :** Site Power BI ; page d’arrivée, liens vers des informations supplémentaires, site de support, liens de téléchargement, présentation des partenaires, etc. | powerbi.microsoft.com | TCP 443 |
| 7 | **Facultatif :** Centre de développement Power BI | dev.powerbi.com | TCP 443 |
| 8 | **Facultatif :** Site du support technique | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
