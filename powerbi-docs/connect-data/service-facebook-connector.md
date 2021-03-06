---
title: 'Service tiers : Connecteur Facebook pour Power BI Desktop'
description: 'Service tiers : Connecteur Facebook pour Power BI Desktop'
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 02/20/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 4f1faf585643c593e194e965dff2bb29988e27d4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402567"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Utiliser le connecteur Facebook pour Power BI Desktop
Le connecteur Facebook de **Power BI Desktop** s’appuie sur l’API Graph de Facebook. Ses fonctionnalités et sa disponibilité peuvent donc varier au fil du temps.

Vous pouvez consulter un [didacticiel sur le connecteur Facebook pour Power BI Desktop](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Dépréciation du connecteur de données Facebook** : L’importation et l’actualisation de données Facebook dans Excel ne fonctionneront plus correctement à partir du mois d’avril 2020. D’ici là, vous pouvez continuer à utiliser le connecteur Facebook *Récupérer et transformer (Power Query)* . Après cette date, vous ne pourrez plus vous connecter à Facebook et vous recevrez un message d’erreur. Nous vous recommandons de revoir ou supprimer dès que possible vos requêtes *Récupérer et transformer (Power Query)* existantes qui utilisent le connecteur Facebook afin d'éviter des résultats inattendus.


La version v1.0 de l’API Graph de Facebook a expiré le 30 avril 2015. Power BI utilise l’API Graph en arrière-plan pour le connecteur Facebook, ce qui vous permet de vous connecter à vos données et de les analyser.

Les requêtes créées avant le 30 avril 2015 ne fonctionnent peut-être plus ou retournent moins de données. Depuis le 30 avril 2015, Power BI utilise la version 2.8 dans tous les appels à l’API Facebook. Si votre requête a été créée avant le 30 avril 2015 et que vous ne l’avez pas utilisée depuis, vous devrez probablement vous authentifier à nouveau afin d’approuver le nouveau jeu d’autorisations que nous vous demanderons.

Nous nous efforçons de publier des mises à jour en fonction des modifications. Toutefois, il se peut que l’API soit modifiée d’une manière qui affecte les résultats des requêtes que nous générons. Dans certains cas, certaines requêtes peuvent ne plus être prises en charge. En raison de cette dépendance, nous ne pouvons pas garantir les résultats de vos requêtes lors de l’utilisation de ce connecteur.

Pour plus d’informations sur la modification de l’API de Facebook, accédez [ici](https://developers.facebook.com/docs/apps/changelog#v2_0).

