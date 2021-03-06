---
title: Conseils pour créer des applications modèles dans Power BI
description: Conseils sur la création de requêtes, de modèles de données, de rapports et de tableaux de bord pour concevoir des applications modèles de qualité
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
ms.openlocfilehash: b20bb007c55f7d7d618b70690475d34d9f53fc06
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491710"
---
# <a name="tips-for-authoring-template-apps-in-power-bi"></a>Conseils pour créer des applications modèles dans Power BI

Quand [vous créez une application modèle](service-template-apps-create.md) dans Power BI, une partie du travail consiste à créer l’espace de travail associé, à tester l’application et à mettre l’application finalisée en production. L’autre part importante du travail est bien sûr la création du rapport et du tableau de bord de l’application. Nous pouvons décomposer le processus de création en quatre composants principaux. Bien définir ces composants vous aide à créer une application modèle de qualité :

* Avec les **requêtes**, vous [connectez](desktop-connect-to-data.md) et [transformez](../transform-model/desktop-query-overview.md) les données, et vous définissez les [paramètres](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/). 
* Dans le **modèle de données**, vous créez les [relations](../transform-model/desktop-create-and-manage-relationships.md), les [mesures](../transform-model/desktop-measures.md) et les améliorations des questions et réponses.  
* Les **[pages de rapport](../create-reports/desktop-report-view.md)** comprennent des visuels et des filtres pour fournir des insights sur vos données.  
* Les **[tableaux de bord](../consumer/end-user-dashboards.md)** et les [vignettes](../create-reports/service-dashboard-create.md) offrent une vue d’ensemble des insights inclus.
* Des exemples de données rendent votre application détectable immédiatement après l’installation.

Vous connaissez peut-être chacun de ces éléments en tant que fonctionnalités Power BI existantes. Quand vous créez une application modèle, vous devez prendre d’autres points en considération pour chaque élément. Consultez les différentes sections ci-dessous pour plus de détails.

<a name="queries"></a>

## <a name="queries"></a>Requêtes
Pour les applications modèles, les requêtes développées dans Power BI Desktop sont utilisées pour la connexion à votre source de données et l’importation des données. Ces requêtes sont nécessaires pour renvoyer un schéma cohérent et elles sont prises en charge pour l’actualisation planifiée des données.

### <a name="connect-to-your-api"></a>Vous connecter à votre API
Tout d’abord, vous devez vous connecter à votre API à partir de Power BI Desktop pour commencer à créer les requêtes.

Vous pouvez utiliser les connecteurs de données disponibles dans Power BI Desktop pour vous connecter à votre API. Vous pouvez utiliser le connecteur de données web (Obtenir des données -> Web) pour vous connecter à votre API REST ou le connecteur OData (Obtenir des données -> Flux OData) pour vous connecter à votre flux OData.

> [!NOTE]
> Les modèles d’applications ne prennent actuellement pas en charge les connecteurs personnalisés. Il est donc recommandé d’explorer à l’aide d’Odatafeed Auth 2.0 comme atténuation pour certains des cas d’utilisation de connexion ou d’envoyer votre connecteur pour certification. Si vous souhaitez savoir comment développer un connecteur de données et le certifier, consultez la [documentation sur les connecteurs de données](https://aka.ms/DataConnectors).

### <a name="consider-the-source"></a>Considérer la source
Les requêtes définissent les données incluses dans le modèle de données. Selon la taille de votre système, ces requêtes doivent également inclure des filtres pour garantir que vos clients manipulent des données de taille gérable pour votre scénario d’application professionnelle.

Les applications modèles Power BI peuvent exécuter plusieurs requêtes en parallèle, et pour plusieurs utilisateurs simultanément.  Planifiez votre stratégie de limitation et de simultanéité des requêtes, et demandez-nous comment rendre votre application modèle tolérante aux pannes.

### <a name="schema-enforcement"></a>Application du schéma
Assurez-vous que vos requêtes résistent aux modifications dans votre système, car les modifications de schéma lors de l’actualisation peuvent nuire au modèle. Si la source peut retourner un résultat de schéma de valeur null ou vide pour certaines requêtes, prévoyez de retourner une table vide ou un message d’erreur personnalisé compréhensible.

### <a name="parameters"></a>Paramètres
Les [paramètres](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) dans Power BI Desktop permettent aux utilisateurs de fournir des valeurs d’entrée qui personnalisent les données récupérées par l’utilisateur. Déterminez à l’avance les paramètres appropriés pour éviter d’avoir à apporter des modifications après avoir passé du temps à créer des requêtes ou des rapports détaillés.

> [!NOTE]
> Les applications modèles prennent en charge tous les paramètres à l’exception des paramètres Any et Binary.
>

### <a name="additional-query-tips"></a>Conseils supplémentaires pour les requêtes

* Veillez à bien saisir tous les noms de colonnes.
* Les colonnes doivent avoir des noms informatifs (consultez [Questions et réponses](#qa)).  
* Pour la logique partagée, utilisez des fonctions ou des requêtes.  
* Les niveaux de confidentialité ne sont actuellement pas pris en charge dans le service. Si vous recevez un message à propos de niveaux de confidentialité, vous devrez peut-être réécrire la requête pour utiliser des chemins relatifs.  

## <a name="data-models"></a>Modèles de données

Un modèle de données bien conçu garantit que vos clients pourront facilement et intuitivement interagir avec l’application modèle. Créez le modèle de données dans Power BI Desktop.

> [!NOTE]
> Effectuez la plus grande partie de la modélisation de base (saisie, noms de colonnes) dans les [requêtes](#queries).

### <a name="qa"></a>Questions et réponses
La modélisation détermine également la façon dont les questions et réponses fournissent des résultats pour vos clients. Pensez à ajouter des synonymes pour les colonnes fréquemment utilisées. Assurez-vous aussi d’avoir saisi les noms de colonnes corrects dans les [requêtes](#queries).

### <a name="additional-data-model-tips"></a>Conseils supplémentaires pour les modèles de données

Vérifiez les points suivants :

* Vous avez appliqué une mise en forme à toutes les colonnes de valeur. Vous avez appliqué des types dans la requête.  
* Vous avez appliqué une mise en forme à toutes les mesures.
* Vous avez défini le résumé par défaut, en particulier « Ne pas résumer » quand cela s’applique (pour les valeurs uniques, par exemple).  
* Vous avez défini la catégorie de données, le cas échéant.  
* Vous avez défini les relations appropriées.  

## <a name="reports"></a>Rapports
Les pages de rapport fournissent des insights supplémentaires sur les données incluses dans votre application modèle. Utilisez ces pages pour répondre aux questions professionnelles essentielles auxquelles votre application modèle essaye de répondre. Créez le rapport à l’aide de Power BI Desktop.


### <a name="additional-report-tips"></a>Conseils supplémentaires pour les rapports

* Utilisez plusieurs visuels par page pour le filtrage croisé.  
* Alignez les visuels soigneusement (sans chevauchement).  
* Définissez la disposition sur 4:3 ou 16:9.  
* Toutes les agrégations présentées doivent être cohérentes numériquement (moyennes, valeurs uniques).  
* Veillez à ce que le découpage produise des résultats rationnels.  
* Le logo doit être présent au moins sur la première page du rapport.  
* Les éléments doivent respecter autant que possible le schéma de couleurs du client.  

<a name="dashboard"></a>

## <a name="dashboards"></a>Tableaux de bord
Le tableau de bord est le principal point d’interaction avec votre application modèle pour vos clients. Il doit inclure une vue d’ensemble du contenu inclus, en particulier les mesures les plus importantes de votre scénario d’application professionnelle.

Pour créer un tableau de bord dans votre application modèle, chargez votre fichier PBIX via Obtenir des données > Fichiers, ou publiez directement à partir de Power BI Desktop.


### <a name="additional-dashboard-tips"></a>Conseils supplémentaires pour le tableau de bord

* Conservez le même thème pour les vignettes épinglées à votre tableau de bord pour garantir la cohérence générale.  
* Épinglez un logo au thème afin que les consommateurs sachent d’où provient le pack.  
* La disposition conseillée pour convenir à la plupart des résolutions d’écran est 5 ou 6 vignettes de petite taille.  
* Toutes les vignettes du tableau de bord doivent avoir des titres/sous-titres appropriés.  
* Essayez de regrouper les éléments verticalement ou horizontalement dans le tableau de bord pour les différents scénarios.  

## <a name="sample-data"></a>Exemple de données
Pendant l’étape de création d’applications, les modèles d’applications encapsulent les données du cache dans l’espace de travail dans le cadre de l’application :

* Ceci permet au programme d’installation de comprendre la fonctionnalité et le but de l’application avant de connecter les données.
* Ceci crée une expérience qui dirige le programme d’installation pour explorer davantage les fonctionnalités de l’application, ce qui entraîne la connexion du jeu de données de l’application.

Nous vous recommandons d’avoir des exemples de données de qualité avant de créer l’application. vérifiez que le rapport et les tableaux de bord de l’application sont remplis avec des données.

## <a name="publishing-on-appsource"></a>Publication sur AppSource
Des applications modèles peuvent être publiées sur AppSource. Suivez ces instructions avant d’envoyer votre application à AppSource :

* Vérifiez que vous créez une application modèle avec des exemples de données qui permettent au programme d’installation de comprendre ce que l’application peut faire (un rapport vide et un tableau de bord ne sont pas approuvés).
Les applications modèles prennent uniquement en charge les exemples de données, vérifiez que la case de l’application statique est cochée. [En savoir plus](./service-template-apps-create.md#define-the-properties-of-the-template-app)
* Instructions à suivre par l’équipe de validation, notamment les informations d'identification et les paramètres requis pour se connecter aux données.
* L’application doit inclure une icône d’application dans Power BI et sur votre offre CPP. [En savoir plus](./service-template-apps-create.md#define-the-properties-of-the-template-app)
* Page d’accueil configurée. [En savoir plus](./service-template-apps-create.md#define-the-properties-of-the-template-app)
* Respectez bien les instructions données dans la documentation sous [Espace partenaires -> Offre d’application Power BI](/azure/marketplace/partner-center-portal/create-power-bi-app-offer).
* Si votre application comprend un tableau de bord, assurez-vous qu’il n’est pas vide.
* Installez l’application à l’aide du lien fourni avant de l’envoyer, assurez-vous que vous pouvez connecter le jeu de données et que l’expérience de l’application est celle prévue.
* Avant de charger pbix dans l’espace de travail modèle, veillez à décharger toutes les connexions inutiles.
* Respectez les [Meilleures pratiques en matière de conception de visuels et de rapports](../visuals/power-bi-report-visualizations.md) de Power BI pour avoir un impact maximal sur vos utilisateurs et obtenir l’approbation pour la distribution.
<!--- * In general, only application with valuable functionality can be approved for general use on AppSource. Application with sample data content only must have either a guidance or statistical value.) -->

## <a name="create-a-download-link-for-the-app"></a>Créer un lien de téléchargement de l’application

Après avoir publié l’application modèle sur AppSource, créez un lien de téléchargement à partir de votre site web vers l’un des emplacements suivants :
* Page de téléchargement AppSource : consultable publiquement ; obtenez le lien à partir de votre page AppSource.
* Power BI : consultable par un utilisateur de Power BI.

Pour rediriger un utilisateur vers le lien de téléchargement de l’application dans Power BI, consultez l’exemple de code suivant : [Dépôt GitHub](https://github.com/microsoft/Template-apps-examples).

[![Lien de téléchargement de l’application](media/service-template-apps-tips/service-template-apps-tips-download.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)

## <a name="automate-parameter-configuration-during-installation"></a>Automatiser la configuration des paramètres lors de l’installation

Si vous êtes éditeur de logiciels indépendant et que vous distribuez votre application de modèle par le biais de votre service web, vous pouvez créer une automatisation qui configure automatiquement les paramètres de l’application de modèle quand vos clients installent l’application dans leur compte Power BI. Cela rend les choses plus faciles pour vos clients et augmente la probabilité d’une installation réussie, car ils n’ont pas besoin de fournir des détails qu’ils ignorent peut-être. Pour plus d’informations, consultez [Configuration automatisée d’une installation d’application modèle](../developer/template-apps/template-apps-auto-install.md).

## <a name="next-steps"></a>Étapes suivantes

[Que sont les applications modèles Power BI ?](service-template-apps-overview.md)
