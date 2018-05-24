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
---
# <a name="azure-sql-modules-for-nodejs"></a>Modules Azure SQL pour Node.js

Utilisez des données stockées dans une [base de données SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) à partir de Node.js.
La bibliothèque de gestion fournit une interface pour rendre les bases de données SQL Microsoft Azure plus faciles à gérer.

## <a name="client-package"></a>Package client

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm client de SQL Server

```bash
npm install tedious
```

### <a name="example"></a>Exemples

Cet exemple se connecte à une base de données SQL Server et effectue une requête simple.

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

## <a name="management-package"></a>Gestion des packages

### <a name="install-npm-modules"></a>Installer les modules npm

Installer le module npm de gestion de serveur SQL Azure

```
npm install azure-arm-sql
```   

### <a name="example"></a>Exemples

S’authentifier, créer un client et répertorier tous les serveurs.

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

## <a name="samples"></a>Exemples

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
