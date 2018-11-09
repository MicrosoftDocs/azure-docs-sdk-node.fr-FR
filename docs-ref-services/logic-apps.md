---
title: Modules Azure Logic Apps pour Node.js
description: Références pour les modules Azure Logic Apps pour Node.js
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 021f57c7f4f1b86a3c0e97f345d2f934351669b8
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51111164"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="15988-103">Modules Azure Logic Apps pour Node.js</span><span class="sxs-lookup"><span data-stu-id="15988-103">Azure Logic Apps modules for Node.js</span></span>

<span data-ttu-id="15988-104">Logic Apps offre un moyen de simplifier et d’implémenter des intégrations et des workflows évolutifs dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="15988-104">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="15988-105">Son concepteur visuel modélise et automatise votre processus sous la forme d’une série d’étapes appelée workflow.</span><span class="sxs-lookup"><span data-stu-id="15988-105">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="15988-106">De nombreux connecteurs sont disponibles dans le cloud et en local pour accélérer l’intégration dans différents services et protocoles.</span><span class="sxs-lookup"><span data-stu-id="15988-106">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="15988-107">Une application logique commence par un déclencheur (tel que « Lorsqu’un compte est ajouté à Dynamics CRM »). Après le déclenchement, cette application peut initialiser de nombreuses combinaisons d’actions, de conversions et de conditions logiques.</span><span class="sxs-lookup"><span data-stu-id="15988-107">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="15988-108">Les avantages de Logic Apps sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="15988-108">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="15988-109">Gain de temps en créant des processus complexes à l’aide d’outils de conception faciles à comprendre</span><span class="sxs-lookup"><span data-stu-id="15988-109">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="15988-110">Implémentation transparente de modèles et de workflows qui seraient sans cela difficiles à mettre en œuvre dans le code</span><span class="sxs-lookup"><span data-stu-id="15988-110">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="15988-111">Mise en route rapide à partir de modèles</span><span class="sxs-lookup"><span data-stu-id="15988-111">Getting started quickly from templates</span></span>
- <span data-ttu-id="15988-112">Personnalisation de votre application logique avec vos propres API, lignes de code et actions personnalisées</span><span class="sxs-lookup"><span data-stu-id="15988-112">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="15988-113">Connexion et synchronisation de systèmes disparates sur site et dans le cloud</span><span class="sxs-lookup"><span data-stu-id="15988-113">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="15988-114">Exploitation du serveur BizTalk, de Gestion des API, d’Azure Functions et d’Azure Service Bus avec la prise en charge d’une intégration de premier plan</span><span class="sxs-lookup"><span data-stu-id="15988-114">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="15988-115">Logic Apps est une fonctionnalité iPaaS (integration platform as a service) entièrement gérée, qui évite aux développeurs l’obligation d’assurer l’hébergement, l’évolutivité, la disponibilité et la gestion.</span><span class="sxs-lookup"><span data-stu-id="15988-115">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="15988-116">Logic Apps monte en puissance automatiquement pour répondre à la demande.</span><span class="sxs-lookup"><span data-stu-id="15988-116">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="15988-117">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="15988-117">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="15988-118">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="15988-118">Install the npm module</span></span>

<span data-ttu-id="15988-119">Installer le module Azure Logic pour Node.js</span><span class="sxs-lookup"><span data-stu-id="15988-119">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="15988-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="15988-120">Example</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a><span data-ttu-id="15988-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="15988-121">Samples</span></span>

<span data-ttu-id="15988-122">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="15988-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
