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
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51394913"
---
# <a name="azure-modules-for-javascript"></a>Modules Azure pour JavaScript

Gérez les ressources Azure et connectez-vous aux services depuis vos applications JavaScript avec les modules Azure pour JavaScript. Le code est disponible en tant que [modules npm](node-sdk-azure-install.md) à utiliser dans vos projets. 

## <a name="manage-azure-resources"></a>Gérer des ressources Azure

Utilisez les modules de gestion pour créer et interroger des ressources à partir de vos applications ou pour créer vos propres outils d’automatisation Azure. 

Par exemple, pour créer une machine virtuelle Linux en utilisant une interface réseau existante, vous devez écrire le code suivant :

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

Vérifiez les [instructions d’installation](node-sdk-azure-install.md) pour obtenir une liste complète des modules et consultez l’[article de prise en main](node-sdk-azure-get-started.md) pour configurer l’authentification et exécutez l’exemple de code pour créer et mettre à jour des ressources dans votre abonnement Azure. 

## <a name="connect-to-azure-services"></a>Se connecter aux services Azure

En plus d’utiliser les modules Azure pour créer et gérer des ressources dans Azure, vous pouvez vous servir de packages pour vous connecter et utiliser les services cloud Azure dans vos applications. Par exemple, vous pouvez mettre à jour une table SQL Database ou charger des fichiers dans le stockage Azure. Sélectionnez le package dont vous avez besoin pour un service particulier à partir de la [liste complète](node-sdk-azure-install.md) et visitez le [centre de développement JavaScript](https://azure.microsoft.com/develop/nodejs/) afin de trouver des didacticiels et des exemples de code pour vous aider à apprendre à utiliser les modules dans vos applications.

Par exemple, pour imprimer le contenu de chaque objet blob dans un conteneur de stockage Azure :

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a>Exemple de code et référence

Les exemples suivants détaillent les tâches courantes avec les modules de gestion Azure et disposent de codes préparés pour vos applications :

- [Machines virtuelles](node-samples-services-compute.md)
- [Applications Web](node-samples-services-web-and-mobile.md)
- [Base de données SQL](node-samples-services-database.md)
   
Une [référence](https://docs.microsoft.com/javascript/api) est disponible pour tous les modules dans les modules de service et de gestion. Les nouvelles fonctionnalités, les dernières modifications et les instructions de migration des versions précédentes sont disponibles dans les [notes de publication](https://github.com/Azure/azure-sdk-for-node/releases).