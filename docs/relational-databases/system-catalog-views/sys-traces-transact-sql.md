---
title: sys. traces (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- traces
- sys.traces_TSQL
- sys.traces
- traces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.traces catalog view
ms.assetid: 4a03be22-b7da-4e2a-97ff-94bed890a620
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 147c080df688ff02d133e725b1ac310439a68eb8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68126676"
---
# <a name="systraces-transact-sql"></a>sys.traces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  L’affichage catalogue **sys. traces** contient les traces en cours d’exécution sur le système. Cette vue est destinée à remplacer la fonction **fn_trace_getinfo** .  
  
 Pour obtenir la liste complète des événements de trace pris en charge, consultez [SQL Server référence](../../relational-databases/event-classes/sql-server-event-class-reference.md)de la classe d’événements.  
  
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt les affichages catalogue des événements étendus.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**identifi**|**int**|ID de la trace.|  
|**statu**|**int**|État de la trace :<br /><br /> 0 = arrêtée<br /><br /> 1 = en cours d’exécution|  
|**d**|**nvarchar(260)**|Chemin du fichier de trace Cette valeur est NULL lorsque la trace représente une trace d'ensemble de lignes.|  
|**max_size**|**bigint**|Limite de la taille de fichier de trace maximale en mégaoctets (Mo). Cette valeur est NULL lorsque la trace représente une trace d'ensemble de lignes.|  
|**stop_time**|**DATETIME**|Heure d'arrêt de trace d'exécution.|  
|**max_files**|**int**|Nombre maximal de fichiers de substitution. Cette valeur est NULL lorsque le nombre maximal n'est pas défini.|  
|**is_rowset**|**bit**|1 = trace d'ensemble de lignes.|  
|**is_rollover**|**bit**|1 = l'option de substitution est activée.|  
|**is_shutdown**|**bit**|1 = l'option d'arrêt est activée.|  
|**is_default**|**bit**|1 = trace par défaut.|  
|**buffer_count**|**int**|Nombre de tampons en mémoire utilisés par la trace.|  
|**buffer_size**|**int**|Taille de chaque tampon (Ko).|  
|**file_position**|**bigint**|Dernière position d'un fichier de trace. Cette valeur est NULL lorsque la trace représente une trace d'ensemble de lignes.|  
|**reader_spid**|**int**|ID de session de lecteur de trace d'ensemble de lignes. Cette valeur est NULL lorsque la trace est un fichier de trace.|  
|**start_time**|**DATETIME**|Heure de début de trace.|  
|**last_event_time**|**DATETIME**|Heure du dernier déclenchement d'événement.|  
|**event_count**|**bigint**|Nombre total d'événements qui se sont produits.|  
|**dropped_event_count**|**int**|Nombre total d'événements supprimés.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys. trace_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys. trace_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys. trace_event_bindings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys. trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
