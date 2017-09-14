---
title: "Exemple de code permettant d’utiliser les bases de données Azure avec Node.js"
description: "Exemple de code illustrant l’utilisation des bases de données Azure avec Node.js."
author: tomarcher
manager: douge
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: tarcher
ms.openlocfilehash: 8292a8fd0353ae84ac2b1622e5c622e60be04c9b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="sample-code-for-using-azure-databases-with-nodejs"></a><span data-ttu-id="755e5-103">Exemple de code permettant d’utiliser les bases de données Azure avec Node.js</span><span class="sxs-lookup"><span data-stu-id="755e5-103">Sample code for using Azure databases with Node.js</span></span>

<span data-ttu-id="755e5-104">L’exemple de code suivant illustre l’utilisation des bases de données Azure avec Node.js.</span><span class="sxs-lookup"><span data-stu-id="755e5-104">The following sample code illustrate using Azure databases with Node.js.</span></span>

<span data-ttu-id="755e5-105">Si vous avez besoin de code pour d’autres tâches, vous pouvez parcourir la liste complète des [exemples Azure Node.js](https://azure.microsoft.com/resources/samples/?term=nodejs).</span><span class="sxs-lookup"><span data-stu-id="755e5-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="755e5-106">**Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="755e5-106">**Cosmos DB**</span></span> ||
| [<span data-ttu-id="755e5-107">Utiliser Azure Cosmos DB et l’API Graph</span><span class="sxs-lookup"><span data-stu-id="755e5-107">Use the Azure Cosmos DB and Graph API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) | <span data-ttu-id="755e5-108">Vous montre comment utiliser Azure Cosmos DB avec l’API Graph pour stocker et accéder aux données à partir d’une application Node.js.</span><span class="sxs-lookup"><span data-stu-id="755e5-108">Shows you how to use the Azure Cosmos DB with the Graph API to store and access data from a Node.js application.</span></span> |
| [<span data-ttu-id="755e5-109">Utiliser Azure Cosmos DB et l’API DocumentDB</span><span class="sxs-lookup"><span data-stu-id="755e5-109">Use the Azure Cosmos DB and Document DB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) | <span data-ttu-id="755e5-110">Vous montre comment utiliser Azure Cosmos DB avec l’API DocumentDB pour stocker et accéder aux données à partir d’une application Node.js.</span><span class="sxs-lookup"><span data-stu-id="755e5-110">Shows you how to use the Azure Cosmos DB with the DocumentDB API to store and access data from a Node.js application.</span></span> |
| <span data-ttu-id="755e5-111">**DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="755e5-111">**DocumentDB**</span></span> ||
| [<span data-ttu-id="755e5-112">Développement d’applications web avec Node.js et Express à l’aide de DocumentDB</span><span class="sxs-lookup"><span data-stu-id="755e5-112">Web application development with Node.js and Express using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-todo-app/) | <span data-ttu-id="755e5-113">Vous montre comment utiliser le service Azure DocumentDB pour stocker des données et y accéder à partir d’une application Node.js Express sur Azure.</span><span class="sxs-lookup"><span data-stu-id="755e5-113">Shows how to use Azure DocumentDB to store and access data from a Node.js Express application on Azure.</span></span> |
| [<span data-ttu-id="755e5-114">Développement d’une application console Node.js à l’aide de DocumentDB</span><span class="sxs-lookup"><span data-stu-id="755e5-114">Developing a Node.js console app using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-getting-started/) | <span data-ttu-id="755e5-115">Cet exemple vous montre comment prendre en main rapidement le service DocumentDB de Microsoft Azure et Node.js.</span><span class="sxs-lookup"><span data-stu-id="755e5-115">This sample shows you how get started quickly with Microsoft Azure DocumentDB service and Node.js.</span></span> |
| <span data-ttu-id="755e5-116">**MongoDB**</span><span class="sxs-lookup"><span data-stu-id="755e5-116">**MongoDB**</span></span> ||
| [<span data-ttu-id="755e5-117">Application web Node.js et MongoDB dans Azure</span><span class="sxs-lookup"><span data-stu-id="755e5-117">Node.js and MongoDB web app in Azure</span></span>](https://azure.microsoft.com/resources/samples/meanjs/) | <span data-ttu-id="755e5-118">Exemple d’application que vous pouvez utiliser pour suivre le didacticiel, [Créer une application web Node.js et MongoDB dans Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span><span class="sxs-lookup"><span data-stu-id="755e5-118">Sample application that you can use to follow along with the tutorial, [Build a Node.js and MongoDB web app in Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span></span> |
| <span data-ttu-id="755e5-119">**Base de données SQL**</span><span class="sxs-lookup"><span data-stu-id="755e5-119">**SQL Database**</span></span> ||
| [<span data-ttu-id="755e5-120">Azure SQL Database : utiliser Node.js pour vous connecter et interroger des données</span><span class="sxs-lookup"><span data-stu-id="755e5-120">Azure SQL Database: Use Node.js to connect and query data</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) | <span data-ttu-id="755e5-121">Indique comment se connecter à une base de données SQL Azure avec Node.js, puis utiliser les instructions Transact-SQL pour interroger, insérer, mettre à jour et supprimer des données dans la base de données à partir des plateformes Windows, Ubuntu Linux et Mac.</span><span class="sxs-lookup"><span data-stu-id="755e5-121">Demonstrates how to connect to an Azure SQL database using Node.js; then use Transact-SQL statements to query, insert, update, and delete data in the database from Windows, Ubuntu Linux, and Mac platforms.</span></span> |