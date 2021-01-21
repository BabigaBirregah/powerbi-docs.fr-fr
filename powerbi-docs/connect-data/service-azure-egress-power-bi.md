---
title: Sortie Azure et Power BI
description: Comprendre les frais de sortie Azure et Power BI en fonction de l’emplacement du locataire et de Power BI Premium
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Data from databases
ms.openlocfilehash: ec47968294e0fd905d1733bdb30ae1840069aed7
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597467"
---
# <a name="power-bi-and-azure-egress"></a>Sortie Azure et Power BI

Le déplacement de données (sortie) hors des centres de données Azure peut entraîner des frais de bande passante. Quand vous utilisez Power BI avec des sources de données Azure, vous pouvez éviter des frais de sortie Azure en vous assurant que votre locataire Power BI se trouve dans la même région que vos sources de données Azure.

Quand votre locataire Power BI est déployé sur la même région Azure que celle sur laquelle vous déployez vos sources de données, vous n’encourez pas de frais de sortie pour l’actualisation planifiée et les interactions DirectQuery. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Détermination de l’emplacement de votre locataire Power BI

Pour savoir où se trouve votre locataire Power BI, consultez l’article [Où est situé mon client Power BI ?](../admin/service-admin-where-is-my-tenant-located.md).

Pour les clients Multi-Géo Power BI Premium, si votre locataire Power BI ne se trouve pas à l’emplacement optimal pour certaines de vos sources de données basées sur Azure, vous pouvez déployer la fonctionnalité Multi-Géo Power BI Premium dans la région Azure souhaitée et réunir ainsi votre locataire Power BI et les sources de données Azure dans la même région Azure.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur Power BI Premium ou la fonctionnalité Multi-Géo, consultez les ressources suivantes :

* [Détails de la tarification de la bande passante Azure](https://azure.microsoft.com/pricing/details/bandwidth/)
* [Présentation de Microsoft Power BI Premium](../admin/service-premium-what-is.md)
* [Acheter Power BI Premium](../admin/service-admin-premium-purchase.md)
* [Prise en charge de zones géographiques multiples dans Power BI Premium (préversion)](../admin/service-admin-premium-multi-geo.md)
* [Où est situé mon locataire Power BI ?](../admin/service-admin-where-is-my-tenant-located.md)
* [FAQ Power BI Premium](../admin/service-premium-faq.md)
