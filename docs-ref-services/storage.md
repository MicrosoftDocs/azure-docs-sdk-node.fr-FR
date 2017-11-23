---
title: Modules de Stockage Azure pour Node.js
description: "Références pour les modules de Stockage Azure pour Node.js"
keywords: "Azure, nœud, SDK, API, stockage, Node.js, Javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="2acf7-104">Modules de Stockage Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="2acf7-104">Azure Storage modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2acf7-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="2acf7-105">Overview</span></span>

<span data-ttu-id="2acf7-106">Utilisez le module client de stockage Azure pour :</span><span class="sxs-lookup"><span data-stu-id="2acf7-106">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="2acf7-107">Lire et écrire des objets et des fichiers à partir du [Stockage Blob Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span><span class="sxs-lookup"><span data-stu-id="2acf7-107">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="2acf7-108">Envoyer et recevoir des messages entre des applications connectées par le cloud avec le [stockage de files d’attente Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span><span class="sxs-lookup"><span data-stu-id="2acf7-108">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="2acf7-109">Lire et écrire des données structurées volumineuses avec le [stockage de tables Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span><span class="sxs-lookup"><span data-stu-id="2acf7-109">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="2acf7-110">Créer, mettre à jour et gérer les requêtes et les comptes de stockage Azure et régénérer les clés d’accès à partir de vos applications Node.js avec les modules de gestion.</span><span class="sxs-lookup"><span data-stu-id="2acf7-110">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="2acf7-111">Package client</span><span class="sxs-lookup"><span data-stu-id="2acf7-111">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2acf7-112">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="2acf7-112">Install the npm module</span></span>

<span data-ttu-id="2acf7-113">Installer le module npm de client de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="2acf7-113">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="2acf7-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="2acf7-114">Example</span></span>

<span data-ttu-id="2acf7-115">Cet exemple crée un conteneur de stockage et télécharge un fichier local `data.txt` vers celui-ci.</span><span class="sxs-lookup"><span data-stu-id="2acf7-115">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="2acf7-116">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="2acf7-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2acf7-117">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="2acf7-117">Install the npm module</span></span> 

<span data-ttu-id="2acf7-118">Installer le module npm de gestion de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="2acf7-118">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="2acf7-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="2acf7-119">Example</span></span>

<span data-ttu-id="2acf7-120">Cet exemple répertorie les comptes de stockage.</span><span class="sxs-lookup"><span data-stu-id="2acf7-120">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2acf7-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="2acf7-121">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="2acf7-122">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="2acf7-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
