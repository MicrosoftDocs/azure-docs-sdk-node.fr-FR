---
title: Modules Azure Commerce pour Node.js
description: "Références pour les modules Azure Commerce pour Node.js"
keywords: Azure, SDK, API, Commerce, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="03d54-104">Modules Azure Commerce pour Node.js</span><span class="sxs-lookup"><span data-stu-id="03d54-104">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="03d54-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="03d54-105">Overview</span></span>

<span data-ttu-id="03d54-106">Utilisez les API Azure Commerce pour extraire les données d’utilisation et de ressources dans vos outils d’analyse de données préférés.</span><span class="sxs-lookup"><span data-stu-id="03d54-106">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="03d54-107">Les API d’utilisation des ressources Azure et RateCard peuvent vous aider à prévoir vos coûts avec précision et à les gérer.</span><span class="sxs-lookup"><span data-stu-id="03d54-107">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="03d54-108">Les API sont implémentées en tant que fournisseur de ressources et font partie intégrante de la famille d’API exposées par Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="03d54-108">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="03d54-109">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="03d54-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="03d54-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="03d54-110">Install the npm module</span></span>

<span data-ttu-id="03d54-111">Installer le module npm Azure Commerce</span><span class="sxs-lookup"><span data-stu-id="03d54-111">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="03d54-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="03d54-112">Example</span></span>

<span data-ttu-id="03d54-113">Cet exemple récupère vos données de consommation Azure estimées pour le mois dernier.</span><span class="sxs-lookup"><span data-stu-id="03d54-113">This example retrieves your estimated Azure consumption data for the last month.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="03d54-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="03d54-114">Samples</span></span>

<span data-ttu-id="03d54-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="03d54-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
