---
title: Modules Azure Cosmos DB pour Node.js
description: "Références pour les modules Azure Cosmos DB pour Node.js"
keywords: Azure, SDK, API, Cosmos DB, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 1f545f89b5304b611dbe1ed9cb86052c112f13c1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="29ec2-104">Modules Azure Cosmos DB pour Node.js</span><span class="sxs-lookup"><span data-stu-id="29ec2-104">Azure Cosmos DB Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="29ec2-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="29ec2-105">Overview</span></span>

<span data-ttu-id="29ec2-106">Azure Cosmos DB est un service de base de données multimodèle mondialement distribué de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29ec2-106">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="29ec2-107">Azure Cosmos DB vous permet de faire évoluer en toute flexibilité et de façon indépendante le débit et le stockage sur n’importe quel nombre de régions géographiques Azure.</span><span class="sxs-lookup"><span data-stu-id="29ec2-107">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="29ec2-108">Il offre des garanties en termes de débit, de latence, de disponibilité et de cohérence avec des contrats SLA complets, ce qu’aucun autre service de base de données ne peut offrir.</span><span class="sxs-lookup"><span data-stu-id="29ec2-108">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="29ec2-109">Azure Cosmos DB contient un moteur de base de données non basé sur un schéma, régi par les ressources et optimisé pour les écritures. Celui-ci prend en charge plusieurs modèles de données : clé-valeur, documents, graphiques et colonnes.</span><span class="sxs-lookup"><span data-stu-id="29ec2-109">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="29ec2-110">Il prend également en charge de nombreuses API permettant d’accéder aux données, notamment MongoDB, DocumentDB SQL, Gremlin (préversion) et Tables Azure (préversion), d’une manière extensible.</span><span class="sxs-lookup"><span data-stu-id="29ec2-110">It also supports many APIs for accessing data including MongoDB, DocumentDB SQL, Gremlin (preview), and Azure Tables (preview), in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="29ec2-111">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="29ec2-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="29ec2-112">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="29ec2-112">Install the npm module</span></span> 

<span data-ttu-id="29ec2-113">Installer le module npm Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="29ec2-113">Install the Azure Cosmos DB npm module</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="29ec2-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="29ec2-114">Example</span></span>

<span data-ttu-id="29ec2-115">Cet exemple répertorie tous les comptes Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="29ec2-115">This example lists all Cosmos DB accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a><span data-ttu-id="29ec2-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="29ec2-116">Samples</span></span>

* [<span data-ttu-id="29ec2-117">Développement d’une application Node.js en utilisant Azure Cosmos DB - Document DB</span><span class="sxs-lookup"><span data-stu-id="29ec2-117">Developing a Node.js app using Azure Cosmos DB - DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="29ec2-118">Développement d’une application Node.js en utilisant Azure Cosmos DB - Gremlin</span><span class="sxs-lookup"><span data-stu-id="29ec2-118">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="29ec2-119">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="29ec2-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
