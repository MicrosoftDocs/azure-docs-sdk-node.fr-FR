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
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>Kit de développement logiciel (SDK) Microsoft Azure pour Node.js - ContainerServiceClient
Ce projet fournit un package Node.js permettant d’accéder à Azure. Pour le moment, il prend en charge :
- **Node.js version 6.x.x ou ultérieure**

## <a name="features"></a>Caractéristiques


## <a name="how-to-install"></a>Procédure d’installation

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>Utilisation

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>Authentification, création du client et liste containerServices à titre d’exemple.

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

## <a name="related-projects"></a>Projets associés

- [Kit de développement logiciel (SDK) Microsoft Azure pour Node.js](https://github.com/Azure/azure-sdk-for-node)