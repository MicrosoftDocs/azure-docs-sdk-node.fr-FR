---
title: Modules Azure Monitor pour Node.js
description: "Références pour les modules Azure Monitor pour Node.js"
keywords: Azure, SDK, API, Monitor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="2184a-104">Modules Azure Monitor pour Node.js</span><span class="sxs-lookup"><span data-stu-id="2184a-104">Azure Monitor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2184a-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="2184a-105">Overview</span></span>
<span data-ttu-id="2184a-106">Les applications cloud sont complexes, et se composent de nombreux éléments mobiles.</span><span class="sxs-lookup"><span data-stu-id="2184a-106">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="2184a-107">L’analyse fournit des données visant à garantir que votre application reste opérationnelle et soit exécutée en toute intégrité.</span><span class="sxs-lookup"><span data-stu-id="2184a-107">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="2184a-108">Elle vous permet également de parer à des problèmes potentiels ou de résoudre des problèmes déjà survenus.</span><span class="sxs-lookup"><span data-stu-id="2184a-108">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="2184a-109">En outre, vous pouvez utiliser les données d’analyse pour obtenir des informations détaillées sur votre application.</span><span class="sxs-lookup"><span data-stu-id="2184a-109">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="2184a-110">Ces connaissances peuvent vous aider à améliorer les performances de l’application ou sa facilité de gestion, ou à automatiser des actions qui exigeraient normalement une intervention manuelle.</span><span class="sxs-lookup"><span data-stu-id="2184a-110">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="2184a-111">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="2184a-111">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="2184a-112">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="2184a-112">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="2184a-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="2184a-113">Example</span></span>

<span data-ttu-id="2184a-114">Cet exemple de code imprime toutes les règles d’alerte associées à un groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="2184a-114">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a><span data-ttu-id="2184a-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="2184a-115">Samples</span></span>

<span data-ttu-id="2184a-116">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="2184a-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
