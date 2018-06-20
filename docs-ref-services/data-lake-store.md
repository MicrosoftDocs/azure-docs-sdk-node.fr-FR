---
title: Modules Azure Data Lake Store pour Node.js
description: Références pour les modules Azure Data Lake Store pour Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: a108cc6d184b72d2d4227f9e60da6b7a535f92ae
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
ms.locfileid: "28117124"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="e63e5-103">Modules Azure Data Lake Store pour Node.js</span><span class="sxs-lookup"><span data-stu-id="e63e5-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="e63e5-104">Azure Data Lake Store est un référentiel d'entreprise à très grande échelle pour les charges de travail d'analyse du Big Data.</span><span class="sxs-lookup"><span data-stu-id="e63e5-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="e63e5-105">Azure Data Lake vous permet de capturer les données de toute taille, de tout type et à toute vitesse d'ingestion dans un emplacement unique en vue d'une analyse opérationnelle et exploratoire.</span><span class="sxs-lookup"><span data-stu-id="e63e5-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="e63e5-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="e63e5-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e63e5-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="e63e5-107">Install the npm module</span></span>

<span data-ttu-id="e63e5-108">Utiliser npm pour installer les modules Azure Data Lake Store pour Node.js</span><span class="sxs-lookup"><span data-stu-id="e63e5-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="e63e5-109">exemples</span><span class="sxs-lookup"><span data-stu-id="e63e5-109">Example</span></span>

<span data-ttu-id="e63e5-110">Cet exemple répertorie tous les comptes Data Lake Store d’un abonnement Azure donné</span><span class="sxs-lookup"><span data-stu-id="e63e5-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="e63e5-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="e63e5-111">Samples</span></span>

<span data-ttu-id="e63e5-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="e63e5-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
