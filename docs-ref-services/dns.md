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
ms.openlocfilehash: 610bc878acba978b7be25ea2caee4000cef3b452
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-dns-modules-for-nodejs"></a>Modules Azure DNS pour Node.js

Azure DNS vous permet d’héberger vos domaines DNS dans Azure. Gérez vos enregistrements DNS en utilisant les informations d’identification et le contrat de support et de facturation déjà disponibles avec les autres services Azure. Intégrez en toute transparence les services Azure avec les mises à jour de DNS correspondantes et simplifiez ainsi l’ensemble du processus de déploiement.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure DNS

```bash
npm install azure-arm-dns
```

### <a name="example"></a>Exemples

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
