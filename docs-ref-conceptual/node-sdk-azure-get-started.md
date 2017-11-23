---
title: Prise en main des modules Azure pour Node.js
description: Prise en main des fonctions de base des modules Azure pour Node.js avec votre propre abonnement Azure.
keywords: "Azure, nœud, SDK, API, prise en main, node.js"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: ec83d58585014cca05885af4de55473637c410e8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="840cc-104">Prise en main des modules Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="840cc-104">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="840cc-105">Ce guide vous familiarise avec l’installation des modules Azure pour Node.js, l’authentification auprès d’Azure avec un principal de service, et l’exécution d’un exemple de code qui crée des ressources dans votre abonnement Azure et se connecte à des services cloud Azure.</span><span class="sxs-lookup"><span data-stu-id="840cc-105">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="840cc-106">Composants requis</span><span class="sxs-lookup"><span data-stu-id="840cc-106">Prerequisites</span></span>

- <span data-ttu-id="840cc-107">Un compte Azure.</span><span class="sxs-lookup"><span data-stu-id="840cc-107">An Azure account.</span></span> <span data-ttu-id="840cc-108">Si vous n’en avez pas, inscrivez-vous pour un [essai gratuit](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="840cc-108">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="840cc-109">Node.JS</span><span class="sxs-lookup"><span data-stu-id="840cc-109">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="840cc-110">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) ou [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="840cc-110">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="840cc-111">Préparation de votre environnement</span><span class="sxs-lookup"><span data-stu-id="840cc-111">Prepare your environment</span></span>

<span data-ttu-id="840cc-112">Créez un nouveau projet dans un répertoire vide et installez les modules npm suivants :</span><span class="sxs-lookup"><span data-stu-id="840cc-112">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="840cc-113">Configurer l’authentification</span><span class="sxs-lookup"><span data-stu-id="840cc-113">Set up authentication</span></span>

<span data-ttu-id="840cc-114">Vos applications Node.js doivent lire et créer des autorisations dans votre abonnement Azure pour exécuter l’exemple de code de ce guide.</span><span class="sxs-lookup"><span data-stu-id="840cc-114">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="840cc-115">Créez un principal de service et configurez votre application pour qu’elle s’exécute avec ses informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="840cc-115">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="840cc-116">Les principaux de service constituent un compte non interactif associé à votre identité, auquel vous accordez seulement les privilèges que votre application doit exécuter.</span><span class="sxs-lookup"><span data-stu-id="840cc-116">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="840cc-117">[Créez un principal de service à l’aide d’Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) et capturez la sortie.</span><span class="sxs-lookup"><span data-stu-id="840cc-117">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="840cc-118">Vous devez fournir un [mot de passe sécurisé](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) dans l’argument du mot de passe à la place de `MY_SECURE_PASSWORD`.</span><span class="sxs-lookup"><span data-stu-id="840cc-118">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

<span data-ttu-id="840cc-119">Exportez les valeurs pour *ID d’app*, le *mot de passe* et le *client* en tant que variables d’environnement :</span><span class="sxs-lookup"><span data-stu-id="840cc-119">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="840cc-120">Obtenir l’ID pour votre abonnement en entrant [az account show](https://docs.microsoft.com/cli/azure/account#show)</span><span class="sxs-lookup"><span data-stu-id="840cc-120">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

<span data-ttu-id="840cc-121">Exporter l’ID d’abonnement sous la forme d’une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="840cc-121">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="840cc-122">Créer une machine virtuelle Linux</span><span class="sxs-lookup"><span data-stu-id="840cc-122">Create a Linux virtual machine</span></span>

<span data-ttu-id="840cc-123">Créez un nouveau fichier *createVM.js* dans le répertoire actuel avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="840cc-123">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="840cc-124">Mettez à jour la valeur de `adminPass` avec un bon mot de passe.</span><span class="sxs-lookup"><span data-stu-id="840cc-124">Update the value of `adminPass` with a good password.</span></span>

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
                        primary: true
                    }
                ]
            },
            storageProfile: {
                imageReference: {
                    publisher: 'Canonical',
                    offer: 'UbuntuServer',
                    sku: '16.04-LTS',
                    version: 'latest'
                },
            }
        };

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

<span data-ttu-id="840cc-125">Exécutez le code depuis la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="840cc-125">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="840cc-126">Lorsque le code se termine, obtenez l’adresse IP de votre nouvelle machine virtuelle et connectez-vous avec SSH en utilisant la valeur de `adminPass` à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="840cc-126">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="840cc-127">Écrire un objet blob dans le stockage Azure</span><span class="sxs-lookup"><span data-stu-id="840cc-127">Write a blob to Azure Storage</span></span>

<span data-ttu-id="840cc-128">Créez un nouveau fichier *uploadFile.js* dans le répertoire actuel avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="840cc-128">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

<span data-ttu-id="840cc-129">Exécutez la commande, puis copiez et collez l’URL à partir de la sortie dans votre navigateur web pour afficher le fichier dans le stockage Azure :</span><span class="sxs-lookup"><span data-stu-id="840cc-129">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="840cc-130">Supprimer des ressources</span><span class="sxs-lookup"><span data-stu-id="840cc-130">Clean up resources</span></span>

<span data-ttu-id="840cc-131">Supprimez le groupe de ressources pour supprimer les ressources créées dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="840cc-131">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="840cc-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="840cc-132">Next steps</span></span>

<span data-ttu-id="840cc-133">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="840cc-133">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="840cc-134">Référence</span><span class="sxs-lookup"><span data-stu-id="840cc-134">Reference</span></span> 

<span data-ttu-id="840cc-135">Il existe une [référence](/nodejs/api/overview/azure/?view=azure-node-2.0.0) pour tous les packages.</span><span class="sxs-lookup"><span data-stu-id="840cc-135">A [reference](/nodejs/api/overview/azure/?view=azure-node-2.0.0) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="840cc-136">Obtenir de l’aide et donner son avis</span><span class="sxs-lookup"><span data-stu-id="840cc-136">Get help and give feedback</span></span>

<span data-ttu-id="840cc-137">Posez des questions à la communauté sur [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span><span class="sxs-lookup"><span data-stu-id="840cc-137">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="840cc-138">Signalez des bogues et des problèmes concernant les modules Azure pour Node.js sur le [projet GitHub](https://github.com/Azure/azure-sdk-for-node).</span><span class="sxs-lookup"><span data-stu-id="840cc-138">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

