---
title: Visuels Power BI de l’analytique incorporée Power BI pour de meilleurs insights via la BI incorporée
description: Cet article décrit les visuels Power BI personnalisés. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: overview
ms.date: 07/14/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 3d2e8f46605238a87eb23c32765f0a4ffaa02400
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888072"
---
# <a name="visuals-in-power-bi"></a>Visuels dans Power BI

Power BI est fourni avec de nombreux visuels Power BI prêts à l’emploi. Ces visuels sont disponibles dans le volet de visualisation de [Power BI Desktop](https://powerbi.microsoft.com/desktop/) et du [service Power BI](https://app.powerbi.com), et peuvent être utilisés pour la création et la modification de contenu Power BI.

:::image type="content" source="media/power-bi-custom-visuals/power-bi-visualizations.png" alt-text="Capture d’écran du volet de visualisation Power BI tel qu’il apparaît dans Power BI Desktop et le service Power BI.":::

De nombreux autres visuels Power BI sont disponibles à partir de Microsoft [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) ou par le biais de Power BI. Ces visuels sont créés par Microsoft et les partenaires Microsoft, et sont testés et validés par l’équipe de validation AppSource.

Vous pouvez également développer votre propre visuel Power BI, qui sera utilisé par vous, votre organisation ou l’intégralité de la communauté Power BI.

## <a name="default-power-bi-visuals"></a>Visuels Power BI par défaut

Il s’agit des visuels Power BI prêts à l’emploi disponibles dans le volet de visualisation de *Power BI Desktop* et du *service Power BI*.

Pour désépingler un visuel Power BI du volet de visualisation, cliquez dessus avec le bouton droit et sélectionnez **désépingler**.

Pour restaurer les visuels Power BI par défaut dans le volet de visualisation, cliquez sur **Importer un élément visuel personnalisé**, puis sélectionnez **Restaurer les visuels par défaut** . 

## <a name="appsource-power-bi-visuals"></a>Visuels Power BI AppSource

Les membres de la communauté et Microsoft mettent à disposition du public leurs visuels Power BI et les publient sur [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Vous pouvez télécharger ces visuels et les ajouter à vos rapports Power BI. Microsoft a testé et approuvé ces visuels Power BI en termes de fonctionnalité et de qualité.

>[!NOTE]
>* En utilisant des visuels Power BI créés avec notre kit SDK, vous pouvez être amené à importer ou envoyer des données depuis/vers des services tiers ou autres situés en dehors de la zone géographique, de la limite de conformité ou de l’instance de cloud national de votre locataire Power BI.
>* Les visuels certifiés Power BI sont des visuels d’AppSource qui ont fait l’objet de tests supplémentaires pour vérifier qu’ils n’accèdent pas à des services ou ressources externes.
>* Une fois importés à partir d’AppSource, les visuels Power BI peuvent être mis à jour automatiquement sans aucun autre préavis.

### <a name="what-is-appsource"></a>Présentation d’AppSource

[AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) est l’endroit où figurent des applications, des compléments et des extensions pour vos logiciels Microsoft. AppSource connecte des millions d’utilisateurs de produits comme Microsoft 365, Azure, Dynamics 365, Cortana et Power BI à des solutions qui les aident à effectuer leur travail de façon plus efficace et intelligente.

### <a name="certified-power-bi-visuals"></a>Visuels Power BI certifiés

Les visuels Power BI certifiés sont des visuels dans [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) qui sont conformes à certaines exigences de codes spécifiées, celles-ci ayant été testées et approuvées par l’équipe Microsoft Power BI. Les tests sont conçus pour vérifier que le visuel n’a pas accès à des services ni à des ressources externes.

Pour voir la liste des visuels Power BI certifiés ou pour soumettre les vôtres, consultez [Visuels Power BI certifiés](power-bi-custom-visuals-certified.md).

### <a name="samples-for-power-bi-visuals"></a>Exemples de visuels Power BI

Chaque visuel Power BI sur AppSource contient un exemple de données qui illustre son fonctionnement. Pour télécharger l’exemple, dans [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) sélectionnez un visuel Power BI et, dans la section *Essayer un exemple*, cliquez sur le lien **exemple de rapport**.

## <a name="organizational-store"></a>Magasin d’organisation

Les administrateurs Power BI approuvent et déploient des visuels Power BI dans leur organisation. Les auteurs de rapports peuvent ainsi facilement détecter, mettre à jour et utiliser ces visuels Power BI. Les administrateurs peuvent facilement gérer ces visuels avec des actions telles que la mise à jour de versions, la désactivation et l’activation de visuels Power BI.

Pour accéder au magasin d’organisation, dans le volet *Visualisation*, cliquez sur **Importer un élément visuel personnalisé**, sélectionnez **Importer à partir de la Place de marché** et, en haut de la fenêtre *Visuels Power BI*, sélectionnez l’onglet **Mon organisation**.

[En savoir plus sur les visuels organisationnels](power-bi-custom-visuals-organization.md).

## <a name="visual-files"></a>Fichiers de visuels

Les visuels Power BI sont des packages qui incluent du code pour afficher les données qu’ils reçoivent. Toute personne peut créer un visuel personnalisé et l’empaqueter dans un fichier `.pbiviz` unique, qui peut ensuite être importé dans un rapport Power BI.

Pour importer un visuel Power BI, dans le volet *Visualisation*, cliquez sur **Importer un élément visuel personnalisé**, puis sélectionnez **Importer à partir du fichier**.

Si vous êtes un développeur web et que vous souhaitez créer votre propre visuel et l’ajouter à AppSource, vous pouvez apprendre à [développer un visuel de carte ronde Power BI](develop-circle-card.md) et [publier un visuel Power BI sur AppSource](office-store.md).

> [!WARNING]
> Un visuel Power BI peut contenir du code présentant des risques en matière de sécurité ou de confidentialité. Vérifiez que vous faites confiance à son auteur et à sa source avant de l’importer dans votre rapport.

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Développement d’un visuel de carte ronde Power BI](develop-circle-card.md)

>[!div class="nextstepaction"]
>[Structure de projet des visuels Power BI](visual-project-structure.md)

>[!div class="nextstepaction"]
>[Marche à suivre pour les visuels Power BI](guidelines-powerbi-visuals.md)

>[!div class="nextstepaction"]
>[Forum aux questions](power-bi-custom-visuals-faq.md)

>[!div class="nextstepaction"]
>[Communauté Power BI](https://community.powerbi.com/)