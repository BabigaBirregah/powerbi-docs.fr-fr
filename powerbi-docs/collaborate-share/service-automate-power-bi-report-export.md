---
title: Exporter un rapport et l’envoyer par e-mail avec Power Automate
description: Dans cet article, vous utilisez Power Automate pour automatiser l’exportation et la distribution des rapports Power BI dans divers formats et scénarios pris en charge.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098695"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>Exporter un rapport Power BI et l’envoyer par e-mail Power Automate

Avec [Power Automate](/power-automate/getting-started), vous pouvez automatiser l’exportation et la distribution des rapports Power BI dans divers formats et scénarios. Dans cet article, vous créez votre propre flux à partir de zéro. Vous utilisez l’action Exporter vers un fichier pour les rapports Power BI pour distribuer automatiquement un rapport Power BI par e-mail.

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="Étapes d’exportation et d’envoi d’un rapport par e-mail dans Power Automate.":::

## <a name="prerequisites"></a>Prérequis  

Pour suivre la procédure, veillez à disposer des éléments suivants :

- Au minimum un espace de travail situé dans votre locataire Power BI et disposant d’une capacité réservée. La capacité en question peut correspondre à n’importe quelle référence SKU A1/EM1 – A6/P3. En savoir plus sur les [capacités réservées dans Power BI Premium](../admin/service-premium-what-is.md).
- Un accès aux connecteurs standard dans Power Automate, qui sont fournis avec tous les abonnements Office 365.

## <a name="create-a-flow-from-scratch"></a>Créer entièrement un flux 

Dans cette tâche, vous créez un flux simple à partir de zéro. Le flux exporte un rapport Power BI sous forme de fichier PDF et le joint à un e-mail qui doit être envoyé chaque semaine.  

1. Connectez-vous à Power Automate (flow.microsoft.com).
2. Sélectionnez **Créer** > **Flux planifié**. 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="Créez un flux planifié dans Power Automate.":::

3. Dans **Générer un flux planifié**, attribuez un nom au flux. 
4. Dans **Exécuter ce flux**, sélectionnez la date et l’heure de début de votre flux, ainsi que la fréquence de répétition.
5. Dans **Aux jours indiqués**, sélectionnez les jours auxquels vous souhaitez que le flux s’exécute, puis sélectionnez **Créer**.

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power Automate, planifier le flux.":::

6. Dans **Périodicité**, sélectionnez **Afficher les options avancées** et entrez une valeur pour **Aux heures indiquées** et **Aux minutes indiquées** afin de définir une heure spécifique pour l’exécution de votre flux.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="Définissez la périodicité dans Power Automate.":::

7. Sélectionnez **Nouvelle étape**.
8. Dans **Choisir une action**, recherchez **Power BI** et sélectionnez **Exporter vers un fichier pour les rapports Power BI**.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="Choisissez une action dans Power Automate.":::

9. Dans **Exporter vers un fichier pour les rapports Power BI**, sélectionnez un **Espace de travail** et un **Rapport** dans les listes déroulantes.
10. Sélectionnez le **Format d’exportation** souhaité pour votre rapport Power BI.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="Sélectionnez le format d’exportation dans Power Automate.":::

11. Si vous le souhaitez, indiquez des pages spécifiques à exporter dans le champ **Pages pageName -1**. Notez que le paramètre du nom de page est différent du nom de la page d’affichage. Recherchez le nom de la page en accédant à la page dans le service Power BI et en copiant la dernière partie de l’URL.
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="Sélectionnez le nom du volet dans l’URL.":::

12. Si vous le souhaitez, indiquez un signet spécifique à afficher dans le champ **Pages Nom du signet**. Comme pour le paramètre du nom de page, vous trouvez le paramètre du nom de signet dans l’URL du rapport. Vous pouvez spécifier des paramètres supplémentaires pour le rapport Power BI. Pour obtenir les descriptions détaillées de ces paramètres, consultez la [référence sur le connecteur pour l’API REST Power BI](/connectors/powerbi/#export-to-file-for-power-bi-reports).

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="Sélectionnez le nom du signet dans l’URL.":::

13. Sélectionnez **Nouvelle étape**.
14. Dans **Choisir une action**, recherchez **Outlook** et sélectionnez **Envoyer un e-mail (v2)** .
15. Dans **Envoyer un e-mail (v2)** , remplissez les champs **À**, **Objet** et **Corps** de votre e-mail.
16. Sélectionnez **Afficher les options avancées**. Dans **Nom des pièces jointes – 1**, entrez un nom pour votre pièce jointe. Ajoutez une extension de fichier au nom de fichier (par exemple, .PDF) qui correspond au **format d’exportation** de votre choix.
17. Dans **Contenu de la pièce jointe**, sélectionnez **Contenu du fichier** pour joindre votre rapport Power BI exporté.  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="Sélectionnez votre rapport exporté à envoyer par e-mail.":::

18. Lorsque vous avez terminé, sélectionnez **Étape suivante** ou **Enregistrer**. Power Automate crée et évalue le flux, et vous informe s’il trouve des erreurs.
1. En cas d’erreurs, sélectionnez  **Modifier le flux** pour les corriger. Sinon, sélectionnez la flèche **Retour** pour afficher les détails du flux et exécuter le nouveau flux.
    Lorsque vous exécutez le flux, Power Automate exporte un rapport Power BI au format spécifié et l’envoie en tant que pièce jointe dans un e-mail comme cela a été planifié.  

## <a name="next-steps"></a>Étapes suivantes

- [Intégrer des alertes de données Power BI à Power Automate](service-flow-integration.md)
- [Bien démarrer avec Power Automate](/power-automate/getting-started/)
- D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
