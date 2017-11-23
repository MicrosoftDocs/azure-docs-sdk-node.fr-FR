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
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="94724-104">Modules Azure MySQL pour Node.js</span><span class="sxs-lookup"><span data-stu-id="94724-104">Azure MySQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="94724-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="94724-105">Overview</span></span>

<span data-ttu-id="94724-106">La bibliothèque client recommandée pour l’accès à des bases de données Azure pour MySQL est la [bibliothèque de connexions open source Node.js pour les bases de données Azure pour MySQL](https://github.com/sidorares/node-mysql2).</span><span class="sxs-lookup"><span data-stu-id="94724-106">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="94724-107">En savoir plus sur les [bases de données Azure pour MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="94724-107">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="94724-108">Package client</span><span class="sxs-lookup"><span data-stu-id="94724-108">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="94724-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="94724-109">Install the npm module</span></span>

<span data-ttu-id="94724-110">Utilisez npm pour installer le module client MySQL.</span><span class="sxs-lookup"><span data-stu-id="94724-110">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="94724-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="94724-111">Example</span></span>

<span data-ttu-id="94724-112">Cet exemple se connecte à une base de données MySQL et exécute une requête simple pour récupérer tous les clients.</span><span class="sxs-lookup"><span data-stu-id="94724-112">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="94724-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="94724-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="94724-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="94724-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
