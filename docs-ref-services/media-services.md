---
title: Modules Azure Media Services pour Node.js
description: "Références pour les modules Azure Media Services pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 77a6716d4ef0d566690325a86e85d66c5ac234d6
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="72e00-103">Modules Azure Media Services pour Node.js</span><span class="sxs-lookup"><span data-stu-id="72e00-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="72e00-104">Azure Media Services est une plateforme extensible basée sur le cloud qui permet aux développeurs de créer des applications évolutives de gestion et de diffusion de médias.</span><span class="sxs-lookup"><span data-stu-id="72e00-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="72e00-105">Media Services est basé sur les API REST qui permettent de télécharger, stocker, encoder et empaqueter en toute sécurité du contenu vidéo ou audio destiné à être diffusé à la demande ou en direct sur différents clients (par exemple, téléviseurs, PC et appareils mobiles).</span><span class="sxs-lookup"><span data-stu-id="72e00-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="72e00-106">Avec Azure Media Services, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="72e00-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="72e00-107">Créer des flux de travail de bout en bout en utilisant uniquement Media Services.</span><span class="sxs-lookup"><span data-stu-id="72e00-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="72e00-108">Utiliser des composants tiers pour certaines parties de votre flux de travail.</span><span class="sxs-lookup"><span data-stu-id="72e00-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="72e00-109">(par exemple, en encodant avec un encodeur tiers).</span><span class="sxs-lookup"><span data-stu-id="72e00-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="72e00-110">Le contenu est ensuite téléchargé, protégé, empaqueté et remis à l'aide de Media Services.</span><span class="sxs-lookup"><span data-stu-id="72e00-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="72e00-111">Diffuser votre contenu en direct ou de le distribuer à la demande.</span><span class="sxs-lookup"><span data-stu-id="72e00-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="72e00-112">La rubrique contient également des liens vers d’autres rubriques pertinentes.</span><span class="sxs-lookup"><span data-stu-id="72e00-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="72e00-113">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="72e00-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="72e00-114">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="72e00-114">Install the npm module</span></span>

<span data-ttu-id="72e00-115">Installer le module npm Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="72e00-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="72e00-116">exemples</span><span class="sxs-lookup"><span data-stu-id="72e00-116">Example</span></span>

<span data-ttu-id="72e00-117">Cet exemple répertorie tous les media services pour un groupe de ressources donné.</span><span class="sxs-lookup"><span data-stu-id="72e00-117">This example lists all media services for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="72e00-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="72e00-118">Samples</span></span>

<span data-ttu-id="72e00-119">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="72e00-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
