---
title: Modules Azure Authorization pour Node.js
description: "Références pour les modules Azure Authorization pour Node.js"
keywords: Azure, SDK, API, Authorization, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-authorization-modules-for-nodejs"></a>Modules Azure Authorization pour Node.js

## <a name="overview"></a>Vue d'ensemble

L’authentification/autorisation d’Azure App Service est une fonctionnalité qui permet à votre application de connecter les utilisateurs de sorte à ne pas être obligé de modifier le code sur le serveur principal. L’autorisation propose un moyen simple de protéger votre application et fonctionne avec des données par utilisateur.

## <a name="management-package"></a>Gestion des packages

Utiliser npm pour installer les modules Azure Authorization pour Node.js

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Authorization

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>Exemple

Cet exemple répertorie toutes les attributions de rôle pour le groupe de ressources demandé.

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
