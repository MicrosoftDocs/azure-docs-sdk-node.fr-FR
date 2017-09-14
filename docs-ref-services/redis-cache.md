---
title: Modules Cache Redis Azure pour Node.js
description: "Références pour les modules Cache Redis Azure pour Node.js"
keywords: Azure, SDK, API, Cache Redis, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 8a10e522e39461697b740750b63fc82a6cc320ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="70b87-104">Modules Cache Redis Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="70b87-104">Azure Redis Cache modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="70b87-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="70b87-105">Overview</span></span>

<span data-ttu-id="70b87-106">Le Cache Redis Azure se base sur le projet Redis open source connu.</span><span class="sxs-lookup"><span data-stu-id="70b87-106">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="70b87-107">Il vous permet d’accéder à une instance Redis sécurisée et dédiée, gérée par Microsoft et accessible depuis vos applications Azure.</span><span class="sxs-lookup"><span data-stu-id="70b87-107">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="70b87-108">Redis est un stockage clé/valeur avancé, dont les clés peuvent contenir des structures de données telles que des chaînes, des hachages, des listes, des groupes et des groupes triés.</span><span class="sxs-lookup"><span data-stu-id="70b87-108">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="70b87-109">Redis prend en charge un ensemble d'opérations atomiques pour ces types de données.</span><span class="sxs-lookup"><span data-stu-id="70b87-109">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="70b87-110">En savoir plus sur le [Cache Redis Azure](https://docs.microsoft.com/azure/redis-cache/).</span><span class="sxs-lookup"><span data-stu-id="70b87-110">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="70b87-111">Package client</span><span class="sxs-lookup"><span data-stu-id="70b87-111">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="70b87-112">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="70b87-112">Install the npm module</span></span>

<span data-ttu-id="70b87-113">Utiliser npm pour installer le module Redis pour Node.js</span><span class="sxs-lookup"><span data-stu-id="70b87-113">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="70b87-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="70b87-114">Example</span></span>

<span data-ttu-id="70b87-115">Cet exemple se connecte à une instance de Cache Redis Azure, stocke une paire clé/valeur et puis lit la valeur stockée par sa clé.</span><span class="sxs-lookup"><span data-stu-id="70b87-115">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a><span data-ttu-id="70b87-116">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="70b87-116">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="70b87-117">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="70b87-117">Install the npm module</span></span>

<span data-ttu-id="70b87-118">Utiliser npm pour installer les modules Cache Redus Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="70b87-118">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="70b87-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="70b87-119">Example</span></span>

<span data-ttu-id="70b87-120">Cet exemple s’authentifie auprès d’Azure et répertorie toutes les instances de Cache Redis dans un groupe de ressources spécifié.</span><span class="sxs-lookup"><span data-stu-id="70b87-120">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a><span data-ttu-id="70b87-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="70b87-121">Samples</span></span>

* [<span data-ttu-id="70b87-122">Utilisation du Cache Redis Azure avec Node.js</span><span class="sxs-lookup"><span data-stu-id="70b87-122">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="70b87-123">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="70b87-123">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
