---
title: Modules Azure Service Map pour Node.js
description: Références pour les modules Azure Service Map pour Node.js
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 494d948896d65dd67b06f455386f500346862beb
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52067074"
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="8aa30-103">Modules Azure Service Map pour Node.js</span><span class="sxs-lookup"><span data-stu-id="8aa30-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="8aa30-104">La solution Service Map détecte automatiquement les composants d’application sur les systèmes Windows et Linux, et mappe la communication entre les services.</span><span class="sxs-lookup"><span data-stu-id="8aa30-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="8aa30-105">Elle affiche les connexions entre serveurs, processus et ports au sein de toute architecture TCP connectée, sans nécessiter de configuration autre que l’installation d’un agent.</span><span class="sxs-lookup"><span data-stu-id="8aa30-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="8aa30-106">En savoir plus sur [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="8aa30-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="8aa30-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="8aa30-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8aa30-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="8aa30-108">Install the npm module</span></span>

<span data-ttu-id="8aa30-109">Installer le module npm Azure Service Map</span><span class="sxs-lookup"><span data-stu-id="8aa30-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="8aa30-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="8aa30-110">Example</span></span>

<span data-ttu-id="8aa30-111">Cet exemple répertorie tous les mappages de service pour le groupe de ressources et l’espace de travail spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8aa30-111">This example lists all service maps for the specified resource group and workspace.</span></span>

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

## <a name="samples"></a><span data-ttu-id="8aa30-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="8aa30-112">Samples</span></span>

<span data-ttu-id="8aa30-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="8aa30-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
