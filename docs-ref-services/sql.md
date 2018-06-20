---
title: Modules Azure SQL pour Node.js
description: Références pour les modules Azure SQL pour Node.js
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 095a54a0919b237891ea89f4c826be0fc3060bbe
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259444"
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="0cba9-103">Modules Azure SQL pour Node.js</span><span class="sxs-lookup"><span data-stu-id="0cba9-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="0cba9-104">Utilisez des données stockées dans une [base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) à partir de Node.js.</span><span class="sxs-lookup"><span data-stu-id="0cba9-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="0cba9-105">La bibliothèque de gestion fournit une interface pour rendre les bases de données SQL Microsoft Azure plus faciles à gérer.</span><span class="sxs-lookup"><span data-stu-id="0cba9-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="0cba9-106">Package client</span><span class="sxs-lookup"><span data-stu-id="0cba9-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0cba9-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="0cba9-107">Install the npm module</span></span>

<span data-ttu-id="0cba9-108">Installer le module npm client de SQL Server</span><span class="sxs-lookup"><span data-stu-id="0cba9-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="0cba9-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="0cba9-109">Example</span></span>

<span data-ttu-id="0cba9-110">Cet exemple se connecte à une base de données SQL Server et effectue une requête simple.</span><span class="sxs-lookup"><span data-stu-id="0cba9-110">This example connects to a SQL Server database and perform a simple query.</span></span>

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a><span data-ttu-id="0cba9-111">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="0cba9-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="0cba9-112">Installer les modules npm</span><span class="sxs-lookup"><span data-stu-id="0cba9-112">Install npm modules</span></span>

<span data-ttu-id="0cba9-113">Installer le module npm de gestion de serveur SQL Azure</span><span class="sxs-lookup"><span data-stu-id="0cba9-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="0cba9-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="0cba9-114">Example</span></span>

<span data-ttu-id="0cba9-115">S’authentifier, créer un client et répertorier tous les serveurs.</span><span class="sxs-lookup"><span data-stu-id="0cba9-115">Authenticate, create a client, and list all servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="0cba9-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="0cba9-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="0cba9-117">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="0cba9-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
