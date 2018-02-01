---
title: "Créer un principal de service Azure avec Node.js"
description: "Apprendre à utiliser l’authentification par principale de service via Node.js"
author: craigshoemaker
manager: routlaw
ms.author: cshoe
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 73afa36571abcb7c87273e9c2b3665e199786931
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="73b25-103">Créer un principal de service Azure avec Node.js</span><span class="sxs-lookup"><span data-stu-id="73b25-103">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="73b25-104">Lorsqu’une application doit accéder à des ressources, vous pouvez configurer une identité pour l’application et authentifier l’application avec ses propres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="73b25-104">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="73b25-105">Cette identité est connue en tant que *principal de service*.</span><span class="sxs-lookup"><span data-stu-id="73b25-105">This identity is known as a *service principal*.</span></span> <span data-ttu-id="73b25-106">Essentiellement, vous créez des clés pour votre compte Azure Active Directory que vous fournissez au SDK pour l’authentification au lieu de demander l’intervention de l’utilisateur ou bien une combinaison nom d’utilisateur/mot de passe.</span><span class="sxs-lookup"><span data-stu-id="73b25-106">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="73b25-107">L’approche de principal de service vous permet de :</span><span class="sxs-lookup"><span data-stu-id="73b25-107">The service principal approach enables you to:</span></span>
- <span data-ttu-id="73b25-108">Affecter à l’identité de l’application des autorisations différentes de vos propres autorisations.</span><span class="sxs-lookup"><span data-stu-id="73b25-108">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="73b25-109">En règle générale, ces autorisations sont strictement limitées à ce que l’application doit faire.</span><span class="sxs-lookup"><span data-stu-id="73b25-109">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="73b25-110">Utilisez un certificat pour l’authentification lors de l’exécution d’un script sans assistance.</span><span class="sxs-lookup"><span data-stu-id="73b25-110">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="73b25-111">Cette rubrique vous montre trois techniques de création d’un principal de service.</span><span class="sxs-lookup"><span data-stu-id="73b25-111">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="73b25-112">Portail Azure</span><span class="sxs-lookup"><span data-stu-id="73b25-112">Azure portal</span></span>
- <span data-ttu-id="73b25-113">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="73b25-113">Azure CLI 2.0</span></span>
- <span data-ttu-id="73b25-114">Kit de développement logiciel (SDK) Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="73b25-114">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="73b25-115">Création d’un principal de service à l’aide du portail Azure</span><span class="sxs-lookup"><span data-stu-id="73b25-115">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="73b25-116">Suivez les étapes planifiées dans la rubrique, [Utiliser le portail pour créer une application et un principal de service Azure Active Directory pouvant accéder aux ressources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), pour générer le principal de service.</span><span class="sxs-lookup"><span data-stu-id="73b25-116">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="73b25-117">Création d’un principal de service à l’aide d’Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="73b25-117">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="73b25-118">La création d’un principal de service à l’aide d’[Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) peut suivre les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="73b25-118">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="73b25-119">Téléchargez [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="73b25-119">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="73b25-120">Ouvrez une fenêtre de terminal.</span><span class="sxs-lookup"><span data-stu-id="73b25-120">Open a terminal window.</span></span>

3. <span data-ttu-id="73b25-121">Tapez la commande suivante pour démarrer le processus d’ouverture de session :</span><span class="sxs-lookup"><span data-stu-id="73b25-121">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="73b25-122">Appeler `az login` résulte en une URL et un code.</span><span class="sxs-lookup"><span data-stu-id="73b25-122">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="73b25-123">Accédez à l’URL spécifiée, entrez le code, puis connectez-vous avec votre identité Azure (Cela peut se produire automatiquement si vous êtes déjà connecté).</span><span class="sxs-lookup"><span data-stu-id="73b25-123">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="73b25-124">Vous serez alors en mesure d’accéder à votre compte via l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="73b25-124">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="73b25-125">Obtenez vos ID d’abonnement et de client :</span><span class="sxs-lookup"><span data-stu-id="73b25-125">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="73b25-126">Voici un exemple de sortie :</span><span class="sxs-lookup"><span data-stu-id="73b25-126">The following shows an example of the output:</span></span>

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    <span data-ttu-id="73b25-127">**Prenez note de l’ID d’abonnement car il sera utilisé à l’étape 7.**</span><span class="sxs-lookup"><span data-stu-id="73b25-127">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="73b25-128">Créez un principal de service afin d’obtenir un objet JSON contenant les autres éléments d’information dont vous avez besoin pour vous authentifier avec Azure.</span><span class="sxs-lookup"><span data-stu-id="73b25-128">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="73b25-129">Voici un exemple de sortie :</span><span class="sxs-lookup"><span data-stu-id="73b25-129">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="73b25-130">**Notez les valeurs de client, nom et mot de passe car elles sont utilisées à l’étape 7.**</span><span class="sxs-lookup"><span data-stu-id="73b25-130">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="73b25-131">Définissez les variables d’environnement en remplaçant les espaces réservés &lt;ID d’abonnement>, &lt;client >, &lt;nom >, et &lt;mot de passe par les valeurs obtenues aux étapes 4 et 5.</span><span class="sxs-lookup"><span data-stu-id="73b25-131">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="73b25-132">**Avec Bash**</span><span class="sxs-lookup"><span data-stu-id="73b25-132">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="73b25-133">**Utiliser PowerShell**</span><span class="sxs-lookup"><span data-stu-id="73b25-133">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="73b25-134">Création d’un principal de service à l’aide du kit de développement logiciel Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="73b25-134">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="73b25-135">Pour créer un principal de service par programmation à l’aide de JavaScript, utilisez le [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="73b25-135">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="73b25-136">Utilisation du principal de service</span><span class="sxs-lookup"><span data-stu-id="73b25-136">Using the service principal</span></span>

<span data-ttu-id="73b25-137">Une fois que vous avez un principal de service, l’extrait de code JavaScript suivant montre comment utiliser les clés de principale de service pour l’authentification avec le SDK Azure pour Node.js.</span><span class="sxs-lookup"><span data-stu-id="73b25-137">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="73b25-138">Modifiez les espaces réservés suivants : &lt;ID client ou ID d’app >, &lt;secret ou mot de passe >, et &lt;domaine ou client>,</span><span class="sxs-lookup"><span data-stu-id="73b25-138">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
