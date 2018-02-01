---
title: Modules de Stockage Azure pour Node.js
description: "Références pour les modules de Stockage Azure pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-storage-modules-for-nodejs"></a>Modules de Stockage Azure pour Node.js

Utilisez le module client de stockage Azure pour :

- Lire et écrire des objets et des fichiers à partir du [Stockage Blob Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)
- Envoyer et recevoir des messages entre des applications connectées par le cloud avec le [stockage de files d’attente Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)
- Lire et écrire des données structurées volumineuses avec le [stockage de tables Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)

Créer, mettre à jour et gérer les requêtes et les comptes de stockage Azure et régénérer les clés d’accès à partir de vos applications Node.js avec les modules de gestion.

## <a name="client-package"></a>Package client

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm de client de stockage Azure

```bash
npm install azure-storage
```

### <a name="example"></a>exemples

Cet exemple crée un conteneur de stockage et télécharge un fichier local `data.txt` vers celui-ci.

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm 

Installer le module npm de gestion de stockage Azure

```bash
npm install azure-arm-storage
```

### <a name="example"></a>exemples

Cet exemple répertorie les comptes de stockage.

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemples

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
