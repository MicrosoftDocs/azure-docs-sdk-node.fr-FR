---
title: Modules Azure Operational Insights pour Node.js
description: "Références pour les modules Azure Operational Insights pour Node.js"
keywords: Azure, SDK, API, Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="34913-104">Modules Azure Operational Insights pour Node.js</span><span class="sxs-lookup"><span data-stu-id="34913-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="34913-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="34913-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="34913-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="34913-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="34913-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="34913-107">Install the npm module</span></span>

<span data-ttu-id="34913-108">Utiliser npm pour installer le module Azure Operational Insights pour Node.js</span><span class="sxs-lookup"><span data-stu-id="34913-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="34913-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="34913-109">Example</span></span> 

<span data-ttu-id="34913-110">Cet exemple crée un client, le connecte à Operational Insights et récupère une liste d’espaces de travail par un groupe de ressources spécifié.</span><span class="sxs-lookup"><span data-stu-id="34913-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="34913-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="34913-111">Samples</span></span>

<span data-ttu-id="34913-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="34913-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
