---
title: sys. dm_pdw_diag_processing_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8b880820ac633402d1d3cdd679b16a54d1be358e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899540"
---
# <a name="sysdm_pdw_diag_processing_stats-transact-sql"></a>sys. dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Affiche des informations relatives à tous les événements de diagnostic internes qui peuvent être incorporés dans les sessions de diagnostic définies par l’administrateur. Interrogez cette vue pour comprendre les statistiques sous-jacentes aux sous-systèmes de diagnostic et d’événement qui pilotent le remplissage de toutes les autres vues DMV. Il existe un groupe de files d’attente pour chaque processus sur chaque nœud.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Nœud d’appareil dont ce journal provient.|  
|**process_id**|**int**|Identificateur du processus en cours d’exécution de cette statistique.|  
|**target_name**|**nvarchar(255)**|Nom de la file d’attente.|  
|**queue_size**|**int**|Nombre d’éléments dans la file d’attente de traitement. La taille de la file d’attente est généralement 0. Un nombre positif indique que le système est soumis à une contrainte et qu’il génère des travaux en souffrance des événements. Un nombre positif dans les autres colonnes signifie que le système est endommagé pour cette file d’attente et toutes les vues DMV associées.|  
|**lost_events_count**|**bigint**|Nombre d’événements perdus.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
