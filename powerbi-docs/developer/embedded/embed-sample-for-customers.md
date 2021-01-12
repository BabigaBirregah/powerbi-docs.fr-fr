---
title: Incorporer du contenu dans votre application d’analytique incorporée Power BI pour offrir de meilleurs insights à vos clients via la BI incorporée
description: Découvrez comment incorporer un rapport, un tableau de bord ou une vignette dans un exemple d’analytique incorporée dans Power BI. Obtenez de meilleurs insights BI incorporés avec l’analytique incorporée Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/22/2020
ms.openlocfilehash: f6ca898bafff0b3375df65b63f913eb81d8dc006
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888946"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>Tutoriel : Incorporer du contenu Power BI en utilisant un exemple d’application *Incorporer pour vos clients*

L’**Analytique incorporée** et **Power BI Embedded** (l’offre Azure) vous permettent d’incorporer dans votre application des contenus Power BI comme des rapports, des tableaux de bord et des vignettes.

Ce didacticiel vous montre comment effectuer les opérations suivantes :
>[!div class="checklist"]
>* Configurer votre environnement incorporé.
>* Configurer un exemple d’application *Incorporer pour vos clients* (également appelée *L’application possède les données*).

Pour utiliser votre application, vos utilisateurs n’ont pas besoin de se connecter à Power BI ou de disposer d’une licence Power BI.

Nous vous recommandons d’utiliser la méthode *Incorporer pour vos clients* pour incorporer votre contenu Power BI si vous êtes éditeur de logiciels indépendant (ISV) ou développeur, et que vous voulez créer des applications pour des tiers.

## <a name="code-sample-specifications"></a>Spécifications de l’exemple de code

Ce tutoriel inclut des instructions sur la configuration d’un exemple d’application *Incorporer pour vos clients* dans un des langages suivants :

* .NET Framework
* .NET Core
* Java
* Node JS
* Python

Les exemples de code prennent en charge les navigateurs suivants :

* Google Chrome

* Microsoft Edge

* Mozilla Firefox

## <a name="prerequisites"></a>Prérequis

Avant de commencer ce tutoriel, vérifiez que vous disposez des dépendances de Power BI et du code listées ci-dessous :

* **Dépendances de Power BI**

    * Votre propre [locataire Azure Active Directory](create-an-azure-active-directory-tenant.md).

    * Pour authentifier votre application auprès de Power BI, vous avez besoin d’un des éléments suivants :

        * [Principal de service](embed-service-principal.md) : un [objet de principal de service](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) Azure Active Directory (Azure AD) qui permet à Azure AD d’authentifier votre application.

        * Licence [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) : il s’agit de votre **utilisateur maître** et votre application va l’utiliser pour s’authentifier auprès de Power BI.

        * Une licence Power BI [Premium par utilisateur](../../admin/service-premium-per-user-faq.md) : il s’agit de votre **utilisateur maître** et votre application va l’utiliser pour s’authentifier auprès de Power BI.

    >[!NOTE]
    >Pour [passer en production](move-to-production.md), vous avez besoin d’une [capacité](embedded-capacity.md).

* **Dépendances du code**

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)
    
    
    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [SDK .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core) (ou ultérieur)
    
    * Un environnement de développement intégré (IDE). Nous vous recommandons d’utiliser un des environnements suivants :
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK (ou JRE)](https://www.oracle.com/java/technologies/)
    
    * [IDE Eclipse](https://www.eclipse.org/downloads/packages/) : vérifiez que vous disposez de *Eclipse for Java EE Developers* (Enterprise Edition)
    
    * [Distributions binaires d’Apache Tomcat](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node JS](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * Un environnement de développement intégré (IDE). Nous vous recommandons d’utiliser un des environnements suivants :
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/) (ou ultérieur)
    
        >[!NOTE]
        >* Si vous installez *Python* pour la première fois, sélectionnez l’option **Add Python to PATH** pour ajouter l’installation à la variable `PATH`.
        >* Si *Python* est déjà installé, vérifiez que la variable `PATH` inclut son chemin d’installation. Pour plus d’informations, consultez la documentation Python [Excursus: Setting environment variables](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables) de la documentation Python (ce lien fait référence à Python 3).
    
    * Un environnement de développement intégré (IDE). Nous vous recommandons d’utiliser un des environnements suivants :
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>Méthode

Pour créer un exemple d’application *Incorporer pour vos clients*, effectuez les étapes suivantes :

1. [Sélectionnez votre méthode d’authentification](#step-1---select-your-authentication-method).

2. [Inscrivez une application Azure AD](#step-2---register-an-azure-ad-application).

3. [Créez un espace de travail Power BI](#step-3---create-a-power-bi-workspace).

4. [Créez et publiez un rapport Power BI](#step-4---create-and-publish-a-power-bi-report).

5. [Obtenez les valeurs des paramètres d’incorporation](#step-5---get-the-embedding-parameter-values).

6. [Accès à l’API du principal de service](#step-6---service-principal-api-access)
 
7. [Activez l’accès à l’espace de travail](#step-7---enable-workspace-access).

8. [Incorporez votre contenu](#step-8---embed-your-content).

## <a name="step-1---select-your-authentication-method"></a>Étape 1 - Sélectionner votre méthode d’authentification

Votre solution incorporée va varier en fonction de la méthode d’authentification que vous sélectionnez. Par conséquent, il est important de comprendre les différences entre les méthodes d’authentification et de déterminer celle qui convient le mieux à votre solution.

Le tableau ci-dessous décrit quelques-unes des principales différences entre les méthodes d’authentification [principal de service](embed-service-principal.md) et **utilisateur maître**.

|Considération  |Principal du service  |Utilisateur maître  |
|---------|---------|---------|
|Mechanism     |L’[objet de principal de service](/azure/active-directory/develop/app-objects-and-service-principals.md#service-principal-object) de votre application Azure AD permet à Azure AD d’authentifier votre application de solution incorporée auprès de Power BI.        |Votre application Azure AD utilise les informations d’identification (nom d’utilisateur et mot de passe) d’un utilisateur Power BI pour s’authentifier auprès de Power BI.         |
|Sécurité     |*Principal de service* est la méthode d’autorisation recommandée d’Azure AD. Si vous utilisez un principal de service, * vous pouvez vous authentifier en utilisant un *secret d’application* ou un *certificat*.</br></br>Ce tutoriel décrit l’utilisation du *principal de service* avec un *secret d’application*. Pour incorporer en utilisant un *principal de service* et un *certificat*, reportez-vous à l’article [principal de service avec un certificat](embed-service-principal-certificate.md).         |Cette méthode d’authentification n’est pas considérée comme étant aussi sécurisée que l’utilisation d’un *principal de service*. Cela est dû au fait que vous devez être vigilant avec les informations d’identification (nom d’utilisateur et mot de passe) de l’*utilisateur maître*. Par exemple, vous ne devez pas les exposer dans votre application d’incorporation, et vous devez changer le mot de passe fréquemment.         |
|Autorisations déléguées d’Azure AD |Non obligatoire. |Votre *utilisateur maître* ou un administrateur doit donner son consentement à votre application pour qu’elle puisse accéder aux [autorisations](/azure/active-directory/develop/v2-permissions-and-consent) de l’API REST Power BI (également appelées « étendues »). Par exemple, *Report.ReadWrite.All*. |
|Accès au service Power BI |Vous ne pouvez pas accéder au service Power BI avec un *principal de service*.|Vous pouvez accéder au service Power BI avec les informations d’identification de votre *utilisateur maître*.|
|Licence     |Ne nécessite pas de licence Pro. Vous pouvez utiliser le contenu de n’importe quel espace de travail dont vous êtes membre ou administrateur.         |Nécessite une licence [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md).         |

## <a name="step-2---register-an-azure-ad-application"></a>Étape 2 - Inscrire une application Azure AD

L’inscription de votre application auprès d’Azure AD vous permet les actions suivantes :
> [!div class="checklist"]
>* Établir une identité pour votre application
>* Autoriser votre application à accéder aux [API REST Power BI](/rest/api/power-bi/)
>* Si vous utilisez un *utilisateur maître* : spécifiez les [autorisations REST Power BI](/azure/active-directory/develop/v2-permissions-and-consent) de votre application

Pour inscrire votre application auprès d’Azure AD, suivez les instructions données dans [Inscrire votre application](register-app.md).

>[!NOTE]
>Avant d’inscrire votre application, vous devez décider de la méthode d’authentification à utiliser, *principal de service* ou *utilisateur maître*.

## <a name="step-3---create-a-power-bi-workspace"></a>Étape 3 - Créer un espace de travail Power BI

Power BI conserve vos rapports, tableaux de bord et vignettes dans un espace de travail. Pour incorporer ces éléments, vous devez les créer et les charger dans un espace de travail.

>[!TIP]
>Si vous disposez déjà d’un espace de travail, vous pouvez passer cette étape.

Pour créer un espace de travail, effectuez les actions suivantes :

1. Connectez-vous à Power BI.

2. sélectionnez **Espaces de travail**.

3. Sélectionnez **Créer un espace de travail**.

4. Nommez votre espace de travail, puis sélectionnez **Enregistrer**.

## <a name="step-4---create-and-publish-a-power-bi-report"></a>Étape 4 - Créer et publier un rapport Power BI

L’étape suivante consiste à créer un rapport et à le charger dans votre espace de travail. Vous pouvez [créer votre propre rapport](/powerbi-docs/fundamentals/desktop-getting-started#build-reports) en utilisant Power BI Desktop, puis le [publier](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) dans votre espace de travail. Vous pouvez aussi charger un exemple de rapport dans votre espace de travail.

>[!Tip]
>Si vous disposez déjà d’un espace de travail avec un rapport, vous pouvez passer cette étape.

Pour télécharger un exemple de rapport et le publier dans votre espace de travail, effectuez les étapes suivantes :

1. Ouvrez le dossier GitHub des [exemples Power BI Desktop](https://github.com/Microsoft/PowerBI-Desktop-Samples).

2. Sélectionnez **Code**, puis sélectionnez **Download zip** (Télécharger le fichier zip).

    :::image type="content" source="media/embed-sample-for-customers/download-sample-report.png" alt-text="Capture d’écran montrant l’option de téléchargement du fichier ZIP dans les exemples Power BI Desktop de GitHub":::

3. Extrayez le fichier ZIP téléchargé et accédez au dossier **Samples Reports**.

4. Sélectionnez un rapport à incorporer, puis [publiez-le](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) dans votre espace de travail.

## <a name="step-5---get-the-embedding-parameter-values"></a>Étape 5 - Obtenir les valeurs des paramètres d’incorporation

Pour incorporer votre contenu, vous devez obtenir certaines valeurs de paramètre. Le tableau ci-dessous montre les valeurs nécessaires, et indique si elles s’appliquent à la méthode d’authentification *principal de service*, à la méthode d’authentification, *utilisateur maître*, ou aux deux.

Avant d’incorporer votre contenu, vérifiez que vous disposez de toutes les valeurs listées ci-dessous. Certaines des valeurs diffèrent selon la méthode d’authentification que vous utilisez.

|Paramètre   |Principal du service   |Utilisateur maître  |
|-------------------|---|---|
|[ID client](#client-id) |![S’applique à.](../../media/yes.png) |![S’applique à.](../../media/yes.png) |
|[ID de l’espace de travail](#workspace-id)     |![S’applique à.](../../media/yes.png) |![S’applique à.](../../media/yes.png) |
|[ID du rapport](#report-id)           |![S’applique à.](../../media/yes.png) |![S’applique à.](../../media/yes.png) |
|[Clé secrète client](#client-secret) |![S’applique à.](../../media/yes.png) |![Non applicable.](../../media/no.png) |
|[Tenant ID](#tenant-id)                 |![S’applique à.](../../media/yes.png) |![Non applicable.](../../media/no.png) |
|[Nom d’utilisateur Power BI](#power-bi-username-and-password)   |![Non applicable.](../../media/no.png) |![S’applique à.](../../media/yes.png) |
|[Mot de passe Power BI](#power-bi-username-and-password)   |![Non applicable.](../../media/no.png) |![S’applique à.](../../media/yes.png) |

### <a name="client-id"></a>ID client

>[!TIP]
>**S’applique à :** ![S’applique à.](../../media/yes.png)Principal de service ![S’applique à. ](../../media/yes.png)Utilisateur maître

Pour obtenir le GUID de l’ID client (également appelé *ID d’application*), effectuez les étapes suivantes :

1. Connectez-vous à [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Recherchez **Inscriptions d’applications**, puis sélectionnez le lien **Inscriptions d’applications**.

3. Sélectionnez l’application Azure AD que vous utilisez pour l’incorporation de votre contenu Power BI.

4. Dans la section **Vue d’ensemble**, copiez le GUID **ID d’application (client)** .

### <a name="workspace-id"></a>ID de l’espace de travail

>[!TIP]
>**S’applique à :** ![S’applique à.](../../media/yes.png)Principal de service ![S’applique à. ](../../media/yes.png)Utilisateur maître

Pour obtenir le GUID de l’ID d’espace de travail, effectuez les étapes suivantes :

1. Connectez-vous au service Power BI.

2. Ouvrez le rapport que vous voulez incorporer.

3. Copiez le GUID à partir de l’URL. Le GUID est le nombre qui se trouve entre **/groups/** et **/reports/** .

    :::image type="content" source="media/embed-sample-for-customers/workspace-id.png" alt-text="Capture d’écran montrant le GUID de l’ID d’espace de travail dans l’URL du service Power BI":::

### <a name="report-id"></a>ID du rapport

>[!TIP]
>**S’applique à :** ![S’applique à.](../../media/yes.png)Principal de service ![S’applique à. ](../../media/yes.png)Utilisateur maître

1. Connectez-vous au service Power BI.

2. Ouvrez le rapport que vous voulez incorporer.

3. Copiez le GUID à partir de l’URL. Le GUID est le nombre qui se trouve entre **/reports/** et **/ReportSection/** .

    :::image type="content" source="media/embed-sample-for-customers/report-id.png" alt-text="Capture d’écran montrant le GUID de l’ID de rapport dans l’URL du service Power BI":::

### <a name="client-secret"></a>Clé secrète client

>[!TIP]
>**S’applique à :** ![S’applique à.](../../media/yes.png)Principal de service ![Ne s’applique pas à.](../../media/no.png)Utilisateur maître

Pour obtenir le secret client, effectuez les étapes suivantes :

1. Connectez-vous à [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Recherchez **Inscriptions d’applications**, puis sélectionnez le lien **Inscriptions d’applications**.

3. Sélectionnez l’application Azure AD que vous utilisez pour l’incorporation de votre contenu Power BI.

4. Sous **Gérer**, sélectionnez **Certificats et secrets**.

5. Sous **Secrets client**, sélectionnez **Nouveau secret client**.

6. Dans la fenêtre contextuelle **Ajouter un secret client**, spécifiez une description du secret de votre application, sélectionnez la date d’expiration du secret de l’application, puis sélectionnez **Ajouter**.

7. Dans la section **Secrets client**, copiez la chaîne qui se trouve dans la colonne **Valeur** du secret de l’application nouvellement créé. La valeur du secret client est votre *ID de client*.

### <a name="tenant-id"></a>ID client

>[!TIP]
>**S’applique à :** ![S’applique à.](../../media/yes.png)Principal de service ![Ne s’applique pas à.](../../media/no.png)Utilisateur maître

Pour obtenir le GUID de l’ID de locataire, effectuez les étapes suivantes :

1. Connectez-vous à [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Recherchez **Inscriptions d’applications**, puis sélectionnez le lien **Inscriptions d’applications**.

3. Sélectionnez l’application Azure AD que vous utilisez pour l’incorporation de votre contenu Power BI.

4. Dans la section **Vue d’ensemble**, copiez le GUID de l’**ID de l’annuaire (locataire)** .

### <a name="power-bi-username-and-password"></a>Nom d’utilisateur et mot de passe Power BI

>[!TIP]
>**S’applique à :** ![Ne s’applique pas à.](../../media/no.png)Principal de service ![S’applique à.](../../media/yes.png)Utilisateur maître

Obtenez le *nom d’utilisateur* et le *mot de passe* de l’utilisateur Power BI que vous utilisez comme **utilisateur maître**. C’est le même utilisateur que celui que vous avez utilisé dans le service Power BI pour créer un espace de travail et y charger un rapport.

## <a name="step-6---service-principal-api-access"></a>Étape 6 - Accès à l’API du principal de service

>[!TIP]
>**S’applique à :** ![S’applique à.](../../media/yes.png)Principal de service ![Ne s’applique pas à.](../../media/no.png)Utilisateur maître
>
>Cette étape est nécessaire seulement si vous utilisez la méthode d’authentification *principal de service*. Si vous utilisez un *utilisateur maître*, ignorez cette étape et passez à [Étape 7 - Activer l’accès à l’espace de travail](#step-7---enable-workspace-access).

Pour qu’une application Azure AD soit en mesure d’accéder au contenu et aux API de Power BI, un administrateur Power BI doit activer l’accès au principal de service dans le portail d’administrateur Power BI. Si vous n’êtes pas administrateur de votre locataire, demandez à l’administrateur du locataire d’activer les *Paramètres du client* pour vous.
        
1. Dans *Service Power BI*, sélectionnez **Paramètres** > **Paramètres** > **Portail d’administration**.
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="Capture d’écran montrant l’option de menu Paramètres d’administration dans le menu des paramètres du service Power bi":::
        
2. Sélectionnez **Paramètres du client**, puis faites défiler vers le bas jusqu’à la section **Paramètres de développeur**.
        
3. Développez **Autoriser les principaux de service à utiliser les API Power BI** et activez cette option.
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="Capture d’écran montrant comment activer l’option des paramètres de développeur, dans l’option de menu Paramètres du client, dans le service Power BI":::
        
>[!NOTE]
>Lors de l’utilisation d’un *principal de service*, il est recommandé de limiter son accès aux paramètres du locataire en utilisant un *groupe de sécurité*. Pour plus d’informations sur cette fonctionnalité, consultez les sections suivantes dans l’article [Principal de service](embed-service-principal.md) :
> * [Créer un groupe de sécurité Azure AD](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [Activer les paramètres d’administration du service Power BI](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>Étape 7 - Activer l’accès à l’espace de travail

Pour activer vos artefacts d’accès à l’application Azure AD, comme les rapports, tableaux de bord et jeux de données du service Power BI, ajoutez le *principal de service* ou l’*utilisateur maître* en tant que *membre* ou *administrateur* à votre espace de travail.

1. Connectez-vous au service Power BI.

2. Accédez à l’espace de travail pour lequel vous souhaitez activer l’accès, puis dans le menu **Plus**, sélectionnez **Accès à l’espace de travail**.

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Capture d’écran montrant le bouton d’accès à l’espace de travail dans le menu Plus d’un espace de travail Power BI.":::

3. Dans le volet **Accès**, en fonction de la méthode d’authentification que vous utilisez, copiez le *principal de service* ou l’*utilisateur maître* dans la zone de texte **Saisissez une adresse e-mail**.

    >[!NOTE]
    >Si vous utilisez un *principal de service*, son nom correspond au nom que vous avez donné à votre application Azure AD.

5. Sélectionnez **Ajouter**.

## <a name="step-8---embed-your-content"></a>Étape 8 - Incorporer votre contenu

L’exemple d’application incorporée Power BI vous permet de créer une application Power BI *Incorporer pour vos clients*.

Effectuez les étapes suivantes pour modifier l’exemple d’application *Incorporer pour vos clients* de façon à incorporer votre rapport Power BI.  

1. Ouvrez le dossier [Power BI-Developer-Samples](https://github.com/microsoft/PowerBI-Developer-Samples).

2. Sélectionnez **Code**, puis sélectionnez **Download zip** (Télécharger le fichier zip).

    :::image type="content" source="media/embed-sample-for-customers/developer-samples.png" alt-text="Capture d’écran montrant l’option de téléchargement du fichier ZIP dans les exemples Power BI pour les développeurs de GitHub":::

3. Extrayez le fichier ZIP téléchargé et accédez au dossier **PowerBI-Developer-Samples-master**.

4. Selon le langage que votre application doit utiliser, ouvrez un de ces dossiers :

* .NET Core
* .NET Framework
* Java
* Node JS
* Python
    >[!NOTE]
    >Les exemples d’applications *Incorporer pour vos clients* prennent en charge seulement les langages listés ci-dessus. L’exemple d’application *React TS* prend en charge seulement la solution *[Incorporer pour votre organisation](embed-sample-for-your-organization.md)* .

5. Ouvrez le dossier **Embed for your customers**.

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. Ouvrez l’exemple d’application *Incorporer pour vos clients* en utilisant une de ces méthodes :

    * Si vous utilisez [Visual Studio](https://visualstudio.microsoft.com/), ouvrez le fichier **AppOwnsData.sln**.

    * Si vous utilisez [Visual Studio Code](https://code.visualstudio.com/), ouvrez le dossier **App Owns Data**.

7. Ouvrez **appsettings.json**.

8. En fonction de votre méthode d’authentification, entrez les valeurs de paramètre suivantes :

    |Paramètre            |Principal du service  |Utilisateur maître  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |ServicePrincipal         |MasterUser         |
    |`ClientId`           |[ID de client](#client-id) de votre application Azure AD         |[ID de client](#client-id) de votre application Azure AD         |
    |`TenantId`           |Votre [ID de locataire](#tenant-id) Azure AD         |N/A         |
    |`PbiUsername`        |N/A         |Nom d’utilisateur de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`PbiPassword`        |N/A         |Mot de passe de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`ClientSecret`       |Votre [secret client](#client-secret) Azure AD         |N/A         |
    |`WorkspaceId`        |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)          |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)         |
    |`ReportId`           |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)            |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)         |

9. Exécutez le projet en sélectionnant l’option appropriée :

    * Si vous utilisez **Visual Studio**, sélectionnez **IIS Express** (lecture).

    * Si vous utilisez **Visual Studio Code**, sélectionnez **Exécuter > Démarrer le débogage**.

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. En utilisant [Visual Studio](https://visualstudio.microsoft.com/), ouvrez le fichier **AppOwnsData.sln**.

7. Ouvrez **Web.config**.

8. En fonction de votre méthode d’authentification, entrez les valeurs de paramètre suivantes :

    |Paramètre            |Principal du service  |Utilisateur maître  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`applicationId`           |[ID de client](#client-id) de votre application Azure AD         |[ID de client](#client-id) de votre application Azure AD         |
    |`workspaceId`        |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)          |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)         |
    |`reportId`           |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)            |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)         |
    |`pbiUsername`        |N/A         |Nom d’utilisateur de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/A         |Mot de passe de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`applicationSecret`       |Votre [secret client](#client-secret) Azure AD         |N/A         |
    |`tenant`           |Votre [ID de locataire](#tenant-id) Azure AD         |N/A         |

9. Exécutez le projet en sélectionnant **IIS Express** (lecture).

>[!NOTE]
>Si vous ne voyez pas le rapport incorporé lors de l’exécution de l’exemple d’application, actualisez les packages Power BI en effectuant les étapes suivantes :
>1. Cliquez avec le bouton droit sur le nom du projet (AppOwnesData), puis sélectionnez **Gérer les packages NuGet**.
>2. Recherchez **Power BI JavaScript**, puis réinstallez le package.
>
>Pour plus d’informations, consultez [Comment réinstaller et mettre à jour des packages](/nuget/consume-packages/reinstalling-and-updating-packages).

# <a name="java"></a>[Java](#tab/java)

6. Ouvrez **Eclipse** et suivez les instructions décrites ci-dessous.

    >[!NOTE]
    >Pour obtenir des instructions pour l’*exemple d’application Incorporer pour votre client* Java, consultez [IDE Eclipse pour les développeurs Java EE](https://www.eclipse.org/downloads/packages/) (Enterprise Edition). Si vous utilisez une autre application, vous devez la configurer vous-même.

7. Ajoutez le serveur Tomcat à Eclipse :

    a. Sélectionnez **Window (Fenêtre)**  > **Show View (Montrer la vue)**  > **Servers (Serveurs)** .

    b. Dans l’onglet des serveurs, sélectionnez **No servers are available. Cliquez sur ce lien pour créer un serveur** (Aucun serveur n’est disponible. Cliquez sur ce lien pour créer un serveur).

    c. Dans la fenêtre **Define a New Server** (Définir un nouveau serveur), développez **Apache**, puis sélectionnez le serveur Tomcat que vous exécutez sur votre ordinateur. Par exemple, *Tomcat v9.0 Server* (Serveur Tomcat v9.0).

    d. Sélectionnez **Suivant**.

    e. Dans la fenêtre **Tomcat Server**, sélectionnez **Parcourir**, puis accédez au dossier qui contient le serveur Tomcat.

    f. Dans la fenêtre **Tomcat Server** (Serveur Tomcat), sélectionnez **Installed JREs** (JRE installés).

    g. Dans la fenêtre **Installed JREs**, sélectionnez le *jre* disponible, puis sélectionnez **Apply and Close** (Appliquer et fermer).

    h. Dans la fenêtre **Tomcat Server**, sélectionnez **Finish** (Terminer). Vous pouvez voir le serveur Tomcat sous l’onglet *Servers* (Serveurs).

8. Ouvrez le projet dans Eclipse :

    >[!IMPORTANT]
    >Eclipse peut rencontrer des problèmes si le nom du chemin est trop long. Pour éviter ce problème, vérifiez que le dossier de votre exemple d’application n’est pas imbriqué trop profondément dans la structure de dossiers de votre machine.

    a. Sélectionnez **File** (Fichier), puis sélectionnez **Open Projects from File System** (Ouvrir les projets à partir du système de fichiers).

    b. Dans la fenêtre **Import Projects form File System or Archive** (Importer des projets depuis le système de fichiers ou une archive), sélectionnez **Directory** (Répertoire) et ouvrez le dossier **AppOwnsData**.

    c. Sélectionnez **Terminer**.

9. Ajoutez le serveur Tomcat au projet :

    a. Dans le volet **Package Explorer** (Explorateur de packages), cliquez avec le bouton droit sur **AppOwnsData**, puis sélectionnez **Properties** (Propriétés).

    b. Dans la fenêtre **Properties for AppOwnesData** (Propriétés pour AppOwnesData), sélectionnez **Targeted Runtimes** (Runtimes ciblés), puis sélectionnez **Apache Tomcat**. Cette sélection va inclure inclut la version d’*Apache Tomcat* que vous utilisez, par exemple *Apache Tomact v9.0*.

    c. Sélectionnez **Apply and Close** (Appliquer et fermer).

10. Renseignez les paramètres requis

    a. Dans **Package explorer** (Explorateur de packages), développez le projet **AppOwnsData**.

    b. Développez **Java Resources** (Ressources Java).

    c. Développez **src**.

    d. Développez **com.embedsample.appoensdata.config**.

    e. Ouvrez **Config.java**.

    f. En fonction de votre méthode d’authentification, entrez les valeurs de paramètre suivantes :

    |Paramètre            |Principal du service  |Utilisateur maître  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`workspaceId`        |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)          |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)         |
    |`reportId`           |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)            |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)         | 
    |`clientId`           |[ID de client](#client-id) de votre application Azure AD         |[ID de client](#client-id) de votre application Azure AD         |
    |`pbiUsername`        |N/A         |Nom d’utilisateur de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/A         |Mot de passe de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`tenantId`           |Votre [ID de locataire](#tenant-id) Azure AD         |N/A         |
    |`appSecret`       |Votre [secret client](#client-secret) Azure AD         |N/A         |

11. Exécuter le projet

    a. Dans le **Package Explorer** (Explorateur de packages), cliquez avec le bouton droit sur **AppOwnesData**.

    b. Sélectionnez **Run as (Exécuter en tant que)**   > **Run on Server (Exécuter sur le serveur)** .

    c. Dans la fenêtre **Run on Server**, sélectionnez **Choose an existing server** (Choisir un serveur existant) et sélectionnez le serveur *Tomcat*.

    d. Sélectionnez **Terminer**.

# <a name="node-js"></a>[Node JS](#tab/node-js)

6. Ouvrez le dossier **App Owns Data** en utilisant votre IDE préféré. Nous vous recommandons d’utiliser un des environnements suivants :

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. Ouvrez un terminal et installez les dépendances nécessaires en exécutant : `npm install`.

8. Développez le dossier **Config** et ouvrez **config.json**.

9. En fonction de votre méthode d’authentification, entrez les valeurs de paramètre suivantes :

    |Paramètre            |Principal du service  |Utilisateur maître  |
    |---------------------|---------|---------|
    |`authenticationMode` |ServicePrincipal         |MasterUser         |
    |`clientId`           |[ID de client](#client-id) de votre application Azure AD         |[ID de client](#client-id) de votre application Azure AD         |
    |`workspaceId`        |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)          |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)         |
    |`reportId`           |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)            |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)         |
    |`pbiUsername`        |N/A         |Nom d’utilisateur de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/A         |Mot de passe de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`clientSecret`       |Votre [secret client](#client-secret) Azure AD         |N/A         |
    |`tenantId`           |Votre [ID de locataire](#tenant-id) Azure AD         |N/A         |

10. Exécutez le projet en effectuant les étapes suivantes :

    a. Dans le terminal de l’IDE, exécutez `npm start`.

    b. Ouvrez un nouvel onglet dans votre navigateur et accédez à [http://localhost:5300](http://localhost:5300).

# <a name="python"></a>[Python](#tab/python)

6. Ouvrez **PowerShell** ou **Invite de commandes**.

7. Vérifiez que vous êtes dans le dossier **Python** > **Incorporer pour vos clients**, et que le fichier **requirements.txt** se trouve dans le dossier, puis exécutez `pip3 install -r requirements.txt`.

8. Ouvrez le dossier **App Owns Data** en utilisant votre IDE préféré. Nous vous recommandons d’utiliser un des environnements suivants :

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. Ouvrez **config.py**.

10. En fonction de votre méthode d’authentification, entrez les valeurs de paramètre suivantes :

    |Paramètre            |Principal du service  |Utilisateur maître  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |ServicePrincipal         |MasterUser         |
    |`WORKSPACE_ID`        |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)          |ID de l’espace de travail avec votre rapport incorporé ; consultez [ID d’espace de travail](#workspace-id)         |
    |`REPORT_ID`           |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)            |ID du rapport que vous incorporez ; consultez [ID de rapport](#report-id)         |
    |`TENANT_ID`           |Votre [ID de locataire](#tenant-id) Azure AD         |N/A         |
    |`CLIENT_ID`           |[ID de client](#client-id) de votre application Azure AD         |[ID de client](#client-id) de votre application Azure AD         |
    |`CLIENT_SECRET`       |Votre [secret client](#client-secret) Azure AD         |N/A         |
    |`POWER_BI_USER`        |N/A         |Nom d’utilisateur de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |
    |`POWER_BI_PASS`        |N/A         |Mot de passe de votre *utilisateur maître* ; consultez [nom d’utilisateur et mot de passe Power BI](#power-bi-username-and-password)         |

11. Enregistrez le fichier.

12. Exécutez le projet en effectuant les étapes suivantes :

    a. Dans **PowerShell** ou **Invite de commandes**, accédez au dossier **Python** > **Incorporer pour vos clients** > **AppOwnesData**, puis exécutez `flask run`.

    b. Ouvrez un nouvel onglet dans votre navigateur et accédez à [http://localhost:5300](http://localhost:5300).

---

## <a name="developing-your-application"></a>Développement de votre application

Après avoir configuré et exécuté l’exemple d’application *Incorporer pour vos clients*, vous pouvez commencer à développer votre propre application.

Quand vous êtes prêt, examinez les exigences pour [passer en production](move-to-production.md). Vous aurez également besoin d’une [capacité](embedded-capacity.md), et vous devez passer en revue l’article sur la [planification de la capacité](embedded-capacity-planning.md) pour établir la référence SKU correspondant le mieux à vos besoins.


## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
>[Passer en production](move-to-production.md)

>[!div class="nextstepaction"]
>[Incorporer pour votre organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Incorporer des rapports paginés pour vos clients](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Incorporer des rapports paginés pour votre organisation](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Poser des questions à la communauté Power BI](https://community.powerbi.com/)