---
title: Modules Azure MySQL pour Node.js
description: "Références pour les modules Azure MySQL pour Node.js"
keywords: "Azure, nœud, SDK, API, Node.js, Javascript, base de données, MySQL"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a>Modules Azure MySQL pour Node.js

## <a name="overview"></a>Vue d'ensemble

La bibliothèque client recommandée pour l’accès à des bases de données Azure pour MySQL est la [bibliothèque de connexions open source Node.js pour les bases de données Azure pour MySQL](https://github.com/sidorares/node-mysql2). 

En savoir plus sur les [bases de données Azure pour MySQL](https://docs.microsoft.com/azure/MySQL/)

## <a name="client-package"></a>Package client

### <a name="install-the-npm-module"></a>Installer le module npm

Utilisez npm pour installer le module client MySQL.

```bash
npm install mysql2
```   

### <a name="example"></a>Exemple

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
