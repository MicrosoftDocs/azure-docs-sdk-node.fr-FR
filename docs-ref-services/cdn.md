---
title: Modules Azure CDN pour Node.js
description: Références pour les modules Azure CDN pour Node.js
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: 1117f8fabfe364d3e5602ee89f652fe98851fef4
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50340267"
---
# <a name="azure-cdn-modules-for-nodejs"></a>Modules Azure CDN pour Node.js

## <a name="overview"></a>Vue d’ensemble

Azure Content Delivery Network (CDN) offre aux développeurs une solution globale pour fournir du contenu de large bande passante hébergé dans Azure ou ailleurs. Le réseau de diffusion de contenu (CDN) vous permet de mettre en cache des objets disponibles publiquement, chargés à partir d’un stockage d’objets blob Azure, d’une application web, d’une machine virtuelle, d’un dossier d’application ou d’un autre emplacement HTTP/HTTPS. Le cache du CDN peut être maintenu dans des emplacements stratégiques afin d’offrir une bande passante maximale pour la distribution de contenu aux utilisateurs. Le CDN est généralement utilisé pour distribuer du contenu statique tel que des images, des feuilles de style, des documents, des fichiers, des scripts côté client et des pages HTML.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure CDN

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>Exemples

Cet exemple répertorie tous les profils CDN.

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
