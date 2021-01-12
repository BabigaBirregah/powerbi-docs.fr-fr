---
title: Power BI for les clients du gouvernement des États-Unis – Vue d’ensemble
description: Les clients du gouvernement des États-Unis peuvent ajouter un abonnement Power BI à leur offre Microsoft 365 Secteur Public. Découvrez comment vous inscrire, vous connecter et connaître la disponibilité des fonctionnalités dans cette description du service.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/05/2021
ms.custom: gcc
LocalizationGroup: Get started
ms.openlocfilehash: 9b52e0698f6b9c1ae779bf21738acee30db7447d
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97927094"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI pour les clients du gouvernement des États-Unis

Cet article est destiné aux clients du gouvernement des États-Unis qui déploient Power BI dans le cadre d’une offre Microsoft 365 Secteur Public. Les abonnements Secteur Public sont prévus pour répondre aux besoins spécifiques des organisations qui doivent respecter les normes de conformité et de sécurité des États-Unis. Le service Power BI conçu pour les clients du gouvernement des États-Unis est différent de la version commerciale du service Power BI. Les différences de fonctionnalités sont décrites dans les sections qui suivent.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Ajouter Power BI à votre offre Microsoft 365 Secteur Public

Pour obtenir un abonnement Power BI pour le gouvernement des États-Unis et affecter des licences aux utilisateurs, vous devez vous inscrire à une offre Microsoft 365 Secteur Public. Si votre organisation dispose déjà d’une offre Microsoft 365 Secteur Public, passez directement à [Achat d’un abonnement Power BI Pro pour les clients du gouvernement](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>S’inscrire à un plan Microsoft 365 Secteur Public

Si vous êtes un nouveau client, vous devez valider l’admissibilité de votre organisation pour pouvoir vous inscrire à un abonnement Microsoft 365 Secteur Public.  Commencez par compléter le [formulaire de validation de l’admissibilité Microsoft 365 Secteur Public](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Pour sélectionner un abonnement adapté à votre organisation, consultez la [description des services Microsoft 365 pour le gouvernement des États-Unis](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Si vous avez déjà déployé Power BI dans un environnement commercial et que vous souhaitez migrer vers le cloud du gouvernement des États-Unis, vous devez ajouter un nouvel abonnement Power BI Pro à votre offre Microsoft 365 Secteur Public. Ensuite, répliquez les données commerciales sur le service Power BI pour le gouvernement des États-Unis, supprimez les attributions de licences commerciales des comptes d’utilisateurs, puis affectez une licence Power BI Pro Secteur Public aux comptes d’utilisateurs.
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Acheter un abonnement Power BI Pro pour les clients du secteur public

Après avoir déployé Microsoft 365, vous pouvez ajouter un abonnement Power BI Pro. Suivez l’aide pas à pas [Inscription d’une organisation du gouvernement des États-Unis](service-govus-signup.md) pour acheter le service Power BI Pro Secteur Public. Achetez suffisamment de licences pour tous les utilisateurs qui doivent utiliser Power BI, puis attribuez-les aux différents comptes d’utilisateur.

> [!IMPORTANT]
> Power BI pour le gouvernement des États-Unis n’est pas disponible sous licence *gratuite*. Chaque utilisateur doit disposer d’une licence *Pro* pour pouvoir accéder au cloud de la communauté du secteur public. Un compte d’utilisateur qui dispose d’une licence gratuite n’est autorisé à accéder qu’au cloud commercial et rencontrera des problèmes d’authentification et d’accès. Si vous avez acheté Power BI Premium, vous n’êtes pas obligé d’attribuer des licences Pro pour permettre l’accès des utilisateurs.  Les utilisateurs de l’organisation peuvent accéder aux rapports partagés avec eux tant que le rapport est publié sur une capacité Premium. Pour connaître les différences entre les types de licences, consultez [Fonctionnalités du service Power BI par type de licence](../fundamentals/service-features-license-type.md).
>

## <a name="government-cloud-instances"></a>Instances du cloud pour le secteur public

Microsoft 365 propose différents environnements pour les organismes gouvernementaux qui répondent à différentes exigences de conformité. Pour plus d’informations sur chaque environnement, consultez :

* Le [Cloud de la communauté du secteur public (GCC) Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) est conçu pour les administrations fédérales, nationales et locales.

* Le [Cloud de la communauté du secteur public High (GCC High) Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) est conçu pour les agences fédérales, le secteur de la défense, l’industrie aéronautique et d’autres organisations détenant des informations protégées non classées. Cet environnement est adapté aux organisations de sécurité nationale et aux entreprises disposant de données ITAR (International Traffic in Arms Regulations) ou soumises à des exigences DFARS (Defense Federal Acquisition Regulation Supplement).

* [L’environnement Microsoft 365 DoD](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) est conçu exclusivement pour le département de la Défense des États-Unis.


## <a name="sign-in-to-power-bi-for-us-government"></a>Se connecter à Power BI pour l’État fédéral américain

L’URL de connexion à Power BI diffère pour les utilisateurs du secteur public et les utilisateurs commerciaux. Pour vous connecter à Power BI, utilisez les URL suivantes :

| Version commerciale  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Votre compte peut être configuré dans plusieurs clouds. Si votre compte est configuré ainsi, lorsque vous utilisez Power BI Desktop, vous pouvez choisir à quel cloud vous connecter.

## <a name="allow-connections-to-power-bi"></a>Autoriser les connexions à Power BI

Pour utiliser le service Power BI, vous devez autoriser les connexions aux points de terminaison nécessaires sur Internet. Ces destinations doivent être accessibles pour permettre à votre propre réseau, à Power BI et aux autres services dépendants de communiquer entre eux.

Dans le tableau ci-dessous, nous listons les points de terminaison que vous devez ajouter à votre liste d’autorisation de façon à activer la connexion au service Power BI pour une utilisation de site générale. Ces points de terminaison sont propres au cloud US Government. Avec le service Power BI, seul le port TCP 443 doit être ouvert pour les points de terminaison listés. Les points de terminaison axés sur l’obtention de données, l’intégration des tableaux de bord et des rapports, les visuels Power BI et d’autres services facultatifs ne sont pas uniques au cloud US Government. Pour aussi ajouter ces URL à votre liste d’autorisation, consultez [Ajouter des URL Power BI à votre liste d’autorisation](power-bi-whitelist-urls.md).

L’authentification, l’identité et l’administration de Power BI sont dépendantes de la connectivité aux services Microsoft 365. Vous devez aussi vous connecter à Microsoft 365 pour consulter les journaux d’audit. Pour identifier les points de terminaison de ces services, consultez Intégration de Microsoft 365 dans le tableau ci-dessous.

### <a name="power-bi-urls-for-general-site-usage"></a>URL Power BI pour une utilisation de site générale

|  Objectif | Destination |
| ---- | ----- |
| API de back-end | **GCC** : api.powerbigov.us |
| | **GCC-High** : api.high.powerbigov.us |
| | **DoD** : api.mil.powerbi.gov.us |
| API de back-end | **GCC** : *analysis.usgovcloudapi.net |
| | **GCC High** : *.high.analysis.usgovcloudapi.net |
| | **DoD** : *.mil.analysis.usgovcloudapi.net |
| API de back-end | **All** : *.pbidedicated.usgovcloudapi.net |
| Réseau de distribution de contenu (CDN) | **GCC** : gov.content.powerapps.us |
| | **GCC High** : high.content.powerapps.us |
| | **DoD** : mil.content.powerapps.us |
| Intégration de Microsoft 365 | **GCC** : [Points de terminaison internationaux](/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| | **GCC High** : [Points de terminaison US Government GCC High](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints) |
| | **DoD** : [Points de terminaison US Government DoD](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints) |
| Portail |**GCC** : *.powerbigov.us |
| | **GCC-High** : *.high.powerbigov.us |
| | **DoD** : *.mil.powerbigov.us |
| Données de télémétrie du service | **All** : dc.services.visualstudio.us |
| Messages d'information (facultatif) | **All** : dynmsg.modpim.com |
| Enquêtes NPS (facultatif) | **All** : nps.onyx.azure.net |

## <a name="connect-government-and-global-azure-cloud-services"></a>Connexion entre le service Azure Cloud pour le secteur public et le service Azure Cloud mondial

Azure est réparti sur plusieurs clouds. Par défaut, vous pouvez activer des règles de pare-feu pour ouvrir une connexion à une instance propre au cloud, mais la mise en réseau entre clouds est différente.  Pour communiquer entre les services du cloud public et ceux du Cloud de la communauté du secteur public, vous devez configurer des règles de pare-feu spécifiques. Par exemple, si vous souhaitez accéder à des instances de cloud public d’une base de données SQL à partir de votre déploiement cloud pour le secteur public de Power BI, il vous faut une règle de pare-feu dans la base de données SQL. Configurez des règles de pare-feu spécifiques dans les bases de données SQL afin d’autoriser les connexions au cloud Azure Government pour les centres de données suivants :

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona
* Est des États-Unis – US DoD
* Centre des États-Unis – US DoD

Pour obtenir celles du cloud du gouvernement des États-Unis, téléchargez le fichier [Plages d’adresses IP et balises de service Azure – Cloud du gouvernement des États-Unis](https://www.microsoft.com/download/details.aspx?id=57063). Les plages sont listées pour Power BI et Power Query.

Pour plus d’informations sur les services cloud Microsoft Azure Government, consultez [Documentation Azure Government](/azure/azure-government/).

Pour configurer des pare-feu pour les bases de données SQL, consultez [Créer et gérer des règles de pare-feu IP](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilité des fonctionnalités de Power BI

Pour répondre aux besoins des clients du cloud pour le secteur public, il existe quelques différences entre les offres pour le gouvernement et les offres commerciales. Notre objectif est de rendre toutes les fonctionnalités disponibles dans les clouds du secteur public dans un délai de 30 jours de disponibilité générale. Dans certains cas, les dépendances sous-jacentes nous empêchent de rendre une fonctionnalité disponible. La liste ci-dessous présente les fonctionnalités qui ne sont pas encore disponibles dans un environnement de secteur public particulier ou qui sont disponibles avec des fonctionnalités limitées. La liste utilise la clé suivante :

|Clé |Description|
|-----|------|
|![disponible](../media/yes.png)|La fonctionnalité est disponible dans l’environnement, hormis les exceptions définies dans les notes de bas de page.|
|![non disponible](../media/no.png)| La fonctionnalité n’est pas disponible dans l’environnement et nous n’avons pas de date de mise à disposition à communiquer pour le moment.|

En cas de lancement prévu pour un environnement donné, nous indiquons le trimestre auquel elle devrait être mise à disposition.

|Caractéristique |GCC |GCC High |DoD|
|------|------|------|------|
|[Azure B2B Collaboration entre le cloud public et le cloud commercial](service-admin-azure-ad-b2b.md)<sup>1</sup>|![disponible](../media/yes.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|
|[Incorporation dans SharePoint Online à l’aide du composant WebPart Power BI](/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![disponible](../media/yes.png)|![Disponible](../media/yes.png)|![non disponible](../media/no.png)|
|[Connectivité Power Automate pour les alertes de données](../connect-data/power-bi-data-sources.md)|![disponible](../media/yes.png)|![disponible](../media/yes.png)|![non disponible](../media/no.png)|
|[Onglet Power BI dans Teams](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>2</sup>|![disponible](../media/yes.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|
|[Grands modèles](service-premium-large-models.md) | ![non disponible](../media/no.png) |![non disponible](../media/no.png)| ![non disponible](../media/no.png) |
|[Dataflows - Optimisation du moteur de calcul SQL](../transform-model/dataflows/dataflows-premium-features.md) | ![non disponible](../media/no.png) |![non disponible](../media/no.png)| ![non disponible](../media/no.png) |
|[Dataflows - Requête directe](../transform-model/dataflows/dataflows-configure-consume.md) | ![non disponible](../media/no.png) |![non disponible](../media/no.png)|![non disponible](../media/no.png)|
|[Protection des données (étiquettes MIP)](service-security-sensitivity-label-overview.md)|![non disponible](../media/no.png)|![non disponible](../media/no.png) |![non disponible](../media/no.png)|
|[Applications modèles](../connect-data/service-template-apps-overview.md)<sup>3</sup>|![non disponible](../media/no.png) |![non disponible](../media/no.png)| ![non disponible](../media/no.png)|
|[Visuels personnalisés](../developer/visuals/power-bi-custom-visuals.md)<sup>3</sup>|![non disponible](../media/no.png) |![non disponible](../media/no.png)| ![non disponible](../media/no.png)|
|[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-power-bi-dashboard)| ![non disponible](../media/no.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|
|[Connecteur de données de qualité d’appel](/microsoftteams/cqd-power-bi-connector)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|
|[Apportez votre propre stockage (Azure Data Lake Gen2)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|
|[Génération d’un code QR](../create-reports/service-create-qr-code-for-tile.md)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|

<sup>1</sup> B2B Collaboration est disponible pour GCC, à condition que l’utilisateur externe dispose d’une licence dans cet environnement. Les licences Cloud commercial ne sont pas valides dans GCC. Pour plus d’informations sur les limitations connues de B2B Collaboration pour le gouvernement américain, lisez la [comparaison entre Azure Government et Azure international](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2).

<sup>2</sup> L’expérience Power BI dans Teams pour GCC est limitée : elle fonctionne uniquement pour les espaces de travail classiques et n’inclut pas les fonctionnalités améliorées décrites dans [Incorporer du contenu Power BI dans Microsoft Teams](../collaborate-share/service-embed-report-microsoft-teams.md).

<sup>3</sup> Lors de la publication, la fonctionnalité pour les applications modèles et les visuels personnalisés sera limitée aux clouds du secteur public. Des informations supplémentaires sur des limitations spécifiques seront publiées au moment de la publication.

## <a name="next-steps"></a>Étapes suivantes

* [Inscription à Power BI pour le gouvernement des États-Unis](service-govus-signup.md)
* [Microsoft Power Apps US Government](/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](/power-automate/us-govt)
* [Démonstration de Power BI US Government](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)
