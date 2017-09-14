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
# <a name="azure-dns-modules-for-nodejs"></a>Modules Azure DNS pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure DNS vous permet d’héberger vos domaines DNS dans Azure. Gérez vos enregistrements DNS en utilisant les informations d’identification et le contrat de support et de facturation déjà disponibles avec les autres services Azure. Intégrez en toute transparence les services Azure avec les mises à jour de DNS correspondantes et simplifiez ainsi l’ensemble du processus de déploiement.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure DNS

```bash
npm install azure-arm-dns
```

### <a name="example"></a>Exemple

Cet exemple répertorie les zones de gestion DNS.

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

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
