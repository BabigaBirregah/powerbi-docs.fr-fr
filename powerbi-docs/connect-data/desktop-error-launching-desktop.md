---
title: Résoudre les problèmes de démarrage de Power BI Desktop
description: Résoudre les problèmes de démarrage de Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 11/14/2020
LocalizationGroup: Troubleshooting
ms.openlocfilehash: c41f8f9b23ef57d5dd6fd4b851918b7ffa5904a0
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226936"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Résoudre les problèmes liés à l’ouverture de Power BI Desktop

Cet article décrit et fournit une solution pour un certain nombre de cas où Power BI ne peut pas s’ouvrir. 

## <a name="resolve-issues-with-opening-encrypted-pbix-files"></a>Résoudre les problèmes liés à l’ouverture de fichiers PBIX chiffrés

Vous ne pouvez pas ouvrir les fichiers PBIX chiffrés à l’aide d’une version de Power BI Desktop qui ne prend pas en charge la protection des informations.

Si vous devez continuer à utiliser Power BI Desktop, la solution recommandée consiste à effectuer une mise à jour vers une version qui prend en charge la protection des informations. Vous pouvez télécharger la [dernière version de Power BI Desktop](https://www.microsoft.com/download/confirmation.aspx?id=58494) (ce lien est un lien de téléchargement direct vers le fichier exécutable d’installation). La dernière version de Power BI Desktop prend en charge la protection des informations et peut déchiffrer et ouvrir n’importe quel fichier PBIX chiffré.

###

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Résoudre les problèmes avec la passerelle de données locale et Power BI Desktop

Dans Power BI Desktop, les utilisateurs ayant installé et exécuté des versions précédentes de la *passerelle de données locale Power BI* peuvent se retrouver dans l’impossibilité d’ouvrir Power BI Desktop. Cela est dû aux restrictions de stratégie d’administration placées par la passerelle de données locale sur les canaux nommés de l’ordinateur local.

Vous disposez de trois options pour résoudre le problème lié à la passerelle de données locale et permettre à Power BI Desktop de s’ouvrir :

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Solution 1 : Installer la dernière version de la passerelle de données locale Power BI

La dernière version de la passerelle de données locale Power BI ne place pas de restrictions sur les canaux nommés de l’ordinateur local et permet ainsi à Power BI Desktop de s’ouvrir correctement. Si vous souhaitez continuer à utiliser la passerelle de données locale Power BI, la solution recommandée consiste à la mettre à jour. Vous pouvez télécharger la [dernière version de la passerelle de données locale Power BI](https://go.microsoft.com/fwlink/?LinkId=698863). Le lien est un lien direct vers le fichier exécutable d’installation.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Solution 2 : Désinstaller ou arrêter le service Microsoft de passerelle de données locale Power BI

Vous pouvez désinstaller la passerelle de données locale Power BI si vous n’en avez plus besoin. Ou vous pouvez arrêter le service Microsoft de passerelle de données locale Power BI, qui supprime la restriction de la stratégie et permet l’ouverture de Power BI Desktop.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Solution 3 : Exécuter Power BI Desktop avec des privilèges d’administrateur

Vous pouvez aussi démarrer Power BI Desktop en tant qu’administrateur, ce qui permet également à Power BI Desktop de s’ouvrir correctement. Il est toutefois recommandé d’installer la dernière version de la passerelle de données locale Power BI, comme décrit précédemment.

Power BI Desktop est conçu comme une architecture multitraitement et que plusieurs de ces processus communiquent à l’aide de canaux nommés de Windows. D’autres processus peuvent interférer avec ces canaux nommés. La raison la plus courante de telles interférences est la sécurité, notamment les situations où un logiciel antivirus ou des pare-feu peuvent bloquer les canaux ou rediriger le trafic vers un port spécifique. L’ouverture de Power BI Desktop avec des privilèges d’administrateur peut résoudre ce problème. Si vous ne pouvez pas ouvrir avec des privilèges d’administrateur, demandez à votre administrateur de déterminer les règles de sécurité qui empêchent les canaux nommés de communiquer correctement. Ensuite, ajoutez Power BI Desktop et ses sous-processus respectifs aux listes vertes.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Résoudre les problèmes lors de la connexion à SQL Server

Lorsque vous tentez de vous connecter à une base de données SQL Server, vous pouvez recevoir un message d’erreur semblable au texte suivant :

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

Souvent, vous pouvez résoudre le problème si vous ouvrez Power BI Desktop en tant qu’administrateur avant d’établir la connexion à SQL Server.

Après avoir ouvert Power BI Desktop en tant qu’administrateur et établi la connexion, les DLL requises sont enregistrées correctement. Après cela, l’ouverture de Power BI Desktop en tant qu’administrateur n’est pas nécessaire. Dans les cas où vous vous connectez à SQL Server avec d’autres informations d’identification Windows, vous devez ouvrir Power BI Desktop en tant qu’administrateur chaque fois que vous vous connectez.

## <a name="get-help-with-other-launch-issues"></a>Obtenir de l’aide sur d’autres problèmes de lancement

Nous nous efforçons autant que possible de résoudre les problèmes qui se produisent avec Power BI Desktop. Nous examinons régulièrement les problèmes qui peuvent affecter de nombreux clients afin de les inclure dans nos articles.

Si le problème avec l’ouverture de Power BI Desktop n’est pas associé à la passerelle de données locale, ou lorsque les solutions précédentes ne fonctionnent pas, vous pouvez soumettre un incident au *support Power BI* (<https://support.powerbi.com>) pour identifier et résoudre votre problème.

Si vous rencontrez d’autres problèmes à l’avenir avec Power BI Desktop, il est utile d’activer le suivi et de recueillir les fichiers journaux. Les fichiers journaux peuvent aider à isoler et à identifier le problème. Pour activer le suivi, choisissez **Fichier** > **Options et paramètres** > **Options**, sélectionnez **Diagnostics**, puis sélectionnez **Activer le suivi**. Power BI Desktop doit être en cours d’exécution pour activer cette option, mais cela est utile pour les problèmes futurs associés à l’ouverture de Power BI Desktop.
