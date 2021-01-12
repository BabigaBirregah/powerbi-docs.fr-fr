---
title: Automatiser la configuration de l’installation des applications modèles pour vos clients
description: Découvrez l’automatisation de la configuration de l’installation des applications modèles.
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: 33de464a1bb1389fadfbc7a85ded9365321e0a62
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926306"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>Configuration automatisée d’une installation d’application modèle

Les applications modèles sont un excellent moyen pour les clients de commencer à obtenir des insights à partir de leurs données. En les connectant à leurs données, les applications modèles les rendent vite opérationnels. Les applications modèles leur proposent des rapports prédéfinis qu’ils peuvent personnaliser s’ils le souhaitent.

Les clients ne savent pas toujours comment se connecter à leurs données. Le fait de devoir leur fournir ces détails au moment où ils installent une application modèle peut être à leurs yeux une contrainte.

Si vous êtes fournisseur de services de données et que vous avez créé une application modèle pour permettre à vos clients d’utiliser leurs données dans votre service, vous pouvez leur faciliter l’installation de votre application modèle. Vous pouvez automatiser la configuration des paramètres de votre application modèle. Quand le client se connecte à votre portail, il sélectionne un lien spécial que vous avez préparé. Ce lien :

- Lance l’automatisation, qui collecte les informations dont elle a besoin.
- Préconfigure les paramètres de l’application modèle.
- Redirige le client vers son compte Power BI dans lequel il peut installer l’application.

Il lui suffit alors de sélectionner **Installer**, de s’authentifier auprès de sa source de données, et le tour est joué !

L’expérience client est illustrée ici.

![Illustration de l’expérience utilisateur avec une application qui s’installe automatiquement.](media/template-apps-auto-install/high-level-flow.png)

Cet article décrit le flux de base, les prérequis, les principales étapes et les API dont vous avez besoin pour automatiser la configuration de l’installation d’une application modèle. Si vous souhaitez vous lancer directement, vous pouvez passer à ce[tutoriel](template-apps-auto-install-tutorial.md), où vous automatiserez la configuration de l’installation de l’application modèle à partir d’un exemple d’application simple que nous avons préparé et qui utilise une fonction Azure.

## <a name="basic-flow"></a>Flux de base

Le flux de base de l’automatisation de la configuration de l’installation d’une application modèle est le suivant :

1. L’utilisateur se connecte au portail de l’ISV et sélectionne le lien fourni. Ceci lance le flux automatisé. À ce stade, le portail de l’ISV prépare la configuration propre à l’utilisateur.

1. L’ISV acquiert un jeton d’*application uniquement* basé sur un [principal de service (jeton d’application uniquement)](../embedded/embed-service-principal.md), qui est inscrit dans le locataire de l’ISV.

1. À l’aide des [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/), l’ISV crée un *ticket d’installation* qui contient la configuration des paramètres propre à l’utilisateur, telle qu’elle est préparée par l’ISV.

1. L’ISV redirige l’utilisateur vers Power BI en employant une méthode de redirection ```POST``` qui contient le ticket d’installation.

1. L’utilisateur est redirigé vers son compte Power BI avec le ticket d’installation et est invité à installer l’application modèle. Quand l’utilisateur sélectionne **Installer**, l’application modèle s’installe automatiquement.

>[!Note]
>Si les valeurs des paramètres sont configurées par l’ISV pendant la création du ticket d’installation, les informations d’identification liées à la source de données ne sont fournies par l’utilisateur qu’aux ultimes étapes de l’installation. Cette organisation permet d’éviter qu’elles soient exposées à un tiers et garantit une connexion sécurisée entre l’utilisateur et les sources de données de l’application modèle.

## <a name="prerequisites"></a>Prérequis

Pour fournir une expérience d’installation préconfigurée pour votre application modèle, vous devez répondre aux prérequis suivants :

* Une licence Power BI Pro. Si vous n’êtes pas inscrit pour Power BI Pro, [inscrivez-vous pour un essai gratuit](https://powerbi.microsoft.com/pricing/) avant de commencer.
* Votre propre locataire Azure Active Directory (Azure AD) configuré. Pour savoir comment en configurer un, consultez les instructions dans [Créer un locataire Azure AD](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant).
* Un **principal de service (jeton d’application uniquement)** inscrit dans le locataire précédent. Pour plus d’informations, consultez [Incorporer du contenu Power BI avec un principal de service et un secret d’application](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal). Veillez à inscrire l’application en tant qu’**application web côté serveur**. Vous inscrivez une application web côté serveur pour créer un secret d’application. Dans ce processus, vous devez enregistrer l’*ID d’application* (ClientID) et le *secret de l’application* (ClientSecret) pour les étapes ultérieures.
* Une **application modèle paramétrable** prête pour l’installation. L’application modèle doit être créée dans le même locataire que celui où vous inscrivez votre application dans Azure AD. Pour plus d’informations, consultez [Conseils pour les applications modèles](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips) ou [Créer une application modèle dans Power BI](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create). Vous devez noter les informations suivantes de l’application modèle pour les étapes suivantes :
     * *ID d’application*, *Clé de package* et *ID de propriétaire* tels qu’ils apparaissent dans l’URL d’installation à l’issue du processus de [définition des propriétés de l’application modèle](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) exécuté dans le cadre de la création de l’application. Vous pouvez aussi obtenir le même lien en sélectionnant **Obtenir un lien** dans le volet [Release Management](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) de l’application modèle.
    * Les *noms des paramètres* tels qu’ils sont définis dans le jeu de données de l’application modèle. Les noms des paramètres sont des chaînes sensibles à la casse qui peuvent aussi être récupérés à partir de l’onglet **Valeurs des paramètres** au moment de [définir les propriétés de l’application modèle](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) ou dans les paramètres du jeux de données dans Power BI.

    >[!NOTE]
    >Vous pouvez tester votre application d’installation préconfigurée sur votre application modèle si celle-ci est prête pour l’installation, même si elle n’est pas encore publiquement disponible sur AppSource. Pour permettre aux utilisateurs situés en dehors de votre locataire d’utiliser l’application d’installation automatisée afin d’installer votre application modèle, cette dernière doit être publiquement disponible dans la [Place de marché des applications Power BI](https://app.powerbi.com/getdata/services). Avant de distribuer votre application modèle en utilisant l’application d’installation automatisée que vous créez, veillez à la publier dans l’[Espace partenaires](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer).

## <a name="main-steps-and-apis"></a>Étapes principales et API

Les principales étapes de l’automatisation de la configuration de l’installation d’une application modèle et les API dont vous avez besoin sont décrites dans les sections suivantes. Si la plupart des étapes sont effectuées avec les [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/), les exemples de code décrits ici sont produits avec le SDK .NET.

## <a name="step-1-create-a-power-bi-client-object"></a>Étape 1 : Créer un objet client Power BI

L’utilisation des API REST Power BI vous impose d’obtenir un *jeton d’accès* pour votre [principal de service](../embedded/embed-service-principal.md) auprès d’Azure AD. Vous devez obligatoirement [obtenir un jeton d’accès Azure AD](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) pour votre application Power BI avant d’effectuer des appels aux [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/).
Pour créer le client Power BI avec votre jeton d’accès, vous devez créer votre objet client Power BI, qui vous permet d’interagir avec les [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/). Pour cela, wrappez l’élément **AccessToken** avec un objet client Power BI **Microsoft.Rest.TokenCredentials**.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI client object. It's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>Étape 2 : Créer un ticket d’installation

Créez un ticket d’installation, qui est utilisé quand vous redirigez vos utilisateurs vers Power BI. L’API utilisée pour cette opération est l’API **CreateInstallTicket**.
* [Modèles d’applications - CreateInstallTicket](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

Un exemple de création d’un ticket d’installation en vue d’installer et de configurer une application modèle est disponible dans le fichier [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) de l’[exemple d’application](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample).


L’exemple de code suivant montre comment utiliser l’API REST **CreateInstallTicket** pour une application modèle.
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK.
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>Étape 3 : Rediriger les utilisateurs vers Power BI avec le ticket

Une fois que vous avez créé un ticket d’installation, vous vous en servez pour rediriger vos utilisateurs vers Power BI et leur permettre de poursuivre l’installation et la configuration de l’application modèle. Vous utilisez une redirection de méthode ```POST``` vers l’URL d’installation de l’application modèle, avec le ticket d’installation dans le corps de la demande.

Il existe plusieurs méthodes documentées pour émettre une redirection à l’aide de requêtes ```POST```. Le choix de l’une ou de l’autre dépend du scénario et de la façon dont vos utilisateurs interagissent avec votre portail ou votre service.

Un exemple simple, essentiellement utilisé à des fins de test, fait appel à un formulaire comprenant un champ masqué, dont l’envoi se fait automatiquement au moment du chargement.

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

La réponse suivante de l’[exemple d’application](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample) contient le ticket d’installation et redirige automatiquement les utilisateurs vers Power BI. La réponse pour cette fonction Azure correspond au formulaire auto-envoyé que nous avons vu dans l’exemple HTML précédent.

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>Il existe différentes méthodes d’utilisation des redirections de navigateur ```POST```. Vous devez toujours utiliser la méthode la plus sécurisée, qui dépend des besoins et des restrictions de votre service. Rappelez-vous que certains formulaires de redirection non sécurisée peuvent entraîner l’exposition de vos utilisateurs ou de votre service à des problèmes de sécurité.

## <a name="step-4-move-your-automation-to-production"></a>Étape 4 : Passer votre automatisation en production

Quand l’automatisation que vous avez conçue est prête, pensez à la passer en production.

## <a name="next-steps"></a>Étapes suivantes

* Essayez notre [tutoriel](template-apps-auto-install-tutorial.md), qui utilise une fonction Azure simple pour automatiser la configuration de l’installation d’une application modèle.
* D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
