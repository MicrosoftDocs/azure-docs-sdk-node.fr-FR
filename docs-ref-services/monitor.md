---
title: Modules Azure Monitor pour Node.js
description: Références pour les modules Azure Monitor pour Node.js
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: fb2cc5ba927fe03fb5fe3114919ed1b0b6e969ae
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51141308"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="a2e52-103">Modules Azure Monitor pour Node.js</span><span class="sxs-lookup"><span data-stu-id="a2e52-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="a2e52-104">Les applications cloud sont complexes, et se composent de nombreux éléments mobiles.</span><span class="sxs-lookup"><span data-stu-id="a2e52-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="a2e52-105">L’analyse fournit des données visant à garantir que votre application reste opérationnelle et soit exécutée en toute intégrité.</span><span class="sxs-lookup"><span data-stu-id="a2e52-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="a2e52-106">Elle vous permet également de parer à des problèmes potentiels ou de résoudre des problèmes déjà survenus.</span><span class="sxs-lookup"><span data-stu-id="a2e52-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="a2e52-107">En outre, vous pouvez utiliser les données d’analyse pour obtenir des informations détaillées sur votre application.</span><span class="sxs-lookup"><span data-stu-id="a2e52-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="a2e52-108">Ces connaissances peuvent vous aider à améliorer les performances de l’application ou sa facilité de gestion, ou à automatiser des actions qui exigeraient normalement une intervention manuelle.</span><span class="sxs-lookup"><span data-stu-id="a2e52-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="a2e52-109">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="a2e52-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="a2e52-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="a2e52-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="a2e52-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="a2e52-111">Example</span></span>

<span data-ttu-id="a2e52-112">Cet exemple de code imprime toutes les règles d’alerte associées à un groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="a2e52-112">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="a2e52-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="a2e52-113">Samples</span></span>

<span data-ttu-id="a2e52-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="a2e52-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
