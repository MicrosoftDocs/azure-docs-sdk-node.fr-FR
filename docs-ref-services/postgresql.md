---
title: Modules Azure PostgreSQL pour Node.js
description: Références pour les modules Azure PostgreSQL pour Node.js
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: ed9373b767684e4893ca84de1030d062178b7ea4
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50389715"
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="e92e9-103">Modules Azure PostgreSQL pour Node.js</span><span class="sxs-lookup"><span data-stu-id="e92e9-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="e92e9-104">La bibliothèque client recommandée pour l’accès à des bases de données Azure pour PostgreSQL est la [bibliothèque de connexions open source Node.js pour les bases de données Azure pour PostgreSQL](https://www.npmjs.com/package/pg).</span><span class="sxs-lookup"><span data-stu-id="e92e9-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="e92e9-105">Cette bibliothèque est un client PostgreSQL non-bloquant pour Node.js, prenant en charge du JavaScript pur et des liaisons libpq natives optionnelles.</span><span class="sxs-lookup"><span data-stu-id="e92e9-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="e92e9-106">En savoir plus sur les [bases de données Azure pour PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="e92e9-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="e92e9-107">Package client</span><span class="sxs-lookup"><span data-stu-id="e92e9-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e92e9-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="e92e9-108">Install the npm module</span></span>

<span data-ttu-id="e92e9-109">Utilisez npm pour installer le module client PostgreSQL.</span><span class="sxs-lookup"><span data-stu-id="e92e9-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="e92e9-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="e92e9-110">Example</span></span>

<span data-ttu-id="e92e9-111">Cet exemple ouvre une connexion client et exécute une requête simple.</span><span class="sxs-lookup"><span data-stu-id="e92e9-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e92e9-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="e92e9-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="e92e9-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="e92e9-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
