---
title: Exportation de l’API de rapports d’analytique incorporée Power BI pour de meilleurs insights décisionnels incorporés
description: Découvrez comment exporter un rapport Power BI incorporé pour améliorer votre expérience d’analytique incorporée Power BI Embedded. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 12/28/2020
ms.openlocfilehash: acd9d98b55697e8ca3729cad65a1ead8f01f6e62
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887014"
---
# <a name="export-power-bi-report-to-file-preview"></a>Exporter un rapport Power BI vers un fichier (préversion)

L’API `exportToFile` permet d’exporter un rapport Power BI avec un appel REST. Les formats de fichier suivants sont pris en charge :
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * Lors de l’exportation vers un fichier .png, un rapport de plusieurs pages est comprimé dans un fichier .zip.
    * Chaque fichier contenu dans le fichier .zip représente une page du rapport
    * Les noms des pages sont les mêmes que les valeurs de retour des API [Obtenir des pages](/rest/api/power-bi/reports/getpages) ou [Obtenir des pages dans le groupe](/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Exemples d'utilisation

Vous pouvez utiliser la fonctionnalité d’exportation de différentes manières. Voici quelques exemples :

* **Bouton Envoyer à l’impression** : dans votre application, créez un bouton qui, lorsque vous cliquez dessus, déclenche un travail d’exportation. Le travail peut exporter le rapport visualisé dans un fichier .pdf ou .pptx et, une fois qu’il est terminé, l’utilisateur peut recevoir le fichier sous forme de téléchargement. À l’aide de signets, vous pouvez exporter le rapport dans un état spécifique, y compris des filtres configurés, des segments et des paramètres supplémentaires. Étant donné que l’API est asynchrone, la mise à disposition du fichier peut prendre un certain temps.

* **Pièce jointe d’e-mail** : envoyer un e-mail automatisé à intervalles définis, avec un rapport .pdf en pièce jointe. Ce scénario peut être utile si vous souhaitez automatiser l’envoi d’un rapport hebdomadaire aux dirigeants. Pour plus d’informations, consultez [Exportation et envoi par e-mail d’un rapport Power BI avec Power Automate](../../collaborate-share/service-automate-power-bi-report-export.md)

## <a name="using-the-api"></a>Utilisation de l’API

Avant d’utiliser l’API, vérifiez que les [paramètres de locataire administrateurs](../../admin/service-admin-portal.md#tenant-settings) suivants sont activés :
* **Exporter les rapports comme présentations PowerPoint ou documents PDF** : activé par défaut.
* **Exporter des rapports en tant que fichiers image** : nécessaire uniquement pour les fichiers *.png*, et désactivé par défaut.

L’API est asynchrone. Lorsque l’API [exportToFile](/rest/api/power-bi/reports/exporttofile) est appelée, elle déclenche un travail d’exportation. Après avoir déclenché un travail d’exportation, utilisez l’[interrogation](/rest/api/power-bi/reports/getexporttofilestatus) pour suivre le travail jusqu’à ce qu’il soit terminé.

Pendant l’interrogation, l’API retourne un nombre qui représente la quantité de travail effectué. Le travail dans chaque travail d’exportation est calculé en fonction du nombre de pages du rapport. Toutes les pages ont le même poids. Si, par exemple, vous exportez un rapport de 10 pages et que l’interrogation retourne 70, cela signifie que l’API a traité sept des 10 pages du travail d’exportation.

Une fois l’exportation terminée, l’appel de l’API d’interrogation retourne une [URL Power BI](/rest/api/power-bi/reports/getfileofexporttofile) pour obtenir le fichier. L’URL sera disponible pendant 24 heures.

## <a name="supported-features"></a>Fonctionnalités prises en charge

### <a name="selecting-which-pages-to-print"></a>Sélection des pages à imprimer

Spécifiez les pages à imprimer en fonction de la valeur de retour [Obtenir des pages](/rest/api/power-bi/reports/getpages) ou [Obtenir des pages dans le groupe](/rest/api/power-bi/reports/getpagesingroup). Vous pouvez également spécifier l’ordre des pages que vous exportez.

### <a name="bookmarks"></a>Signets

Des [signets](../../consumer/end-user-bookmarks.md) peuvent être utilisés pour enregistrer un rapport dans une configuration spécifique, y compris avec des filtres appliqués et l’état des visuels du rapport. Vous pouvez utiliser l’API [exportToFile](/rest/api/power-bi/reports/exporttofile) pour exporter par programme le signet d’un rapport, de deux manières :

* **Exporter un signet existant**

    Pour exporter un [signet de rapport](../../consumer/end-user-bookmarks.md#report-bookmarks) existant, utilisez la propriété `name`, un identificateur unique (sensible à la casse) que vous pouvez obtenir à l’aide de [l’API de signets JavaScript](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

* **Exporter l’état du rapport**

    Pour exporter l’état actuel du rapport, utilisez la propriété `state`. Par exemple, vous pouvez utiliser la méthode de signet `bookmarksManager.capture` pour capturer les modifications apportées par un utilisateur spécifique à un rapport, puis l’exporter dans son état actuel avec `capturedBookmark.state`.

>[!NOTE]
>[Les signets personnels](../../consumer/end-user-bookmarks.md#personal-bookmarks) et [les filtres persistants](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) ne sont pas pris en charge.

### <a name="filters"></a>Filtres

Dans [PowerBIReportExportConfiguration](/rest/api/power-bi/reports/exporttofile#powerbireportexportconfiguration), `reportLevelFilters` permet d’exporter un rapport filtré.

Pour exporter un rapport filtré, insérez dans [ExportFilter](/rest/api/power-bi/reports/exporttofile#exportfilter) les [paramètres de chaîne de requête d’URL](../../collaborate-share/service-url-filters.md) que vous souhaitez utiliser comme filtre. Lorsque vous entrez la chaîne, vous devez supprimer la partie `?filter=` du paramètre de requête d’URL.

Le tableau ci-dessous contient quelques exemples de syntaxe de chaînes que vous pouvez passer à `ExportFilter`.

|Filtrer    |Syntaxe    | Exemple    |
|---|----|----|----|
|Valeur dans un champ    |Table/Champ eq ’valeur’    |Store/Territory eq ’NC’    |
|Plusieurs valeurs dans un champ    |Table/Champ in (’valeur1’, ’valeur2’)     |Store/Territory in (’NC’, ’TN’)    |
|Valeur distincte dans un champ, autre valeur distincte dans un autre champ    |Table/Champ1 eq ’valeur1’ and Table/Champ2 eq ’valeur2’    |Store/Territory eq ’NC’ and Store/Chain eq ’Fashions Direct’    |

>[!NOTE]
>`ReportLevelFilters` ne peut contenir qu’un seul [ExportFilter](/rest/api/power-bi/reports/exporttofile#exportfilter).

### <a name="authentication"></a>Authentification

Vous pouvez vous authentifier avec un utilisateur (ou un utilisateur maître) ou un [principal de service](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Sécurité au niveau de la ligne (RLS)

La [Sécurité au niveau de la ligne (RLS)](embedded-row-level-security.md) permet d’exporter un rapport mentionnant des données qui ne sont accessibles qu’à certains utilisateurs. Par exemple, si vous exportez un rapport de ventes défini avec des rôles régionaux, vous pouvez filtrer programmatiquement le rapport de façon à n’afficher qu’une région précise.

Pour exporter avec RLS, vous devez disposer des autorisations suivantes :
* Écrire et partager à nouveau des autorisations pour le jeu de données auquel le rapport est connecté
* Si le rapport se trouve dans un espace de travail v1, vous devez être l’administrateur de l’espace de travail.
* Si le rapport se trouve dans un espace de travail v2, vous devez être membre de l’espace de travail ou administrateur.

### <a name="data-protection"></a>Protection des données

Les formats .pdf et .pptx prennent en charge les [étiquettes de sensibilité](../../admin/service-security-sensitivity-label-overview.md). Si vous exportez un rapport doté d’une étiquette de sensibilité au format .pdf ou .pptx, le fichier exporté affiche le rapport avec son étiquette de sensibilité.

Un rapport avec une étiquette de sensibilité ne peut pas être exporté au format .pdf ou .pptx à l’aide d’un [principal de service](embed-service-principal.md).

### <a name="localization"></a>Localisation

Lorsque vous utilisez l’API `exportToFile`, vous pouvez transmettre la valeur locale souhaitée. Les paramètres de localisation affectent la façon dont le rapport est affiché, par exemple en modifiant la mise en forme en fonction de la valeur locale sélectionnée.

## <a name="concurrent-requests"></a>Demandes simultanées

`exportToFile` prend en charge les demandes de travaux d’exportation simultanées. Le tableau ci-dessous indique le nombre de travaux que vous pouvez exécuter en même temps, en fonction de la référence SKU sur laquelle votre rapport réside. Les demandes simultanées font référence aux pages du rapport. Par exemple, 20 pages dans une demande d’exportation sur une référence SKU A6 seront traitées simultanément. Ceci prendra à peu près le même temps que l’envoi de 20 demandes d’exportation d’une page chacune.

Un travail dépassant le nombre de demandes simultanées ne se termine pas. Par exemple, si vous exportez trois pages dans une référence SKU A1, le premier travail s’exécute et les deux derniers attendent les deux cycles d’exécution suivants.

>[!NOTE]
>L’exportation d’un rapport Power BI vers un fichier à l’aide de l’API `exporToFile` n’est pas prise en charge pour [Premium par utilisateur (PPU)](../../admin/service-premium-per-user-faq.md). 

|Référence SKU Azure  |Référence SKU Office  |Nombre maximal de pages de rapport simultanées  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Limites

* Le rapport que vous exportez doit résider sur une capacité Premium ou Embedded.
* Le jeu de données du rapport que vous exportez doit résider sur une capacité Premium ou Embedded.
* Pour la préversion publique, le nombre de pages de rapport Power BI exportées par heure est limité à 50 par capacité.
* Les rapports exportés ne peuvent pas dépasser une taille de fichier de 250 Mo.
* Lors de l’exportation en tant que fichier .png, les étiquettes de sensibilité ne sont pas prises en charge.
* 50 pages peuvent être incluses dans un rapport exporté. Si le rapport contient plus de pages, l’API retourne une erreur et le travail d’exportation est annulé.
* [Les signets personnels](../../consumer/end-user-bookmarks.md#personal-bookmarks) et [les filtres persistants](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) ne sont pas pris en charge.
* Les visuels Power BI répertoriés ci-dessous ne sont pas pris en charge. Lorsqu’un rapport contenant ces visuels est exporté, les parties du rapport contenant ces visuels ne sont pas rendues et un symbole d’erreur s’affiche.
    * Visuels Power BI non certifiés
    * Visuels R
    * PowerApps
    * Visuels Python
    * Visio

## <a name="code-examples"></a>Exemples de code

Lorsque vous créez un travail d’exportation, il y a trois étapes à suivre :

1. [Envoi d’une demande d’exportation](#step-1---sending-an-export-request).
2. [Interrogation](#step-2---polling).
3. [Obtention du fichier](#step-3---getting-the-file).
4. [Utilisation du flux de fichier](#step-4---using-the-file-stream).

Cette section fournit des exemples pour chaque étape.

### <a name="step-1---sending-an-export-request"></a>Étape 1 : envoi d’une demande d’exportation

La première étape consiste à envoyer une demande de rapport. Dans cet exemple, une demande d’exportation est envoyée pour une page spécifique.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null, /* Get the page names from the GetPages REST API */
    string urlFilter = null)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names
        // To get the page names use the GetPages REST API
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
        // ReportLevelFilters collection needs to be instantiated explicitly
        ReportLevelFilters = !string.IsNullOrEmpty(urlFilter) ? new List<ExportFilter>() { new ExportFilter(urlFilter) } : null,

    };

    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Étape 2 : interrogation

Après avoir envoyé une demande de rapport, utilisez l’interrogation pour savoir quand le fichier exporté que vous attendez est prêt.

```csharp
private async Task<HttpOperationResponse<Export>> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the PostExportRequest response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    HttpOperationResponse<Export> httpMessage = null;
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is not always populated
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return httpMessage;
}
```

### <a name="step-3---getting-the-file"></a>Étape 3 : obtention du fichier

Une fois que l’interrogation retourne une URL, utilisez cet exemple pour accéder au fichier reçu.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the PollExportRequest response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="step-4---using-the-file-stream"></a>Étape 4 : Utilisation du flux de fichier

Une fois que vous avez le flux de fichier, vous pouvez le gérer selon vos besoins. Par exemple, vous pouvez l’envoyer par e-mail ou l’utiliser pour télécharger les rapports exportés.

### <a name="end-to-end-example"></a>Exemple de bout en bout

Il s’agit d’un exemple de bout en bout pour l’exportation d’un rapport. Il comprend les étapes suivantes :
1. [Envoi de la demande d'exportation](#step-1---sending-an-export-request).
2. [Interrogation](#step-2---polling).
3. [Obtention du fichier](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null,  /* Get the page names from the GetPages REST API */
    string urlFilter = null)
{
    const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
    const int c_secToMillisec = 1000;
    try
    {
        Export export = null;
        int retryAttempt = 1;
        do
        {
            var exportId = await PostExportRequest(reportId, groupId, format, pageNames, urlFilter);
            var httpMessage = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
            export = httpMessage.Body;
            if (export == null)
            {
                // Error, failure in exporting the report
                return null;
            }
            if (export.Status == ExportState.Failed)
            {
                // Some failure cases indicate that the system is currently busy. The entire export operation can be retried after a certain delay
                // In such cases the recommended waiting time before retrying the entire export operation can be found in the RetryAfter header
                var retryAfter = httpMessage.Response.Headers.RetryAfter;
                if(retryAfter == null)
                {
                    // Failed state with no RetryAfter header indicates that the export failed permanently
                    return null;
                }

                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
            }
        }
        while (export.Status != ExportState.Succeeded && retryAttempt++ < c_maxNumberOfRetries);

        if (export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }

        var exportedFile = await GetExportedFile(reportId, groupId, export);

        // Now you have the exported file stream ready to be used according to your specific needs
        // For example, saving the file can be done as follows:
        /*
            var pathOnDisk = @"C:\temp\" + export.ReportName + exportedFile.FileSuffix;

            using (var fileStream = File.Create(pathOnDisk))
            {
                exportedFile.FileStream.CopyTo(fileStream);
            }
        */

        return exportedFile;
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Étapes suivantes

Vérifiez comment incorporer du contenu pour vos clients et votre organisation :

> [!div class="nextstepaction"]
>[Exporter un rapport paginé dans un fichier](export-paginated-report.md)

> [!div class="nextstepaction"]
>[Incorporer pour vos clients](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporer pour votre organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Exporter et envoyer par e-mail un rapport Power BI avec Power Automate](../../collaborate-share/service-automate-power-bi-report-export.md)
