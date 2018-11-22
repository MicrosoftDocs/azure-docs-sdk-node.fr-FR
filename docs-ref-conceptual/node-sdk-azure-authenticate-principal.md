---
title: Créer un principal de service Azure avec Node.js
description: Apprendre à utiliser l’authentification par principale de service via Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 98d52e21332138512d40ff2de9f5d3388fa596e4
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52140824"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a>Créer un principal de service Azure avec Node.js 

Lorsqu’une application doit accéder à des ressources, vous pouvez configurer une identité pour l’application et authentifier l’application avec ses propres informations d’identification. Cette identité est connue en tant que *principal de service*. Essentiellement, vous créez des clés pour votre compte Azure Active Directory que vous fournissez au SDK pour l’authentification au lieu de demander l’intervention de l’utilisateur ou bien une combinaison nom d’utilisateur/mot de passe.

L’approche de principal de service vous permet de :
- Affecter à l’identité de l’application des autorisations différentes de vos propres autorisations. En règle générale, ces autorisations sont strictement limitées à ce que l’application doit faire.
- Utilisez un certificat pour l’authentification lors de l’exécution d’un script sans assistance.

Cette rubrique vous montre trois techniques de création d’un principal de service.

- Portail Azure
- Azure CLI 2.0
- Kit de développement logiciel (SDK) Azure pour Node.js

## <a name="create-a-service-principal-using-the-azure-portal"></a>Création d’un principal de service à l’aide du portail Azure

Suivez les étapes planifiées dans la rubrique, [Utiliser le portail pour créer une application et un principal de service Azure Active Directory pouvant accéder aux ressources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), pour générer le principal de service.

## <a name="create-a-service-principal-using-the-azure-cli-20"></a>Création d’un principal de service à l’aide d’Azure CLI 2.0

La création d’un principal de service à l’aide d’[Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) peut suivre les étapes suivantes :

1. Téléchargez [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).

2. Ouvrez une fenêtre de terminal.

3. Tapez la commande suivante pour démarrer le processus d’ouverture de session :

    ```shell
    $ az login
    ```

4. Appeler `az login` résulte en une URL et un code. Accédez à l’URL spécifiée, entrez le code, puis connectez-vous avec votre identité Azure (Cela peut se produire automatiquement si vous êtes déjà connecté). Vous serez alors en mesure d’accéder à votre compte via l’interface CLI.

5. Obtenez vos ID d’abonnement et de client :

    ```shell
    $ az account list
    ```

    Voici un exemple de sortie :

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    **Prenez note de l’ID d’abonnement car il sera utilisé à l’étape 7.**

6. Créez un principal de service afin d’obtenir un objet JSON contenant les autres éléments d’information dont vous avez besoin pour vous authentifier avec Azure.

    ```shell
    $ az ad sp create-for-rbac
    ```

    Voici un exemple de sortie :

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    **Notez les valeurs de client, nom et mot de passe car elles sont utilisées à l’étape 7.**

7. Définissez les variables d’environnement en remplaçant les espaces réservés &lt;ID d’abonnement>, &lt;client >, &lt;nom >, et &lt;mot de passe par les valeurs obtenues aux étapes 4 et 5. 

    **Avec Bash**

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    **Utiliser PowerShell**

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a>Création d’un principal de service à l’aide du kit de développement logiciel Azure pour Node.js

Pour créer un principal de service par programmation à l’aide de JavaScript, utilisez le [script ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).   

## <a name="using-the-service-principal"></a>Utilisation du principal de service

Une fois que vous avez un principal de service, l’extrait de code JavaScript suivant montre comment utiliser les clés de principale de service pour l’authentification avec le SDK Azure pour Node.js. Modifiez les espaces réservés suivants : &lt;ID client ou ID d’app >, &lt;secret ou mot de passe >, et &lt;domaine ou client>,

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
