---
title: SQL Server:Buffer Node | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Buffer Node
- Buffer Node object
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 9011394dccf472499c1c8a8bd1023b7c23009883
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "67987211"
---
# <a name="sql-serverbuffer-node"></a>SQL Server:Buffer Node
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'objet **Nœud de tampon** fournit des compteurs qui complètent les compteurs de l'objet **Gestionnaire de tampons** . Il vous permet de contrôler la distribution des pages du pool de mémoires tampons [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour chaque nœud NUMA (Non-Uniform Memory Access). Il existe une instance de l'objet **Nœud de tampon** pour chaque nœud NUMA employé. Dans une architecture non-NUMA, une seule instance de l’objet **Nœud de tampon** est présente.  
  
## <a name="buffer-node-performance-objects"></a>Objets de performances du Nœud de tampon  
 Ce tableau décrit les objets de performance **Nœud de tampon** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs de l'objet Nœud de tampon de SQL Server|Description|  
|-------------------------------------|-----------------|  
|**Pages de base de données**|Indique le nombre de pages dans le pool de mémoires tampons de ce nœud avec le contenu de la base de données.|  
|**Espérance de vie d'une page**|Indique le nombre minimal de secondes pendant lesquelles une page est conservée dans le pool de mémoires tampons sur ce nœud sans références.|  
|**Recherches de pages de nœud local/s**|Indique le nombre de demandes de recherches à partir de ce nœud qui ont été satisfaites par ce nœud.|  
|**Recherches de pages de nœud distant/s**|Indique le nombre de demandes de recherches à partir de ce nœud qui ont été satisfaites par d'autres nœuds.|  
  
 Si vous exécutez SQL Server sur du matériel non-NUMA, les compteurs des objets **Nœud de tampon** et **Gestionnaire de tampons** doivent correspondre.  
  
 Sur du matériel NUMA, les sommes des compteurs respectifs de tous les objets **Nœud de tampon** doivent correspondre aux sommes de leurs objets **Gestionnaire de tampons**équivalents.  
  
> [!NOTE]  
>  Il est possible que les valeurs et les sommes des compteurs ne correspondent pas exactement en raison de la nature dynamique des compteurs et de la précision d'échantillonnage.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server, objet Gestionnaire de tampons](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [Mémoire du serveur (option de configuration de serveur)](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  
