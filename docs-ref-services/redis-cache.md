---
title: Modules Cache Redis Azure pour Node.js
description: "Références pour les modules Cache Redis Azure pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 5d3a410fefcf6840181701763346fbfe08fe023b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="b78b6-103">Modules Cache Redis Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b78b6-103">Azure Redis Cache modules for Node.js</span></span>

<span data-ttu-id="b78b6-104">Le Cache Redis Azure se base sur le projet Redis open source connu.</span><span class="sxs-lookup"><span data-stu-id="b78b6-104">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="b78b6-105">Il vous permet d’accéder à une instance Redis sécurisée et dédiée, gérée par Microsoft et accessible depuis vos applications Azure.</span><span class="sxs-lookup"><span data-stu-id="b78b6-105">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="b78b6-106">Redis est un stockage clé/valeur avancé, dont les clés peuvent contenir des structures de données telles que des chaînes, des hachages, des listes, des groupes et des groupes triés.</span><span class="sxs-lookup"><span data-stu-id="b78b6-106">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="b78b6-107">Redis prend en charge un ensemble d'opérations atomiques pour ces types de données.</span><span class="sxs-lookup"><span data-stu-id="b78b6-107">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="b78b6-108">En savoir plus sur le [Cache Redis Azure](https://docs.microsoft.com/azure/redis-cache/).</span><span class="sxs-lookup"><span data-stu-id="b78b6-108">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="b78b6-109">Package client</span><span class="sxs-lookup"><span data-stu-id="b78b6-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b78b6-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="b78b6-110">Install the npm module</span></span>

<span data-ttu-id="b78b6-111">Utiliser npm pour installer le module Redis pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b78b6-111">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="b78b6-112">exemples</span><span class="sxs-lookup"><span data-stu-id="b78b6-112">Example</span></span>

<span data-ttu-id="b78b6-113">Cet exemple se connecte à une instance de Cache Redis Azure, stocke une paire clé/valeur et puis lit la valeur stockée par sa clé.</span><span class="sxs-lookup"><span data-stu-id="b78b6-113">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="b78b6-114">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="b78b6-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b78b6-115">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="b78b6-115">Install the npm module</span></span>

<span data-ttu-id="b78b6-116">Utiliser npm pour installer les modules Cache Redus Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b78b6-116">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="b78b6-117">exemples</span><span class="sxs-lookup"><span data-stu-id="b78b6-117">Example</span></span>

<span data-ttu-id="b78b6-118">Cet exemple s’authentifie auprès d’Azure et répertorie toutes les instances de Cache Redis dans un groupe de ressources spécifié.</span><span class="sxs-lookup"><span data-stu-id="b78b6-118">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

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


## <a name="samples"></a><span data-ttu-id="b78b6-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="b78b6-119">Samples</span></span>

* [<span data-ttu-id="b78b6-120">Utilisation du Cache Redis Azure avec Node.js</span><span class="sxs-lookup"><span data-stu-id="b78b6-120">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="b78b6-121">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="b78b6-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
