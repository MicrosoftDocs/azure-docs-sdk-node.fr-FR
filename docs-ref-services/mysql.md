---
title: Modules Azure MySQL pour Node.js
description: "Références pour les modules Azure MySQL pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: c78f61d0f76b6a40ad85ae0e7d9101349666eb0b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-mysql-modules-for-nodejs"></a>Modules Azure MySQL pour Node.js

La bibliothèque client recommandée pour l’accès à des bases de données Azure pour MySQL est la [bibliothèque de connexions open source Node.js pour les bases de données Azure pour MySQL](https://github.com/sidorares/node-mysql2). 

En savoir plus sur les [bases de données Azure pour MySQL](https://docs.microsoft.com/azure/MySQL/)

## <a name="client-package"></a>Package client

### <a name="install-the-npm-module"></a>Installer le module npm

Utilisez npm pour installer le module client MySQL.

```bash
npm install mysql2
```   

### <a name="example"></a>exemples

Cet exemple se connecte à une base de données MySQL et exécute une requête simple pour récupérer tous les clients.

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a>Exemples

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
