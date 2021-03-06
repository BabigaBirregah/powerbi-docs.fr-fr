---
title: Se connecter aux données d’Azure Cost Management dans Power BI Desktop
description: Se connecter facilement à Azure pour obtenir des insights sur le coût et l’utilisation d’Azure avec Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 6d99e91657d0c5f0bbd1e9c665f00d16c34ba24f
ms.sourcegitcommit: 772c65b7b440ab082510bf3f64b871d19139d451
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97353240"
---
# <a name="create-visuals-and-reports-with-the-azure-cost-management-connector-in-power-bi-desktop"></a>Créer des visuels et des rapports avec le connecteur Azure Cost Management dans Power BI Desktop

Vous pouvez utiliser le connecteur Azure Cost Management pour Power BI Desktop pour créer des visualisations et des rapports puissants et personnalisés qui vous aideront à mieux comprendre vos dépenses Azure. Le connecteur Azure Cost Management prend actuellement en charge les clients disposant d’un [Contrat client Microsoft](https://azure.microsoft.com/pricing/purchase-options/microsoft-customer-agreement/) ou d’un [Contrat Entreprise](https://azure.microsoft.com/pricing/enterprise-agreement/).  

Le connecteur Azure Cost Management utilise la norme OAuth 2.0 pour l’authentification auprès d’Azure et identifie les utilisateurs qui vont utiliser le connecteur. Les jetons générés dans ce processus sont valides pour une période spécifique. Power BI conserve le jeton pour la connexion suivante. OAuth 2.0 est une norme encadrant le processus d’arrière-plan qui garantit la gestion sécurisée de ces autorisations. Pour vous connecter, vous devez utiliser un compte [Administrateur Entreprise](/azure/billing/billing-understand-ea-roles) pour les Contrats Entreprise ou un [Propriétaire de compte de facturation](/azure/billing/billing-understand-mca-roles) pour les Contrats clients Microsoft. 

> [!NOTE]
> Ce connecteur remplace les connecteurs précédemment disponibles [Azure Consumption Insights et Azure Cost Management (bêta)](desktop-connect-azure-consumption-insights.md). Tous les rapports créés avec le connecteur précédent doivent être recréés à l’aide de ce connecteur.

> [!NOTE]
> Le connecteur Azure Cost Management pour Power BI Desktop ne prend pas en charge la connexion aux clouds du secteur public. 


## <a name="connect-using-azure-cost-management"></a>Se connecter avec Azure Cost Management

Pour utiliser le **connecteur Azure Cost Management** dans Power BI Desktop, procédez comme suit :

1.  Dans le ruban **Accueil**, sélectionnez **Obtenir des données**.
2.  Sélectionnez **Azure** dans la liste des catégories de données.
3.  Sélectionnez **Azure Cost Management**.

    ![Obtenir des données](media/desktop-connect-azure-cost-management/azure-cost-management-00b.png)

4. Dans la boîte de dialogue qui s’affiche, entrez votre **ID de profil de facturation** pour les **Contrats clients Microsoft**, ou votre **Numéro d’inscription** pour les **Contrats Entreprise**. 


## <a name="connect-to-a-microsoft-customer-agreement-account"></a>Se connecter à un compte de contrat client Microsoft 

Pour vous connecter avec un compte de **Contrat client Microsoft**, vous pouvez obtenir votre **ID de profil de facturation** à partir du portail Azure :

1.  Dans le [portail Azure](https://portal.azure.com/), accédez à **Gestion des coûts + facturation**.
2.  Sélectionnez votre profil de facturation. 
3.  Sous **Paramètres** dans le menu, sélectionnez **Propriétés** dans la barre latérale.
4.  Sous **Profil de facturation**, copiez **l’ID**. 
5.  Pour **Choisir l’étendue**, sélectionnez **ID du profil de facturation** et collez l’ID du profil de facturation de l’étape précédente. 
6.  Entrez le nombre de mois et sélectionnez **OK**.

    ![Capture d’écran montrant les propriétés Azure Cost Management avec l’étendue ID du profil de facturation.](media/desktop-connect-azure-cost-management/azure-cost-management-01a.png)

7.  Lorsque vous y êtes invité, connectez-vous avec votre compte d’utilisateur et votre mot de passe Azure. Vous devez utiliser un propriétaire de compte de facturation pour un accès réussi. 


## <a name="connect-to-an-enterprise-agreement-account"></a>Se connecter à un compte Contrat Entreprise

Pour vous connecter avec un compte Contrat Entreprise, vous pouvez récupérer votre ID d’inscription à partir du portail Azure :

1.  Dans le [portail Azure](https://portal.azure.com/), accédez à **Gestion des coûts + facturation**.
2.  Sélectionnez votre compte de facturation.
3.  Dans le menu **Vue d’ensemble**, copiez **l’ID de compte de facturation**.
4.  Pour **Choisir l’étendue**, sélectionnez **Numéro d’inscription** et collez l’ID du compte de facturation de l’étape précédente. 
5.  Entrez le nombre de mois, puis sélectionnez **OK**.

    ![Capture d’écran montrant les propriétés Azure Cost Management avec l’étendue Numéro d’inscription.](media/desktop-connect-azure-cost-management/azure-cost-management-01b.png)

6.  Lorsque vous y êtes invité, connectez-vous avec votre compte d’utilisateur et votre mot de passe Azure. Vous devez utiliser un compte Administrateur Entreprise pour les Contrats Entreprise.

## <a name="data-available-through-the-connector"></a>Données disponibles par le biais du connecteur

Une fois que vous vous êtes correctement authentifié, une fenêtre de **Navigateur** s’affiche avec les tables de données disponibles suivantes :

| **Table** | **Description** |
| --- | --- |
| **Balance summary (Récapitulatif du solde)** | Résumé du solde pour les Contrats Entreprise. |
| **Événements de facturation** | Journal des événements liés aux nouvelles factures, achats de crédits, etc. Contrats clients Microsoft uniquement. |
| **Budgets** | Informations budgétaires permettant de comparer les coûts et l’utilisation réels aux objectifs budgétaires. |
| **Charges** | Un récapitulatif mensuel de l’utilisation d’Azure, des coûts de la Place de marché et des coûts facturés séparément. Contrats clients Microsoft uniquement. |
| **Lots de crédits** | Informations sur les achats de lots de crédits Azure pour le profil de facturation spécifié. Contrats clients Microsoft uniquement. |
| **Pricesheets (Listes de prix)** | Tarifs applicables pour le profil de facturation ou l’inscription Contrat Entreprise spécifié. |
| **RI charges (Coûts facturés pour les instances réservées)** | Coûts associés à vos instances réservées au cours des 24 derniers mois. |
| **RI recommendations (shared) - Recommandations (partagées) pour les instances réservées** | Recommandations d’achat d’instances réservées en fonction des tendances de votre utilisation sur tous vos abonnements au cours des 7, 30 ou 60 derniers jours. |
| **RI recommendations (single) - Recommandations (abonnement unique) pour les instances réservées** | Recommandations d’achat d’instances réservées en fonction des tendances de votre utilisation sur un seul abonnement au cours des 7, 30 ou 60 derniers jours. |
| **RI usage details (Détails d’utilisation des instances réservées)** | Informations sur la consommation de vos instances réservées existantes au cours du mois dernier. |
| **RI usage summary (Récapitulatif de l’utilisation des instances réservées)** | Pourcentage d’utilisation quotidienne des réservations Azure |
| **Usage Details (Détails d’utilisation)** | Une répartition des quantités consommées et des coûts estimés pour le profil de facturation indiqué sur l’inscription de Contrat Entreprise. |
| **Usage details amortized (Détails d’utilisation avec amortissement)** | Une répartition des quantités consommées et des coûts amortis estimés pour le profil de facturation indiqué sur l’inscription de Contrat Entreprise. |

Vous pouvez sélectionner une table pour afficher une boîte de dialogue d’aperçu. Vous pouvez sélectionner une ou plusieurs tables en sélectionnant la case en regard de leur nom, puis en sélectionnant **Charger**.

![Capture d’écran montrant la boîte de dialogue Navigateur.](media/desktop-connect-azure-cost-management/azure-cost-management-01c.png)

Quand vous sélectionnez **Charger**, les données sont chargées dans Power BI Desktop. 

Une fois les données sélectionnées chargées, les tables de données et les champs s’affichent dans le volet **Champs**.


## <a name="next-steps"></a>Étapes suivantes

Vous pouvez vous connecter à de nombreuses sources de données différentes à l’aide de Power BI Desktop. Pour plus d’informations, consultez les articles suivants :

* [Qu’est-ce que Power BI Desktop ?](../fundamentals/desktop-what-is-desktop.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)