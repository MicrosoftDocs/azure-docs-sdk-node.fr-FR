---
title: Modules Azure Authorization pour Node.js
description: Références pour les modules Azure Authorization pour Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51062028"
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="c5140-103">Modules Azure Authorization pour Node.js</span><span class="sxs-lookup"><span data-stu-id="c5140-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c5140-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="c5140-104">Overview</span></span>

<span data-ttu-id="c5140-105">L’authentification/autorisation d’Azure App Service est une fonctionnalité qui permet à votre application de connecter les utilisateurs de sorte à ne pas être obligé de modifier le code sur le serveur principal.</span><span class="sxs-lookup"><span data-stu-id="c5140-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="c5140-106">L’autorisation propose un moyen simple de protéger votre application et fonctionne avec des données par utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c5140-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="c5140-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="c5140-107">Management package</span></span>

<span data-ttu-id="c5140-108">Utiliser npm pour installer les modules Azure Authorization pour Node.js</span><span class="sxs-lookup"><span data-stu-id="c5140-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c5140-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="c5140-109">Install the npm module</span></span>

<span data-ttu-id="c5140-110">Installer le module npm Azure Authorization</span><span class="sxs-lookup"><span data-stu-id="c5140-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="c5140-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="c5140-111">Example</span></span>

<span data-ttu-id="c5140-112">Cet exemple répertorie toutes les attributions de rôle pour le groupe de ressources demandé.</span><span class="sxs-lookup"><span data-stu-id="c5140-112">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="c5140-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="c5140-113">Samples</span></span>

<span data-ttu-id="c5140-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="c5140-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
