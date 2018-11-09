---
title: Modules Azure Data Lake Analytics pour Node.js
description: Références pour les modules Azure Data Lake Analytics pour Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 97a846d9970310931e05e681b23b5787c97260b6
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51134328"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="3fe79-103">Modules Azure Data Lake Analytics pour Node.js</span><span class="sxs-lookup"><span data-stu-id="3fe79-103">Azure Data Lake Analytics modules for Node.js</span></span>

<span data-ttu-id="3fe79-104">Azure Data Lake Analytics est un service de travaux d’analyse à la demande, qui simplifie l’analyse du Big Data.</span><span class="sxs-lookup"><span data-stu-id="3fe79-104">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="3fe79-105">Vous pouvez vous concentrer sur l’écriture, l’exécution et la gestion des travaux, plutôt que sur le fonctionnement de l’infrastructure distribuée.</span><span class="sxs-lookup"><span data-stu-id="3fe79-105">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="3fe79-106">Au lieu de déployer, de configurer et d’optimiser le matériel, vous écrivez des requêtes pour transformer vos données et en extraire des informations pertinentes.</span><span class="sxs-lookup"><span data-stu-id="3fe79-106">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="3fe79-107">Le service d’analyse peut traiter les travaux instantanément, quelle qu’en soit l’échelle, en définissant le compteur sur la puissance requise.</span><span class="sxs-lookup"><span data-stu-id="3fe79-107">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="3fe79-108">Vous payez les travaux uniquement lorsque ceux-ci sont exécutés, ce qui rend le service économique.</span><span class="sxs-lookup"><span data-stu-id="3fe79-108">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="3fe79-109">Le service d’analyse prend en charge Azure Active Directory, ce qui vous permet de gérer les accès et les rôles et de bénéficier d’une intégration à votre système d’identité local.</span><span class="sxs-lookup"><span data-stu-id="3fe79-109">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="3fe79-110">Il inclut également U-SQL, un langage qui associe les avantages de SQL avec la puissance d'expression du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3fe79-110">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="3fe79-111">Le runtime distribué et évolutif d’U-SQL vous permet d’analyser efficacement les données situées dans le magasin et sur les serveurs SQL Server dans Azure, Azure SQL Database et Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="3fe79-111">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="3fe79-112">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="3fe79-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3fe79-113">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="3fe79-113">Install the npm module</span></span>

<span data-ttu-id="3fe79-114">Utiliser npm pour installer les modules Azure Data Lake Analytics pour Node.js</span><span class="sxs-lookup"><span data-stu-id="3fe79-114">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="3fe79-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="3fe79-115">Example</span></span>

<span data-ttu-id="3fe79-116">Cet exemple répertorie tous les comptes Analytics pour un abonnement donné.</span><span class="sxs-lookup"><span data-stu-id="3fe79-116">This example lists all of the analytics accounts for a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="3fe79-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="3fe79-117">Samples</span></span>

<span data-ttu-id="3fe79-118">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="3fe79-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
