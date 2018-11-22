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
ms.openlocfilehash: 36bc5e97a5eea6e821f66bff9b3e8f610baa2dd0
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52098864"
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="731c0-103">Modules Azure Key Vault pour Node.js</span><span class="sxs-lookup"><span data-stu-id="731c0-103">Azure Key Vault modules for Node.js</span></span>

<span data-ttu-id="731c0-104">Azure Key Vault permet de protéger les clés de chiffrement et les secrets utilisés par les services et les applications cloud.</span><span class="sxs-lookup"><span data-stu-id="731c0-104">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="731c0-105">En utilisant Key Vault, vous pouvez chiffrer les clés et les secrets (tels que les clés d’authentification, les clés de compte de stockage, les clés de chiffrement de données, les fichiers PFX et les mots de passe) à l’aide de clés protégées par des modules de sécurité matériels (HSM).</span><span class="sxs-lookup"><span data-stu-id="731c0-105">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="731c0-106">Pour une meilleure garantie, vous pouvez importer ou générer des clés HSM.</span><span class="sxs-lookup"><span data-stu-id="731c0-106">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="731c0-107">Dans ce cas, Microsoft traite vos clés dans des modules de sécurité matériels validés selon la norme « FIPS 140-2 Level 2 » (matériel et microprogramme).</span><span class="sxs-lookup"><span data-stu-id="731c0-107">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="731c0-108">Key Vault rationalise le processus de gestion de clés et vous permet de garder le contrôle des clés qui accèdent à vos données et les chiffrent.</span><span class="sxs-lookup"><span data-stu-id="731c0-108">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="731c0-109">Les développeurs peuvent créer des clés pour le développement et le test en quelques minutes, puis les migrer en toute transparence en clés de production.</span><span class="sxs-lookup"><span data-stu-id="731c0-109">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="731c0-110">Les administrateurs de sécurité peuvent accorder (et annuler) les autorisations sur les clés, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="731c0-110">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="731c0-111">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="731c0-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="731c0-112">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="731c0-112">Install the npm module</span></span> 

<span data-ttu-id="731c0-113">Installer le module npm Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="731c0-113">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="731c0-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="731c0-114">Example</span></span>

<span data-ttu-id="731c0-115">Cet exemple crée un nouveau service Key Vault dans Azure.</span><span class="sxs-lookup"><span data-stu-id="731c0-115">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="731c0-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="731c0-116">Samples</span></span>

- [<span data-ttu-id="731c0-117">Bien démarrer avec Key Vault dans Node.js</span><span class="sxs-lookup"><span data-stu-id="731c0-117">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="731c0-118">Manage Azure resources and resource groups with Node.js (Gérer des ressources et des groupes de ressources Azure avec Node.js)</span><span class="sxs-lookup"><span data-stu-id="731c0-118">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [<span data-ttu-id="731c0-119">Intégration d’Azure AD dans une application web Node.JS</span><span class="sxs-lookup"><span data-stu-id="731c0-119">Integrating Azure AD into a NodeJS web application</span></span>](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

<span data-ttu-id="731c0-120">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="731c0-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
