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
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51465693"
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
