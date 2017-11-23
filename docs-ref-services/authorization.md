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
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="ba66c-104">Modules Azure Authorization pour Node.js</span><span class="sxs-lookup"><span data-stu-id="ba66c-104">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ba66c-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ba66c-105">Overview</span></span>

<span data-ttu-id="ba66c-106">L’authentification/autorisation d’Azure App Service est une fonctionnalité qui permet à votre application de connecter les utilisateurs de sorte à ne pas être obligé de modifier le code sur le serveur principal.</span><span class="sxs-lookup"><span data-stu-id="ba66c-106">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="ba66c-107">L’autorisation propose un moyen simple de protéger votre application et fonctionne avec des données par utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ba66c-107">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="ba66c-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="ba66c-108">Management package</span></span>

<span data-ttu-id="ba66c-109">Utiliser npm pour installer les modules Azure Authorization pour Node.js</span><span class="sxs-lookup"><span data-stu-id="ba66c-109">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ba66c-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="ba66c-110">Install the npm module</span></span>

<span data-ttu-id="ba66c-111">Installer le module npm Azure Authorization</span><span class="sxs-lookup"><span data-stu-id="ba66c-111">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="ba66c-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="ba66c-112">Example</span></span>

<span data-ttu-id="ba66c-113">Cet exemple répertorie toutes les attributions de rôle pour le groupe de ressources demandé.</span><span class="sxs-lookup"><span data-stu-id="ba66c-113">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ba66c-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="ba66c-114">Samples</span></span>

<span data-ttu-id="ba66c-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="ba66c-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
