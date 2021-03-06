---
title: Modèle objet SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4452e9eef26d5b31b837da42664053a1bf7b837e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70148591"
---
# <a name="smo-object-model"></a>Modèle objet SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Le modèle objet SMO est composé d'une hiérarchie d'objets. L'objet <xref:Microsoft.SqlServer.Management.Smo.Server> est l'objet de niveau supérieur et tous les objets de classe d'instance résident sous l'objet <xref:Microsoft.SqlServer.Management.Smo.Server>.  
  
 La classe <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> est une classe de niveau supérieur avec une hiérarchie d'objets distincte. L' <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> objet représente [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les services et les paramètres réseau disponibles via le fournisseur WMI.  
  
 Outre les objets <xref:Microsoft.SqlServer.Management.Smo.Server> et <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>, il existe plusieurs classes utilitaires qui représentent des tâches ou des opérations, telles que <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> ou <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
 Le modèle objet SMO est composé de plusieurs espaces de noms. Pour plus d’informations, consultez [Espaces de noms SMO](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Diagramme du modèle objet SMO](../../relational-databases/server-management-objects-smo/smo-object-model-diagram.md)   
 [Espaces de noms SMO](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)   
 [Fournisseur WMI pour les concepts de gestion de configuration](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
