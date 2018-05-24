---
title: Modules Azure PostgreSQL pour Node.js
description: Références pour les modules Azure PostgreSQL pour Node.js
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: 706f636a89e5e89c1dbf760e01c684bcc9588f1f
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Modules Azure PostgreSQL pour Node.js

La bibliothèque client recommandée pour l’accès à des bases de données Azure pour PostgreSQL est la [bibliothèque de connexions open source Node.js pour les bases de données Azure pour PostgreSQL](https://www.npmjs.com/package/pg). Cette bibliothèque est un client PostgreSQL non-bloquant pour Node.js, prenant en charge du JavaScript pur et des liaisons libpq natives optionnelles.

En savoir plus sur les [bases de données Azure pour PostgreSQL](https://docs.microsoft.com/azure/postgresql/)

## <a name="client-package"></a>Package client

### <a name="install-the-npm-module"></a>Installer le module npm

Utilisez npm pour installer le module client PostgreSQL.

```bash
npm install pg
```   

### <a name="example"></a>Exemples

Cet exemple ouvre une connexion client et exécute une requête simple.

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

## <a name="samples"></a>Exemples

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
