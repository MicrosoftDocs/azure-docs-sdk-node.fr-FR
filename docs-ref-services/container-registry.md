---
title: Modules Azure Container Registry pour Node.js
description: "Références pour les modules Azure Container Registry pour Node.js"
keywords: Azure, SDK, API, Container Registry, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Modules Azure Container Registry pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure Container Registry est un service de registre Docker géré basé sur le Registre open source Docker 2.0. Créez et gérez des registres de conteneur Azure pour stocker et gérer vos images de conteneur Docker privées. Utilisez des registres de conteneur dans Azure avec vos pipelines de développement et de déploiement existants, et exploitez l’expertise de la communauté de Docker.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Container Registry

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>Exemple

Cet exemple obtient une liste des conteneurs disponibles.

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
