---
title: S’authentifier avec les modules de gestion Azure pour Node.js
description: S’authentifier avec un principal de service dans les modules de gestion Azure pour Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: b665c537bf17d08c44357009552054d6b2e609d2
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220511"
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="60e16-103">S’authentifier avec les modules Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="60e16-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="60e16-104">Toutes les API services requièrent une authentification via un `credentials` objet lorsqu’elles sont en cours d’instanciation.</span><span class="sxs-lookup"><span data-stu-id="60e16-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="60e16-105">Il existe trois façons de s’authentifier et de créer les informations d’identification requises via le kit de développement logiciel Azure pour Node.js :</span><span class="sxs-lookup"><span data-stu-id="60e16-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="60e16-106">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="60e16-106">Basic authentication</span></span>
- <span data-ttu-id="60e16-107">Connexion interactive</span><span class="sxs-lookup"><span data-stu-id="60e16-107">Interactive login</span></span>
- <span data-ttu-id="60e16-108">Authentification d’un principal du service</span><span class="sxs-lookup"><span data-stu-id="60e16-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="60e16-109">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="60e16-109">Basic authentication</span></span>

<span data-ttu-id="60e16-110">Pour effectuer une authentification par programmation à l’aide de vos informations d’identification de compte Azure, utilisez la fonction `loginWithUsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="60e16-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="60e16-111">L’extrait de code JavaScript suivant montre comment utiliser l’authentification de base à l’aide des informations d’identification qui sont stockées sous forme de variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="60e16-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="60e16-112">Connexion interactive</span><span class="sxs-lookup"><span data-stu-id="60e16-112">Interactive login</span></span>

<span data-ttu-id="60e16-113">La connexion interactive fournit un lien et un code qui permettent à l’utilisateur de s’authentifier à partir d’un navigateur.</span><span class="sxs-lookup"><span data-stu-id="60e16-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="60e16-114">Utilisez cette méthode lorsque plusieurs comptes sont utilisés par le même script, ou lorsque l’intervention de l’utilisateur est préférée.</span><span class="sxs-lookup"><span data-stu-id="60e16-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="60e16-115">Authentification d’un principal du service</span><span class="sxs-lookup"><span data-stu-id="60e16-115">Service principal authentication</span></span>

<span data-ttu-id="60e16-116">La [connexion interactive](#interactive-login) est le moyen le plus simple pour s’authentifier.</span><span class="sxs-lookup"><span data-stu-id="60e16-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="60e16-117">Toutefois, lorsque vous utilisez le kit de développement Node.js, il se peut que vous souhaitiez utiliser l’authentification du principal de service plutôt que de fournir vos informations d’identification de compte.</span><span class="sxs-lookup"><span data-stu-id="60e16-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="60e16-118">La rubrique [Créer un principal de service Azure avec Node.js](./node-sdk-azure-authenticate-principal.md) explique les différentes techniques de création (et d’utilisation) d’un principal de service.</span><span class="sxs-lookup"><span data-stu-id="60e16-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 