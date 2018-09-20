---
title: Modules Facturation Azure pour Node.js
description: Références pour les modules Facturation Azure pour Node.js
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 20df85ae5e504e460a501737aa07b6692a0da3c7
ms.sourcegitcommit: f830f2f37429b32bbcfa856ad82a817ae2658341
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46213351"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="7980c-103">Modules Facturation Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="7980c-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7980c-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="7980c-104">Overview</span></span>
<span data-ttu-id="7980c-105">Les API Facturation Azure offrent un accès à vos factures Azure et leurs détails.</span><span class="sxs-lookup"><span data-stu-id="7980c-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="7980c-106">Pour utiliser cette API, l’administrateur du compte doit s’abonner depuis le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="7980c-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="7980c-107">Consultez [Gérer l’accès à la facturation Azure à l’aide de rôles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="7980c-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7980c-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="7980c-108">Install the npm module</span></span> 

<span data-ttu-id="7980c-109">Installer le module npm de Facturation Azure</span><span class="sxs-lookup"><span data-stu-id="7980c-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="7980c-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="7980c-110">Example</span></span> 
 
<span data-ttu-id="7980c-111">Cet exemple imprime une liste de toutes vos précédentes factures.</span><span class="sxs-lookup"><span data-stu-id="7980c-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="7980c-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="7980c-112">Samples</span></span>

<span data-ttu-id="7980c-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="7980c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
