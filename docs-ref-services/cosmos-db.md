---
title: Modules Azure Cosmos DB pour Node.js
description: Références pour les modules Azure Cosmos DB pour Node.js
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 2e2813bb3b213de4066b2a3bc971586667a83f68
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51439433"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="88084-103">Modules Azure Cosmos DB pour Node.js</span><span class="sxs-lookup"><span data-stu-id="88084-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="88084-104">Azure Cosmos DB est un service de base de données multimodèle mondialement distribué de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="88084-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="88084-105">Azure Cosmos DB vous permet de faire évoluer en toute flexibilité et de façon indépendante le débit et le stockage sur n’importe quel nombre de régions géographiques Azure.</span><span class="sxs-lookup"><span data-stu-id="88084-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="88084-106">Il offre des garanties en termes de débit, de latence, de disponibilité et de cohérence avec des contrats SLA complets, ce qu’aucun autre service de base de données ne peut offrir.</span><span class="sxs-lookup"><span data-stu-id="88084-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="88084-107">Azure Cosmos DB contient un moteur de base de données non basé sur un schéma, régi par les ressources et optimisé pour les écritures. Celui-ci prend en charge plusieurs modèles de données : clé-valeur, documents, graphiques et colonnes.</span><span class="sxs-lookup"><span data-stu-id="88084-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="88084-108">Il prend également en charge de nombreuses API permettant d’accéder aux données, notamment MongoDB, SQL, Gremlin/Graph, Tables Azure et Cassandra (préversion) d’une manière extensible.</span><span class="sxs-lookup"><span data-stu-id="88084-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="88084-109">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="88084-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="88084-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="88084-110">Install the npm module</span></span> 

<span data-ttu-id="88084-111">Installer le module npm Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="88084-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="88084-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="88084-112">Example</span></span>

<span data-ttu-id="88084-113">Cet exemple répertorie tous les comptes Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="88084-113">This example lists all Azure Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="88084-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="88084-114">Samples</span></span>

* [<span data-ttu-id="88084-115">Développement d’une application Node.js en utilisant Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="88084-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="88084-116">Développement d’une application Node.js en utilisant Azure Cosmos DB - Gremlin</span><span class="sxs-lookup"><span data-stu-id="88084-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="88084-117">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="88084-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
