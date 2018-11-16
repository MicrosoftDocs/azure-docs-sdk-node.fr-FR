---
title: Modules Recherche Azure pour Node.js
description: Références pour les modules Recherche Azure pour Node.js
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: a9c34a57d7964de1713ebf4d6c0f9c000df33042
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51366543"
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="4e490-103">Modules Recherche Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="4e490-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="4e490-104">Le service Recherche Azure est une solution cloud de recherche sous forme de service qui délègue la gestion du serveur et de l’infrastructure à Microsoft pour vous laisser un service prêt à l’emploi que vous renseignez avec vos données pour ensuite ajouter une recherche à votre application.</span><span class="sxs-lookup"><span data-stu-id="4e490-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="4e490-105">En savoir plus sur [Recherche Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="4e490-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="4e490-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="4e490-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4e490-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="4e490-107">Install the npm module</span></span>

<span data-ttu-id="4e490-108">Installer le module npm Recherche Azure</span><span class="sxs-lookup"><span data-stu-id="4e490-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="4e490-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="4e490-109">Example</span></span>

<span data-ttu-id="4e490-110">Cet exemple crée un nouveau service de recherche dans Azure, et dresse la liste des ressources dans son groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="4e490-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="4e490-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="4e490-111">Samples</span></span>

<span data-ttu-id="4e490-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="4e490-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
