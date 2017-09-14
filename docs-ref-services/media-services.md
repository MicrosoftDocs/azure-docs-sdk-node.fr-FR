---
title: Modules Azure Media Services pour Node.js
description: "Références pour les modules Azure Media Services pour Node.js"
keywords: Azure, SDK, API, Media Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a>Modules Azure Media Services pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure Media Services est une plateforme extensible basée sur le cloud qui permet aux développeurs de créer des applications évolutives de gestion et de diffusion de médias. Media Services est basé sur les API REST qui permettent de télécharger, stocker, encoder et empaqueter en toute sécurité du contenu vidéo ou audio destiné à être diffusé à la demande ou en direct sur différents clients (par exemple, téléviseurs, PC et appareils mobiles).

Avec Azure Media Services, vous pouvez :
- Créer des flux de travail de bout en bout en utilisant uniquement Media Services. 
- Utiliser des composants tiers pour certaines parties de votre flux de travail. (par exemple, en encodant avec un encodeur tiers). Le contenu est ensuite téléchargé, protégé, empaqueté et remis à l'aide de Media Services.
- Diffuser votre contenu en direct ou de le distribuer à la demande. La rubrique contient également des liens vers d’autres rubriques pertinentes.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Media Services

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a>Exemple

Cet exemple répertorie tous les media services pour un groupe de ressources donné.

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
