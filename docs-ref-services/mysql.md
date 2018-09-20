---
title: Modules Azure MySQL pour Node.js
description: Références pour les modules Azure MySQL pour Node.js
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: f830f2f37429b32bbcfa856ad82a817ae2658341
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46247223"
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="2f828-103">Modules Azure MySQL pour Node.js</span><span class="sxs-lookup"><span data-stu-id="2f828-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="2f828-104">La bibliothèque client recommandée pour l’accès à des bases de données Azure pour MySQL est la [bibliothèque de connexions open source Node.js pour les bases de données Azure pour MySQL](https://github.com/sidorares/node-mysql2).</span><span class="sxs-lookup"><span data-stu-id="2f828-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="2f828-105">En savoir plus sur les [bases de données Azure pour MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="2f828-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="2f828-106">Package client</span><span class="sxs-lookup"><span data-stu-id="2f828-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2f828-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="2f828-107">Install the npm module</span></span>

<span data-ttu-id="2f828-108">Utilisez npm pour installer le module client MySQL.</span><span class="sxs-lookup"><span data-stu-id="2f828-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="2f828-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="2f828-109">Example</span></span>

<span data-ttu-id="2f828-110">Cet exemple se connecte à une base de données MySQL et exécute une requête simple pour récupérer tous les clients.</span><span class="sxs-lookup"><span data-stu-id="2f828-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2f828-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="2f828-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="2f828-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="2f828-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
