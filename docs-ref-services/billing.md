---
title: Modules Facturation Azure pour Node.js
description: Références pour les modules Facturation Azure pour Node.js
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 20df85ae5e504e460a501737aa07b6692a0da3c7
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47346678"
---
# <a name="azure-billing-modules-for-nodejs"></a>Modules Facturation Azure pour Node.js

## <a name="overview"></a>Vue d’ensemble
Les API Facturation Azure offrent un accès à vos factures Azure et leurs détails.

Pour utiliser cette API, l’administrateur du compte doit s’abonner depuis le portail Azure. Consultez [Gérer l’accès à la facturation Azure à l’aide de rôles](https://docs.microsoft.com/azure/billing/billing-manage-access).

### <a name="install-the-npm-module"></a>Installer le module npm 

Installer le module npm de Facturation Azure 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>Exemples 
 
Cet exemple imprime une liste de toutes vos précédentes factures.
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
