---
title: Modules Azure Service Map pour Node.js
description: "Références pour les modules Azure Service Map pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 3f858e52f7a97ff77959825a1be993ef52f96e57
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="1a095-103">Modules Azure Service Map pour Node.js</span><span class="sxs-lookup"><span data-stu-id="1a095-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="1a095-104">La solution Service Map détecte automatiquement les composants d’application sur les systèmes Windows et Linux, et mappe la communication entre les services.</span><span class="sxs-lookup"><span data-stu-id="1a095-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="1a095-105">Elle affiche les connexions entre serveurs, processus et ports au sein de toute architecture TCP connectée, sans nécessiter de configuration autre que l’installation d’un agent.</span><span class="sxs-lookup"><span data-stu-id="1a095-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="1a095-106">En savoir plus sur [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="1a095-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="1a095-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="1a095-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1a095-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="1a095-108">Install the npm module</span></span>

<span data-ttu-id="1a095-109">Installer le module npm Azure Service Map</span><span class="sxs-lookup"><span data-stu-id="1a095-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="1a095-110">exemples</span><span class="sxs-lookup"><span data-stu-id="1a095-110">Example</span></span>

<span data-ttu-id="1a095-111">Cet exemple répertorie tous les mappages de service pour le groupe de ressources et l’espace de travail spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1a095-111">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="1a095-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="1a095-112">Samples</span></span>

<span data-ttu-id="1a095-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="1a095-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
