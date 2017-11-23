---
title: Modules Azure PostgreSQL pour Node.js
description: "Références pour les modules Azure PostgreSQL pour Node.js"
keywords: "Azure, nœud, SDK, API, Node.js, Javascript, base de données, PostgreSQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="19ddd-104">Modules Azure PostgreSQL pour Node.js</span><span class="sxs-lookup"><span data-stu-id="19ddd-104">Azure PostgreSQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="19ddd-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="19ddd-105">Overview</span></span>

<span data-ttu-id="19ddd-106">La bibliothèque client recommandée pour l’accès à des bases de données Azure pour PostgreSQL est la [bibliothèque de connexions open source Node.js pour les bases de données Azure pour PostgreSQL](https://www.npmjs.com/package/pg).</span><span class="sxs-lookup"><span data-stu-id="19ddd-106">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="19ddd-107">Cette bibliothèque est un client PostgreSQL non-bloquant pour Node.js, prenant en charge du JavaScript pur et des liaisons libpq natives optionnelles.</span><span class="sxs-lookup"><span data-stu-id="19ddd-107">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="19ddd-108">En savoir plus sur les [bases de données Azure pour PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="19ddd-108">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="19ddd-109">Package client</span><span class="sxs-lookup"><span data-stu-id="19ddd-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="19ddd-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="19ddd-110">Install the npm module</span></span>

<span data-ttu-id="19ddd-111">Utilisez npm pour installer le module client PostgreSQL.</span><span class="sxs-lookup"><span data-stu-id="19ddd-111">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="19ddd-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="19ddd-112">Example</span></span>

<span data-ttu-id="19ddd-113">Cet exemple ouvre une connexion client et exécute une requête simple.</span><span class="sxs-lookup"><span data-stu-id="19ddd-113">This example opens a client connection and executes a simple query.</span></span>

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a><span data-ttu-id="19ddd-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="19ddd-114">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="19ddd-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="19ddd-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
