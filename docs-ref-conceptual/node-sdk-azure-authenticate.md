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
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="95648-104">S’authentifier avec les modules Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="95648-104">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="95648-105">Toutes les API services requièrent une authentification via un `credentials` objet lorsqu’elles sont en cours d’instanciation.</span><span class="sxs-lookup"><span data-stu-id="95648-105">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="95648-106">Il existe trois façons de s’authentifier et de créer les informations d’identification requises via le kit de développement logiciel Azure pour Node.js :</span><span class="sxs-lookup"><span data-stu-id="95648-106">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="95648-107">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="95648-107">Basic authentication</span></span>
- <span data-ttu-id="95648-108">Connexion interactive</span><span class="sxs-lookup"><span data-stu-id="95648-108">Interactive login</span></span>
- <span data-ttu-id="95648-109">Authentification d’un principal du service</span><span class="sxs-lookup"><span data-stu-id="95648-109">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="95648-110">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="95648-110">Basic authentication</span></span>

<span data-ttu-id="95648-111">Pour effectuer une authentification par programmation à l’aide de vos informations d’identification de compte Azure, utilisez la fonction `loginWithUsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="95648-111">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="95648-112">L’extrait de code JavaScript suivant montre comment utiliser l’authentification de base à l’aide des informations d’identification qui sont stockées sous forme de variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="95648-112">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="95648-113">Connexion interactive</span><span class="sxs-lookup"><span data-stu-id="95648-113">Interactive login</span></span>

<span data-ttu-id="95648-114">La connexion interactive fournit un lien et un code qui permettent à l’utilisateur de s’authentifier à partir d’un navigateur.</span><span class="sxs-lookup"><span data-stu-id="95648-114">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="95648-115">Utilisez cette méthode lorsque plusieurs comptes sont utilisés par le même script, ou lorsque l’intervention de l’utilisateur est préférée.</span><span class="sxs-lookup"><span data-stu-id="95648-115">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="95648-116">Authentification d’un principal du service</span><span class="sxs-lookup"><span data-stu-id="95648-116">Service principal authentication</span></span>

<span data-ttu-id="95648-117">La [connexion interactive](#interactive-login) est le moyen le plus simple pour s’authentifier.</span><span class="sxs-lookup"><span data-stu-id="95648-117">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="95648-118">Toutefois, lorsque vous utilisez le kit de développement Node.js, il se peut que vous souhaitiez utiliser l’authentification du principal de service plutôt que de fournir vos informations d’identification de compte.</span><span class="sxs-lookup"><span data-stu-id="95648-118">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="95648-119">La rubrique [Créer un principal de service Azure avec Node.js](./node-sdk-azure-authenticate-principal.md) explique les différentes techniques de création (et d’utilisation) d’un principal de service.</span><span class="sxs-lookup"><span data-stu-id="95648-119">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 