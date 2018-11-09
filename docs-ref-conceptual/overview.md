---
title: Modules Azure pour JavaScript
description: Vue d’ensemble des modules de gestion et de service Azure pour JavaScript
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 1d97df65f12c465cf6c790d1e3c016a9ff4aa5ba
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51173088"
---
# <a name="azure-modules-for-javascript"></a><span data-ttu-id="f5210-103">Modules Azure pour JavaScript</span><span class="sxs-lookup"><span data-stu-id="f5210-103">Azure modules for JavaScript</span></span>

<span data-ttu-id="f5210-104">Gérez les ressources Azure et connectez-vous aux services depuis vos applications JavaScript avec les modules Azure pour JavaScript.</span><span class="sxs-lookup"><span data-stu-id="f5210-104">Manage Azure resources and connect to services from your JavaScript applications with the Azure modules for JavaScript.</span></span> <span data-ttu-id="f5210-105">Le code est disponible en tant que [modules npm](node-sdk-azure-install.md) à utiliser dans vos projets.</span><span class="sxs-lookup"><span data-stu-id="f5210-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="f5210-106">Gérer des ressources Azure</span><span class="sxs-lookup"><span data-stu-id="f5210-106">Manage Azure resources</span></span>

<span data-ttu-id="f5210-107">Utilisez les modules de gestion pour créer et interroger des ressources à partir de vos applications ou pour créer vos propres outils d’automatisation Azure.</span><span class="sxs-lookup"><span data-stu-id="f5210-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="f5210-108">Par exemple, pour créer une machine virtuelle Linux en utilisant une interface réseau existante, vous devez écrire le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f5210-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
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
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="f5210-109">Vérifiez les [instructions d’installation](node-sdk-azure-install.md) pour obtenir une liste complète des modules et consultez l’[article de prise en main](node-sdk-azure-get-started.md) pour configurer l’authentification et exécutez l’exemple de code pour créer et mettre à jour des ressources dans votre abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="f5210-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="f5210-110">Se connecter aux services Azure</span><span class="sxs-lookup"><span data-stu-id="f5210-110">Connect to Azure services</span></span>

<span data-ttu-id="f5210-111">En plus d’utiliser les modules Azure pour créer et gérer des ressources dans Azure, vous pouvez vous servir de packages pour vous connecter et utiliser les services cloud Azure dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="f5210-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="f5210-112">Par exemple, vous pouvez mettre à jour une table SQL Database ou charger des fichiers dans le stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="f5210-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="f5210-113">Sélectionnez le package dont vous avez besoin pour un service particulier à partir de la [liste complète](node-sdk-azure-install.md) et visitez le [centre de développement JavaScript](https://azure.microsoft.com/develop/nodejs/) afin de trouver des didacticiels et des exemples de code pour vous aider à apprendre à utiliser les modules dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="f5210-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [JavaScript developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="f5210-114">Par exemple, pour imprimer le contenu de chaque objet blob dans un conteneur de stockage Azure :</span><span class="sxs-lookup"><span data-stu-id="f5210-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="f5210-115">Exemple de code et référence</span><span class="sxs-lookup"><span data-stu-id="f5210-115">Sample code and reference</span></span>

<span data-ttu-id="f5210-116">Les exemples suivants détaillent les tâches courantes avec les modules de gestion Azure et disposent de codes préparés pour vos applications :</span><span class="sxs-lookup"><span data-stu-id="f5210-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="f5210-117">Machines virtuelles</span><span class="sxs-lookup"><span data-stu-id="f5210-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="f5210-118">Applications Web</span><span class="sxs-lookup"><span data-stu-id="f5210-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="f5210-119">Base de données SQL</span><span class="sxs-lookup"><span data-stu-id="f5210-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="f5210-120">Une [référence](https://docs.microsoft.com/javascript/api) est disponible pour tous les modules dans les modules de service et de gestion.</span><span class="sxs-lookup"><span data-stu-id="f5210-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="f5210-121">Les nouvelles fonctionnalités, les dernières modifications et les instructions de migration des versions précédentes sont disponibles dans les [notes de publication](https://github.com/Azure/azure-sdk-for-node/releases).</span><span class="sxs-lookup"><span data-stu-id="f5210-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>