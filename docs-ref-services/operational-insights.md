---
title: Modules Azure Operational Insights pour Node.js
description: Références pour les modules Azure Operational Insights pour Node.js
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: c8a137c4759982e0551d9048ac271780e6a68afe
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51497503"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="b4414-103">Modules Azure Operational Insights pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b4414-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="b4414-104">Utiliser npm pour installer le module Azure Operational Insights pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b4414-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="b4414-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="b4414-105">Example</span></span> 

<span data-ttu-id="b4414-106">Cet exemple crée un client, le connecte à Operational Insights et récupère une liste d’espaces de travail par un groupe de ressources spécifié.</span><span class="sxs-lookup"><span data-stu-id="b4414-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b4414-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="b4414-107">Samples</span></span>

<span data-ttu-id="b4414-108">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="b4414-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
