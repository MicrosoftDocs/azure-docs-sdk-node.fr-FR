---
title: Modules Azure DNS pour Node.js
description: Références pour les modules Azure DNS pour Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52106327"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="1d8c6-103">Modules Azure DNS pour Node.js</span><span class="sxs-lookup"><span data-stu-id="1d8c6-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="1d8c6-104">Azure DNS vous permet d’héberger vos domaines DNS dans Azure.</span><span class="sxs-lookup"><span data-stu-id="1d8c6-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="1d8c6-105">Gérez vos enregistrements DNS en utilisant les informations d’identification et le contrat de support et de facturation déjà disponibles avec les autres services Azure.</span><span class="sxs-lookup"><span data-stu-id="1d8c6-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="1d8c6-106">Intégrez en toute transparence les services Azure avec les mises à jour de DNS correspondantes et simplifiez ainsi l’ensemble du processus de déploiement.</span><span class="sxs-lookup"><span data-stu-id="1d8c6-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="1d8c6-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="1d8c6-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1d8c6-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="1d8c6-108">Install the npm module</span></span>

<span data-ttu-id="1d8c6-109">Installer le module npm Azure DNS</span><span class="sxs-lookup"><span data-stu-id="1d8c6-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="1d8c6-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="1d8c6-110">Example</span></span>

<span data-ttu-id="1d8c6-111">Cet exemple répertorie les zones de gestion DNS.</span><span class="sxs-lookup"><span data-stu-id="1d8c6-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="1d8c6-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="1d8c6-112">Samples</span></span>

<span data-ttu-id="1d8c6-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="1d8c6-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
