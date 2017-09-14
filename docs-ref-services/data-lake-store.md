---
title: Modules Azure Data Lake Store pour Node.js
description: "Références pour les modules Azure Data Lake Store pour Node.js"
keywords: Azure, SDK, API, Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="0fbb5-104">Modules Azure Data Lake Store pour Node.js</span><span class="sxs-lookup"><span data-stu-id="0fbb5-104">Azure Data Lake Store modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0fbb5-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0fbb5-105">Overview</span></span>
<span data-ttu-id="0fbb5-106">Azure Data Lake Store est un référentiel d'entreprise à très grande échelle pour les charges de travail d'analyse du Big Data.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="0fbb5-107">Azure Data Lake vous permet de capturer les données de toute taille, de tout type et à toute vitesse d'ingestion dans un emplacement unique en vue d'une analyse opérationnelle et exploratoire.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="0fbb5-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="0fbb5-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0fbb5-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="0fbb5-109">Install the npm module</span></span>

<span data-ttu-id="0fbb5-110">Utiliser npm pour installer les modules Azure Data Lake Store pour Node.js</span><span class="sxs-lookup"><span data-stu-id="0fbb5-110">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="0fbb5-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="0fbb5-111">Example</span></span>

<span data-ttu-id="0fbb5-112">Cet exemple répertorie tous les comptes Data Lake Store d’un abonnement Azure donné</span><span class="sxs-lookup"><span data-stu-id="0fbb5-112">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="0fbb5-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="0fbb5-113">Samples</span></span>

<span data-ttu-id="0fbb5-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="0fbb5-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
