---
title: Modules Azure Power BI Embedded pour Node.js
description: Références pour les modules Azure Power BI Embedded pour Node.js
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 58251dd1cd3a672a5167193f74d311952d70e84e
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52084863"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="97d45-103">Modules Azure Power BI Embedded pour Node.js</span><span class="sxs-lookup"><span data-stu-id="97d45-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="97d45-104">Avec le service Azure Power BI Embedded, vous pouvez intégrer des rapports Power BI directement dans votre application de nœud pour créer ou modifier des graphiques et des rapports.</span><span class="sxs-lookup"><span data-stu-id="97d45-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="97d45-105">En savoir plus sur [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="97d45-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="97d45-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="97d45-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="97d45-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="97d45-107">Install the npm module</span></span>

<span data-ttu-id="97d45-108">Installer le module npm Azure Power BI</span><span class="sxs-lookup"><span data-stu-id="97d45-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="97d45-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="97d45-109">Example</span></span>

<span data-ttu-id="97d45-110">Cet exemple crée une collection d’espaces de travail dans un groupe de ressources existant.</span><span class="sxs-lookup"><span data-stu-id="97d45-110">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="97d45-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="97d45-111">Samples</span></span>

<span data-ttu-id="97d45-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="97d45-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
