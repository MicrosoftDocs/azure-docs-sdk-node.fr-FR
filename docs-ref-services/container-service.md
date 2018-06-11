---
title: Modules Azure Container Service pour Node.js
description: Références pour les modules Azure Container Service pour Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689825"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a><span data-ttu-id="3d447-103">Kit de développement logiciel (SDK) Microsoft Azure pour Node.js - ContainerServiceClient</span><span class="sxs-lookup"><span data-stu-id="3d447-103">Microsoft Azure SDK for Node.js - ContainerServiceClient</span></span>
<span data-ttu-id="3d447-104">Ce projet fournit un package Node.js permettant d’accéder à Azure.</span><span class="sxs-lookup"><span data-stu-id="3d447-104">This project provides a Node.js package for accessing Azure.</span></span> <span data-ttu-id="3d447-105">Pour le moment, il prend en charge :</span><span class="sxs-lookup"><span data-stu-id="3d447-105">Right now it supports:</span></span>
- <span data-ttu-id="3d447-106">**Node.js version 6.x.x ou ultérieure**</span><span class="sxs-lookup"><span data-stu-id="3d447-106">**Node.js version 6.x.x or higher**</span></span>

## <a name="features"></a><span data-ttu-id="3d447-107">Caractéristiques</span><span class="sxs-lookup"><span data-stu-id="3d447-107">Features</span></span>


## <a name="how-to-install"></a><span data-ttu-id="3d447-108">Procédure d’installation</span><span class="sxs-lookup"><span data-stu-id="3d447-108">How to Install</span></span>

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a><span data-ttu-id="3d447-109">Utilisation</span><span class="sxs-lookup"><span data-stu-id="3d447-109">How to use</span></span>

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a><span data-ttu-id="3d447-110">Authentification, création du client et liste containerServices à titre d’exemple.</span><span class="sxs-lookup"><span data-stu-id="3d447-110">Authentication, client creation and list containerServices as an example.</span></span>

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a><span data-ttu-id="3d447-111">Projets associés</span><span class="sxs-lookup"><span data-stu-id="3d447-111">Related projects</span></span>

- [<span data-ttu-id="3d447-112">Kit de développement logiciel (SDK) Microsoft Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="3d447-112">Microsoft Azure SDK for Node.js</span></span>](https://github.com/Azure/azure-sdk-for-node)