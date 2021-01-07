---
title: Activer les étiquettes de sensibilité dans Power BI
description: Découvrez comment activer les étiquettes de sensibilité dans Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 12/09/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 1732c1b6b8b748c4f3a820b31c4e4fe050a66fcd
ms.sourcegitcommit: b472236df99b490db30f0168bd7284ae6e6095fb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97600320"
---
# <a name="enable-sensitivity-labels-in-power-bi"></a>Activer les étiquettes de sensibilité dans Power BI

Pour que [les étiquettes de sensibilité de Microsoft Information Protection](/microsoft-365/compliance/sensitivity-labels) puissent être utilisées dans Power BI, elles doivent être activées sur le locataire. Cet article explique aux administrateurs Power BI comment procéder. Pour une vue d’ensemble des étiquettes de sensibilité dans Power BI, consultez [Étiquettes de sensibilité dans Power BI](service-security-sensitivity-label-overview.md). Pour plus d’informations sur l’application des étiquettes de sensibilité dans Power BI, consultez [Application d’étiquettes de sensibilité](./service-security-apply-data-sensitivity-labels.md) 

Quand les étiquettes de sensibilité sont activées :

* Des utilisateurs et des groupes de sécurité spécifiés de l’organisation peuvent classer leur contenu Power BI et y [appliquer des étiquettes de confidentialité](./service-security-apply-data-sensitivity-labels.md). Dans le service Power BI, cela correspond à leurs rapports, tableaux de bord, jeux de données et flux de données. Dans Power BI Desktop, il s’agit de leurs fichiers .pbix.
* Dans le service, tous les membres de l’organisation pourront voir ces étiquettes. Dans Desktop, seuls pourront les voir ceux pour lesquels elles sont publiées.

L’activation des étiquettes de sensibilité nécessite une licence Azure Information Protection. Pour plus d’informations, consultez [Licences et configuration requise](#licensing-and-requirements).

>[!NOTE]
>Pendant 48 heures après avoir choisi la fonctionnalité en préversion Information Protection, **les utilisateurs sont susceptibles de rencontrer des problèmes avec les fichiers .pbix sur lesquels des étiquettes de confidentialité ont été appliquées (par exemple pour publier ces fichiers dans le service ou les télécharger à partir du service)** . Ce type de problème est attendu et sera résolu automatiquement dans un délai de 48 heures.

## <a name="licensing-and-requirements"></a>Licences et configuration requise

* Une licence Azure Information Protection Premium P1 ou Premium P2 est requise pour appliquer ou afficher des étiquettes de confidentialité Microsoft Information Protection dans Power BI. Vous pouvez acheter Azure Information Protection en autonome ou par le biais de l’une des suites de licences Microsoft. Pour plus d’informations, consultez les [tarifs Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/).

    >[!NOTE]
    > Si votre organisation utilise des étiquettes de sensibilité Azure Information Protection, vous devez les migrer vers la plateforme d’étiquetage unifiée de Microsoft Information Protection afin qu’elles soient utilisées dans Power BI. [En savoir plus sur la migration des étiquettes de sensibilité](/azure/information-protection/configure-policy-migrate-labels).

* Pour pouvoir appliquer des étiquettes à du contenu et à des fichiers Power BI, un utilisateur doit disposer d’une licence Power BI Pro en plus d’une des licences Azure Information Protection mentionnées ci-dessus.

* Les applications Office disposent de leurs propres [conditions de licence requises pour afficher et appliquer des étiquettes de sensibilité]( https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels ).

* Avant d’activer des étiquettes de confidentialité sur votre abonné, assurez-vous qu’elles sont bien définies et publiées pour les utilisateurs et les groupes appropriés. Consultez [Créer et configurer des étiquettes de sensibilité et leurs stratégies](/microsoft-365/compliance/create-sensitivity-labels) pour plus d’informations.

* La version de décembre 2020 (ou une version ultérieure) de Desktop est nécessaire pour utiliser les étiquettes de confidentialité dans Desktop.

    >[!NOTE]
    > Si vous essayez d’ouvrir un fichier .pbix protégé avec une version de Desktop antérieure à celle de décembre 2020, le processus échouera, et il vous sera demandé de mettre à niveau votre version de Desktop.

## <a name="enable-sensitivity-labels"></a>Activer les étiquettes de sensibilité

Les étiquettes de confidentialité doivent être activées sur le locataire pour pouvoir être utilisées à la fois dans le service et dans Desktop. Cette section explique comment les activer dans les paramètres du locataire. Pour plus d’informations sur Desktop, consultez [Désactivation des étiquettes de confidentialité dans Desktop dans toute l’organisation](#disable-sensitivity-labels-in-desktop-across-your-org) ci-dessous. 

Pour activer les étiquettes de confidentialité sur le locataire, accédez au **Portail d’administration** Power BI, ouvrez le volet **Paramètres du locataire** et recherchez la section **Information Protection**.

![Rechercher la section Information Protection](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Dans la section **Information Protection**, effectuez les étapes suivantes :
1. Ouvrez **Autoriser les utilisateurs à appliquer des étiquettes de confidentialité pour le contenu Power BI**.
1. Activez le bouton bascule.
1. Définissez qui peut appliquer et changer les étiquettes de sensibilité dans les ressources Power BI. Par défaut, toutes les personnes de votre organisation peuvent appliquer des étiquettes de sensibilité. Toutefois, vous pouvez choisir d’activer le paramétrage des étiquettes de sensibilité uniquement pour des utilisateurs ou des groupes de sécurité spécifiques. Si vous avez sélectionné l’ensemble de l’organisation ou des groupes de sécurité particuliers, vous pouvez exclure des sous-ensembles spécifiques d’utilisateurs ou de groupes de sécurité.
   
   * Quand les étiquettes de sensibilité sont activées pour l’ensemble de l’organisation, les exceptions sont généralement des groupes de sécurité.
   * Quand les étiquettes de sensibilité sont activées uniquement pour des utilisateurs ou des groupes de sécurité spécifiques, les exceptions sont généralement des utilisateurs spécifiques.  
    Cette approche permet d’empêcher certains utilisateurs d’appliquer des étiquettes de sensibilité dans Power BI, même s’ils appartiennent à un groupe disposant des autorisations nécessaires.

1. Appuyez sur **Appliquer**.

![Activer les étiquettes de sensibilité](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Seuls les utilisateurs Power BI Pro qui disposent d’autorisations *créer* et *modifier* sur la ressource et qui font partie du groupe de sécurité approprié défini dans cette section peuvent définir et modifier les étiquettes de sensibilité. Les utilisateurs qui ne font pas partie de ce groupe ne peuvent pas définir ou modifier l’étiquette.  

## <a name="disable-sensitivity-labels-in-desktop-across-your-org"></a>Désactivation des étiquettes de confidentialité dans Desktop dans toute l’organisation

Dans les organisations qui souhaitent que les fichiers .pbix ne fonctionnent **pas** avec des étiquettes de confidentialité, l’administrateur Power BI peut créer une stratégie de groupe selon laquelle Power BI empêche les utilisateurs de classer les fichiers .pbix, de les protéger et d’ouvrir les fichiers auxquels une protection a déjà été appliquée. Pour créer une stratégie de ce type, procédez comme suit :

1. Ouvrez l’[Éditeur du Registre](https://support.microsoft.com/windows/how-to-open-registry-editor-in-windows-10-deab38e6-91d6-e0aa-4b7c-8878d9e07b11).

1. Recherchez la clé **HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop**.

1. Recherchez le nom de valeur **EnableInformationProtection** et donnez-lui la valeur **false**.

Pour plus d’informations sur les étiquettes de confidentialité dans Power BI Desktop et leurs limitations, consultez la page [Vue d’ensemble des étiquettes de confidentialité](./service-security-sensitivity-label-overview.md#limitations).

## <a name="troubleshooting"></a>Résolution des problèmes

Power BI utilise les étiquettes de sensibilité Microsoft Information Protection. Par conséquent, si un message d’erreur s’affiche lors d’une tentative d’activation des étiquettes de sensibilité, cela peut être dû à l’une des raisons suivantes :

* Vous ne disposez pas de [licence](#licensing-and-requirements) Azure Information Protection.
* Les étiquettes de sensibilité n’ont pas été [migrées](#enable-sensitivity-labels) vers la version de Microsoft Information Protection prise en charge par Power BI.
* Aucune étiquette de sensibilité Microsoft Information Protection n’a été [définie dans votre organisation](#enable-sensitivity-labels).

## <a name="considerations-and-limitations"></a>Considérations et limitations

Consultez [Étiquettes de sensibilité dans Power BI](service-security-sensitivity-label-overview.md#limitations) pour obtenir la liste des limitations relatives aux étiquettes de sensibilité dans Power BI.

## <a name="next-steps"></a>Étapes suivantes

L’objectif de cet article était d’expliquer comment activer les étiquettes de sensibilité dans Power BI. Les articles suivants fournissent plus de détails sur la protection des données dans Power BI. 

* [Vue d’ensemble des étiquettes de sensibilité dans Power BI](service-security-sensitivity-label-overview.md)
* [Guide pratique pour appliquer des étiquettes de sensibilité dans Power BI](./service-security-apply-data-sensitivity-labels.md)
* [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport des métriques de protection](service-security-data-protection-metrics-report.md)