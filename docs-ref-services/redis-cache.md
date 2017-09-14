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
# <a name="azure-redis-cache-modules-for-nodejs"></a>Modules Cache Redis Azure pour Node.js

## <a name="overview"></a>Vue d'ensemble

Le Cache Redis Azure se base sur le projet Redis open source connu. Il vous permet d’accéder à une instance Redis sécurisée et dédiée, gérée par Microsoft et accessible depuis vos applications Azure.

Redis est un stockage clé/valeur avancé, dont les clés peuvent contenir des structures de données telles que des chaînes, des hachages, des listes, des groupes et des groupes triés. Redis prend en charge un ensemble d'opérations atomiques pour ces types de données.

En savoir plus sur le [Cache Redis Azure](https://docs.microsoft.com/azure/redis-cache/).

## <a name="client-package"></a>Package client

### <a name="install-the-npm-module"></a>Installer le module npm

Utiliser npm pour installer le module Redis pour Node.js

```bash
npm install redis
```

### <a name="example"></a>Exemple

Cet exemple se connecte à une instance de Cache Redis Azure, stocke une paire clé/valeur et puis lit la valeur stockée par sa clé.

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

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Utiliser npm pour installer les modules Cache Redus Azure pour Node.js

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>Exemple

Cet exemple s’authentifie auprès d’Azure et répertorie toutes les instances de Cache Redis dans un groupe de ressources spécifié.

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


## <a name="samples"></a>Exemples

* [Utilisation du Cache Redis Azure avec Node.js](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
