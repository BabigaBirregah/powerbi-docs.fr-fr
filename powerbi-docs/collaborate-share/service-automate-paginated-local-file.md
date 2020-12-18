---
title: Enregistrer un rapport paginé dans un dossier local avec Power Automate
description: Dans cet article, vous utilisez un modèle pour configurer des exportations récurrentes d’un rapport paginé vers votre système de fichiers, au format souhaité.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098681"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>Enregistrer un rapport paginé Power BI dans un dossier local avec Power Automate

Avec [Power Automate](/power-automate/getting-started), vous pouvez automatiser l’exportation et la distribution des rapports paginés Power BI dans divers formats et scénarios pris en charge. Dans cet article, vous utilisez un modèle pour configurer des exportations récurrentes d’un rapport paginé vers votre système de fichiers, au format souhaité. S’il s’agit de la première fois que vous utilisez l’action d’exportation vers un fichier pour les rapports paginés dans Power Automate, consultez les prérequis avant de commencer.

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="Configurez des exportations récurrentes d’un rapport paginé.":::

Vous recherchez d’autres modèles Power Automate pour les rapports paginés Power BI ? Consultez [Exporter des rapports paginés Power BI avec Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Prérequis  

Pour suivre la procédure, veillez à disposer des éléments suivants :

- Au minimum un espace de travail situé dans votre locataire Power BI et disposant d’une capacité réservée. La capacité en question peut correspondre à n’importe quelle référence SKU A4/P1 – A6/P3. Découvrez-en plus sur [les capacités réservées pour les rapports paginés dans Power BI Premium](../admin/service-premium-what-is.md#paginated-reports).
- Un accès aux connecteurs standard dans Power Automate, qui sont fournis avec tous les abonnements Office 365.

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>Enregistrer un rapport paginé Power BI dans un dossier local

1. Sélectionnez le modèle **Enregistrer un rapport paginé Power BI dans un système de fichiers local**. Vérifiez que vous êtes connecté à Power BI et à votre système de fichiers local. Sélectionnez **Continuer**. 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="Enregistrez un rapport paginé Power BI dans un système de fichiers local.":::

2. Vous devrez peut-être sélectionner **Ajouter une nouvelle connexion** pour vous connecter à votre système de fichiers. 
1. Entrez un **Nom de connexion**, le chemin vers le **Dossier racine** requis et authentifiez-vous en entrant votre **Nom d’utilisateur** et votre **Mot de passe**. Sélectionnez une **passerelle** dans la liste déroulante si vous utilisez une passerelle de données locale.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="Entrez un nom de connexion et un dossier racine.":::
 
3. Pour définir la fréquence **Périodicité** de votre flux, sélectionnez une option dans la liste déroulante **Fréquence** et entrez la valeur d’**intervalle** souhaitée.  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="Définissez la fréquence de périodicité de votre flux.":::

4. Vous pouvez aussi sélectionner **Afficher les options avancées**. Configurez d’autres paramètres de **Périodicité**, comme **Fuseau horaire**, **Heure de début**, **Aux jours indiqués**, **Aux heures indiquées** et **Aux minutes indiquées**. 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="Configurez les options avancées de périodicité.":::

5. Dans la zone **Espace de travail**, sélectionnez un espace de travail situé dans une capacité réservée où se situe le rapport. Dans la zone **Rapport**, sélectionnez le rapport paginé que vous souhaitez exporter vers l’espace de travail. Dans la zone **Format d’exportation**, sélectionnez le format d’exportation souhaité. Si vous le souhaitez, vous pouvez spécifier des paramètres pour le rapport paginé. Consultez les descriptions détaillées des paramètres dans la [référence sur le connecteur pour l’API REST Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="Sélectionnez l’espace de travail et le rapport.":::

6. Dans la boîte de dialogue **Créer le fichier**, sous **Chemin du dossier**, sélectionnez le dossier vers lequel vous souhaitez exporter votre rapport paginé.
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="Sélectionnez le dossier dans lequel vous souhaitez exporter votre rapport paginé":::

7. Power Automate génère automatiquement un **nom de fichier** et un **contenu de fichier**. Vous pouvez changer le **nom du fichier**, mais vous devez conserver le **contenu de fichier** généré de manière dynamique.
8. Lorsque vous avez terminé, sélectionnez **Étape suivante** ou **Enregistrer**. Power Automate crée et évalue le flux.
9. Si Power automate détecte des erreurs, sélectionnez **Modifier le flux** pour les corriger. Sinon, sélectionnez la flèche Retour pour afficher les détails du flux et exécuter le nouveau flux.
10. Lorsque vous exécutez le flux, Power Automate exporte un rapport paginé au format spécifié vers le dossier sélectionné dans votre système de fichiers.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="Power Automate exporte un rapport paginé au format spécifié.":::

## <a name="next-steps"></a>Étapes suivantes

- [Exporter des rapports paginés Power BI avec Power Automate](service-automate-paginated-integration.md)
- [Bien démarrer avec Power Automate](/power-automate/getting-started/)
- D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

