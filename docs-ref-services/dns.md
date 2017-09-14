---
title: Modules Azure DNS pour Node.js
description: "Références pour les modules Azure DNS pour Node.js"
keywords: Azure, SDK, API, DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="1fb25-104">Modules Azure DNS pour Node.js</span><span class="sxs-lookup"><span data-stu-id="1fb25-104">Azure DNS modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1fb25-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="1fb25-105">Overview</span></span>

<span data-ttu-id="1fb25-106">Azure DNS vous permet d’héberger vos domaines DNS dans Azure.</span><span class="sxs-lookup"><span data-stu-id="1fb25-106">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="1fb25-107">Gérez vos enregistrements DNS en utilisant les informations d’identification et le contrat de support et de facturation déjà disponibles avec les autres services Azure.</span><span class="sxs-lookup"><span data-stu-id="1fb25-107">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="1fb25-108">Intégrez en toute transparence les services Azure avec les mises à jour de DNS correspondantes et simplifiez ainsi l’ensemble du processus de déploiement.</span><span class="sxs-lookup"><span data-stu-id="1fb25-108">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="1fb25-109">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="1fb25-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1fb25-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="1fb25-110">Install the npm module</span></span>

<span data-ttu-id="1fb25-111">Installer le module npm Azure DNS</span><span class="sxs-lookup"><span data-stu-id="1fb25-111">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="1fb25-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="1fb25-112">Example</span></span>

<span data-ttu-id="1fb25-113">Cet exemple répertorie les zones de gestion DNS.</span><span class="sxs-lookup"><span data-stu-id="1fb25-113">This example lists the DNS Management zones.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="1fb25-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="1fb25-114">Samples</span></span>

<span data-ttu-id="1fb25-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="1fb25-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
