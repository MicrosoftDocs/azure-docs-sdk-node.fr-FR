---
title: Modules Facturation Azure pour Node.js
description: "Références pour les modules Facturation Azure pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 58eed8996f543e845a53a741f8684d9e7f6cc1e4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-billing-modules-for-nodejs"></a>Modules Facturation Azure pour Node.js

## <a name="overview"></a>Vue d'ensemble
Les API Facturation Azure offrent un accès à vos factures Azure et leurs détails.

Pour utiliser cette API, l’administrateur du compte doit s’abonner depuis le portail Azure. Consultez [Gérer l’accès à la facturation Azure à l’aide de rôles](https://docs.microsoft.com/azure/billing/billing-manage-access).

### <a name="install-the-npm-module"></a>Installer le module npm 

Installer le module npm de Facturation Azure 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>exemples 
 
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
