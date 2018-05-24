---
title: Modules Azure Key Vault pour Node.js
description: Références pour les modules Azure Key Vault pour Node.js
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: 72bf4bc5443618f5f1bb9b4d1bb4d905669ff8c8
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-key-vault-modules-for-nodejs"></a>Modules Azure Key Vault pour Node.js

Azure Key Vault permet de protéger les clés de chiffrement et les secrets utilisés par les services et les applications cloud. En utilisant Key Vault, vous pouvez chiffrer les clés et les secrets (tels que les clés d’authentification, les clés de compte de stockage, les clés de chiffrement de données, les fichiers PFX et les mots de passe) à l’aide de clés protégées par des modules de sécurité matériels (HSM). Pour une meilleure garantie, vous pouvez importer ou générer des clés HSM. Dans ce cas, Microsoft traite vos clés dans des modules de sécurité matériels validés selon la norme « FIPS 140-2 Level 2 » (matériel et microprogramme).

Key Vault rationalise le processus de gestion de clés et vous permet de garder le contrôle des clés qui accèdent à vos données et les chiffrent. Les développeurs peuvent créer des clés pour le développement et le test en quelques minutes, puis les migrer en toute transparence en clés de production. Les administrateurs de sécurité peuvent accorder (et annuler) les autorisations sur les clés, si nécessaire.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm 

Installer le module npm Azure Key Vault

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>Exemples

Cet exemple crée un nouveau service Key Vault dans Azure.

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a>Exemples

- [Bien démarrer avec Key Vault dans Node.js](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [Manage Azure resources and resource groups with Node.js (Gérer des ressources et des groupes de ressources Azure avec Node.js)](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [Intégration d’Azure AD dans une application web Node.JS](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
