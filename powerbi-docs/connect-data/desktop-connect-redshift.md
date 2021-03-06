---
title: Se connecter à une base de données Amazon Redshift dans Power BI Desktop
description: Se connecter facilement à une base de données Amazon Redshift et l’utiliser dans Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 60bf73e4500785c766a485fffc92a25bd8f2c852
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411353"
---
# <a name="connect-to-an-amazon-redshift-database-in-power-bi-desktop"></a>Se connecter à une base de données Amazon Redshift dans Power BI Desktop
Dans **Power BI Desktop**, vous pouvez vous connecter à une base de données **Amazon Redshift** et utiliser les données sous-jacentes comme n’importe quelle autre source de données dans Power BI Desktop.

## <a name="connect-to-an-amazon-redshift-database"></a>Se connecter à une base de données Amazon Redshift
Pour vous connecter à une base de données **Amazon Redshift**, sélectionnez **Obtenir des données** dans le ruban **Accueil** de Power BI Desktop. Sélectionnez **Base de données** dans les catégories à gauche pour afficher **Amazon Redshift**.

![Capture d’écran de la boîte de dialogue Obtenir des données, montrant la sélection de la base de données Amazon Redshift.](media/desktop-connect-redshift/connect_redshift_3.png)

Dans la fenêtre **Amazon Redshift** qui s’ouvre, tapez ou collez le nom de votre serveur et de votre base de données **Amazon Redshift** dans la zone. Dans le champ *Serveur*, les utilisateurs peuvent spécifier un port au format suivant : *URL_serveur:port*

![Capture d’écran de la boîte de dialogue Amazon Redshift, montrant les champs Serveur et Base de données.](media/desktop-connect-redshift/connect_redshift_4.png)

Lorsque vous y êtes invité, indiquez votre nom d’utilisateur et votre mot de passe. Vous devez utiliser le nom du serveur correspondant précisément au certificat SSL pour éviter les erreurs. 

![Capture d’écran de l’invite à entrer des informations d’identification Amazon RedShift, montrant les champs Nom d’utilisateur et Mot de passe.](media/desktop-connect-redshift/connect_redshift_5.png)

Une fois que vous êtes connecté, une fenêtre **Navigateur** apparaît et affiche les données disponibles sur le serveur. Vous pouvez ensuite sélectionner un ou plusieurs éléments à importer et utiliser dans **Power BI Desktop**.

![Capture d’écran de la boîte de dialogue Navigateur, montrant les données disponibles sur le serveur.](media/desktop-connect-redshift/connect_redshift_6.png)

Une fois que vous effectuez des sélections dans la fenêtre **Navigateur**, vous pouvez **charger** ou **modifier** les données.

* Si vous choisissez de **charger** les données, vous êtes invité à utiliser le mode *Importation* ou *DirectQuery*. Pour plus d’informations, consultez cet [article expliquant DirectQuery](desktop-use-directquery.md).
* Si vous choisissez de **modifier** les données, l’**Éditeur de requête** s’affiche. Vous pouvez alors appliquer toutes sortes de transformations et de filtres aux données, bon nombre d’entre-eux étant appliqués à la base de données **Amazon Redshift** sous-jacente elle-même (si cela est pris en charge).

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](../fundamentals/desktop-what-is-desktop.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
