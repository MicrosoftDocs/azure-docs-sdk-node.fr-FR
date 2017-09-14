---
title: Modules Azure Logic Apps pour Node.js
description: "Références pour les modules Azure Logic Apps pour Node.js"
keywords: Azure, SDK, API, Logic Apps, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="f7f80-104">Modules Azure Logic Apps pour Node.js</span><span class="sxs-lookup"><span data-stu-id="f7f80-104">Azure Logic Apps modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f7f80-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="f7f80-105">Overview</span></span>
<span data-ttu-id="f7f80-106">Logic Apps offre un moyen de simplifier et d’implémenter des intégrations et des workflows évolutifs dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="f7f80-106">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="f7f80-107">Son concepteur visuel modélise et automatise votre processus sous la forme d’une série d’étapes appelée workflow.</span><span class="sxs-lookup"><span data-stu-id="f7f80-107">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="f7f80-108">De nombreux connecteurs sont disponibles dans le cloud et en local pour accélérer l’intégration dans différents services et protocoles.</span><span class="sxs-lookup"><span data-stu-id="f7f80-108">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="f7f80-109">Une application logique commence par un déclencheur (tel que « Lorsqu’un compte est ajouté à Dynamics CRM »). Après le déclenchement, cette application peut initialiser de nombreuses combinaisons d’actions, de conversions et de conditions logiques.</span><span class="sxs-lookup"><span data-stu-id="f7f80-109">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="f7f80-110">Les avantages de Logic Apps sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f7f80-110">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="f7f80-111">Gain de temps en créant des processus complexes à l’aide d’outils de conception faciles à comprendre</span><span class="sxs-lookup"><span data-stu-id="f7f80-111">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="f7f80-112">Implémentation transparente de modèles et de workflows qui seraient sans cela difficiles à mettre en œuvre dans le code</span><span class="sxs-lookup"><span data-stu-id="f7f80-112">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="f7f80-113">Mise en route rapide à partir de modèles</span><span class="sxs-lookup"><span data-stu-id="f7f80-113">Getting started quickly from templates</span></span>
- <span data-ttu-id="f7f80-114">Personnalisation de votre application logique avec vos propres API, lignes de code et actions personnalisées</span><span class="sxs-lookup"><span data-stu-id="f7f80-114">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="f7f80-115">Connexion et synchronisation de systèmes disparates sur site et dans le cloud</span><span class="sxs-lookup"><span data-stu-id="f7f80-115">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="f7f80-116">Exploitation du serveur BizTalk, de Gestion des API, d’Azure Functions et d’Azure Service Bus avec la prise en charge d’une intégration de premier plan</span><span class="sxs-lookup"><span data-stu-id="f7f80-116">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="f7f80-117">Logic Apps est une fonctionnalité iPaaS (integration platform as a service) entièrement gérée, qui évite aux développeurs l’obligation d’assurer l’hébergement, l’évolutivité, la disponibilité et la gestion.</span><span class="sxs-lookup"><span data-stu-id="f7f80-117">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="f7f80-118">Logic Apps monte en puissance automatiquement pour répondre à la demande.</span><span class="sxs-lookup"><span data-stu-id="f7f80-118">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="f7f80-119">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="f7f80-119">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f7f80-120">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="f7f80-120">Install the npm module</span></span>

<span data-ttu-id="f7f80-121">Installer le module Azure Logic pour Node.js</span><span class="sxs-lookup"><span data-stu-id="f7f80-121">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="f7f80-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="f7f80-122">Example</span></span>

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

### <a name="samples"></a><span data-ttu-id="f7f80-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="f7f80-123">Samples</span></span>

<span data-ttu-id="f7f80-124">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="f7f80-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
