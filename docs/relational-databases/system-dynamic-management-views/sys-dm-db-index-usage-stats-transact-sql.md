---
title: sys. dm_db_index_usage_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_index_usage_stats_TSQL
- sys.dm_db_index_usage_stats
- sys.dm_db_index_usage_stats_TSQL
- dm_db_index_usage_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_usage_stats dynamic management view
ms.assetid: d06a001f-0f72-4679-bc2f-66fff7958b86
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 491ec37d96cf6bdb2b074efb42a54406beb1fd20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264405"
---
# <a name="sysdm_db_index_usage_stats-transact-sql"></a>sys.dm_db_index_usage_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie le nombre des différents types d'opérations d'index et l'heure d'exécution de chaque opération.  
  
 Dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], les vues de gestion dynamique ne peuvent pas exposer des informations qui ont un impact sur la relation contenant-contenu de la base de données, ou exposer des informations concernant d'autres bases de données auxquelles l'utilisateur a accès. Pour éviter d’exposer ces informations, chaque ligne qui contient des données qui n’appartiennent pas au locataire connecté est filtrée.  
  
> [!NOTE]  
>  **sys. dm_db_index_usage_stats** ne retourne pas d’informations sur les index optimisés en mémoire. Pour plus d’informations sur l’utilisation des index optimisés en mémoire, consultez [sys. dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md).  
  
> [!NOTE]  
>  Pour appeler cette vue à [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] partir [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]de ou, utilisez **sys. dm_pdw_nodes_db_index_usage_stats**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**smallint**|ID de la base de données sur laquelle la table ou la vue est définie.|  
|**object_id**|**int**|ID de la table ou de la vue sur laquelle l'index est défini.|  
|**index_id**|**int**|Identificateur de l'index.|  
|**user_seeks**|**bigint**|Nombre de recherches par requête utilisateur.|  
|**user_scans**|**bigint**|Nombre d’analyses par requête utilisateur qui n’utilisaient pas le prédicat « SEEK ».|  
|**user_lookups**|**bigint**|Nombre de recherches de signets par les requêtes utilisateur.|  
|**user_updates**|**bigint**|Nombre de mises à jour par requête utilisateur. Cela comprend l’insertion, la suppression et les mises à jour qui représentent le nombre d’opérations effectuées, pas les lignes réelles affectées. Par exemple, si vous supprimez 1000 lignes dans une instruction, ce nombre est incrémenté de 1|  
|**last_user_seek**|**DATETIME**|Heure de la dernière recherche utilisateur.|  
|**last_user_scan**|**DATETIME**|Heure de la dernière analyse utilisateur.|  
|**last_user_lookup**|**DATETIME**|Heure de la dernière recherche utilisateur.|  
|**last_user_update**|**DATETIME**|Heure de la dernière mise à jour utilisateur.|  
|**system_seeks**|**bigint**|Nombre de recherches par requête système.|  
|**system_scans**|**bigint**|Nombre d'analyses par requête système.|  
|**system_lookups**|**bigint**|Nombre de recherches par requête système.|  
|**system_updates**|**bigint**|Nombre de mises à jour par requête système.|  
|**last_system_seek**|**DATETIME**|Heure de la dernière recherche système.|  
|**last_system_scan**|**DATETIME**|Heure de la dernière analyse système.|  
|**last_system_lookup**|**DATETIME**|Heure de la dernière recherche système.|  
|**last_system_update**|**DATETIME**|Heure de la dernière mise à jour système.|  
|pdw_node_id|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="remarks"></a>Notes  
 Chaque recherche, analyse ou mise à jour individuelle sur l'index spécifié par l'exécution d'une requête, est comptée comme utilisation de cet index et augmente d'une unité le compteur correspondant dans cette vue. Les informations sont renvoyées pour les opérations générées par des requêtes soumises par l'utilisateur et pour les opérations générées par des requêtes internes, telles que des analyses pour le recueil de statistiques.  
  
 Le compteur **user_updates** indique le niveau de maintenance de l'index dû à des opérations d'insertion, de mise à jour ou de suppression sur la table ou la vue sous-jacente. Vous pouvez utiliser cette vue pour déterminer les index qui ne sont que peu utilisés par vos applications. Vous pouvez également l'utiliser pour déterminer les index qui entraînent une surcharge à cause des traitements de maintenance. Vous envisagerez peut-être de supprimer les index qui entraînent une surcharge de maintenance mais qui ne sont pas utilisés pour des requêtes, ou peu fréquemment.  
  
 Les compteurs sont initialisés à zéro au démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER). En outre, si une base de données est détachée ou arrêtée (par exemple parce qu'AUTO_CLOSE a la valeur ON), toutes les lignes associées à la base de données sont supprimées.  
  
 Quand un index est utilisé, une ligne est ajoutée à **sys.dm_db_index_usage_stats** si une ligne n'existe pas déjà pour l'index. Quand la ligne est ajoutée, ses compteurs sont à zéro.  
  
 Pendant la mise [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]niveau vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], ou, les entrées dans sys. dm_db_index_usage_stats sont supprimées. À partir [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]de, les entrées sont conservées telles qu' [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]elles étaient avant.  
  
## <a name="permissions"></a>Autorisations  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .  
  
## <a name="see-also"></a>Voir aussi  

 [Fonctions et vues de gestion dynamique liées aux index &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys. dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  


