---
title: Modules Facturation Azure pour Node.js
description: "Références pour les modules Facturation Azure pour Node.js"
keywords: Azure, SDK, API, Facturation, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="dd10b-104">Modules Facturation Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="dd10b-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dd10b-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="dd10b-105">Overview</span></span>
<span data-ttu-id="dd10b-106">Les API Facturation Azure offrent un accès à vos factures Azure et leurs détails.</span><span class="sxs-lookup"><span data-stu-id="dd10b-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="dd10b-107">Pour utiliser cette API, l’administrateur du compte doit s’abonner depuis le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="dd10b-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="dd10b-108">Consultez [Gérer l’accès à la facturation Azure à l’aide de rôles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="dd10b-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="dd10b-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="dd10b-109">Install the npm module</span></span> 

<span data-ttu-id="dd10b-110">Installer le module npm de Facturation Azure</span><span class="sxs-lookup"><span data-stu-id="dd10b-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="dd10b-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd10b-111">Example</span></span> 
 
<span data-ttu-id="dd10b-112">Cet exemple imprime une liste de toutes vos précédentes factures.</span><span class="sxs-lookup"><span data-stu-id="dd10b-112">This example prints a list of all of your past invoices.</span></span>
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a><span data-ttu-id="dd10b-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="dd10b-113">Samples</span></span>

<span data-ttu-id="dd10b-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="dd10b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
