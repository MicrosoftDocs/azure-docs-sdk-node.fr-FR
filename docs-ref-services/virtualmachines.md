---
title: Modules Machines virtuelles Azure pour Node.js
description: "Références pour les modules Machines virtuelles Azure pour Node.js"
keywords: "Azure, nœud, SDK, API, machine virtuelle, mv, Node.js, Javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>Modules Machines virtuelles Azure pour Node.js

## <a name="overview"></a>Vue d'ensemble

Définir, configurer et déployer de nouvelles machines virtuelles Windows et Linux ainsi que des groupe de machines virtuelles identiques à partir de votre code avec les modules de gestion Azure pour Node.js. Les modules vous permettent de démarrer et d’arrêter des machines virtuelles existantes, d’attacher ou de détacher les disques des machines virtuelles arrêtées dans votre abonnement Azure.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Compute

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>Exemple

L’exemple suivant illustre comment se connecter à Azure, créer un client de gestion et dresser la liste de toutes les images de machine virtuelle pour un emplacement, un éditeur, une offre et une référence SKU spécifiés.

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>Exemples

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
