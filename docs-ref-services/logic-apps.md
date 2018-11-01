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
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50281532"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Modules Azure Logic Apps pour Node.js

Logic Apps offre un moyen de simplifier et d’implémenter des intégrations et des workflows évolutifs dans le cloud. Son concepteur visuel modélise et automatise votre processus sous la forme d’une série d’étapes appelée workflow. De nombreux connecteurs sont disponibles dans le cloud et en local pour accélérer l’intégration dans différents services et protocoles. Une application logique commence par un déclencheur (tel que « Lorsqu’un compte est ajouté à Dynamics CRM »). Après le déclenchement, cette application peut initialiser de nombreuses combinaisons d’actions, de conversions et de conditions logiques.

Les avantages de Logic Apps sont les suivants :
- Gain de temps en créant des processus complexes à l’aide d’outils de conception faciles à comprendre
- Implémentation transparente de modèles et de workflows qui seraient sans cela difficiles à mettre en œuvre dans le code
- Mise en route rapide à partir de modèles
- Personnalisation de votre application logique avec vos propres API, lignes de code et actions personnalisées
- Connexion et synchronisation de systèmes disparates sur site et dans le cloud
- Exploitation du serveur BizTalk, de Gestion des API, d’Azure Functions et d’Azure Service Bus avec la prise en charge d’une intégration de premier plan

Logic Apps est une fonctionnalité iPaaS (integration platform as a service) entièrement gérée, qui évite aux développeurs l’obligation d’assurer l’hébergement, l’évolutivité, la disponibilité et la gestion. Logic Apps monte en puissance automatiquement pour répondre à la demande.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module Azure Logic pour Node.js

```bash
npm install azure-arm-logic
```

### <a name="example"></a>Exemples

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

### <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
