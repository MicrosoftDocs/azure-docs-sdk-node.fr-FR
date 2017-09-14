---
title: "S’authentifier avec les modules de gestion Azure pour Node.js"
description: "S’authentifier avec un principal de service dans les modules de gestion Azure pour Node.js"
keywords: "Azure, nœud, SDK, API, authentification, Active Directory, principal de service"
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a>S’authentifier avec les modules Azure pour Node.js 

Toutes les API services requièrent une authentification via un `credentials` objet lorsqu’elles sont en cours d’instanciation. Il existe trois façons de s’authentifier et de créer les informations d’identification requises via le kit de développement logiciel Azure pour Node.js : 

- Authentification de base
- Connexion interactive
- Authentification d’un principal du service

## <a name="basic-authentication"></a>Authentification de base

Pour effectuer une authentification par programmation à l’aide de vos informations d’identification de compte Azure, utilisez la fonction `loginWithUsernamePassword`. L’extrait de code JavaScript suivant montre comment utiliser l’authentification de base à l’aide des informations d’identification qui sont stockées sous forme de variables d’environnement. 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a>Connexion interactive

La connexion interactive fournit un lien et un code qui permettent à l’utilisateur de s’authentifier à partir d’un navigateur. Utilisez cette méthode lorsque plusieurs comptes sont utilisés par le même script, ou lorsque l’intervention de l’utilisateur est préférée.

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a>Authentification d’un principal du service

La [connexion interactive](#interactive-login) est le moyen le plus simple pour s’authentifier. Toutefois, lorsque vous utilisez le kit de développement Node.js, il se peut que vous souhaitiez utiliser l’authentification du principal de service plutôt que de fournir vos informations d’identification de compte. La rubrique [Créer un principal de service Azure avec Node.js](./node-sdk-azure-authenticate-principal.md) explique les différentes techniques de création (et d’utilisation) d’un principal de service. 