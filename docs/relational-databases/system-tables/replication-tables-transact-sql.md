---
title: Tables de réplication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], replication
- replication [SQL Server], system tables
ms.assetid: 5696ee73-5d7c-4f26-b7ee-6831c9c3edf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3dc89ce68529212246d85bdbafa8d9487b77a067
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67910235"
---
# <a name="replication-tables-transact-sql"></a>Tables de réplication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Les tables système de réplication prennent en charge une topologie de réplication. Lorsqu'une base de données utilisateur est configurée en tant que serveur de publication ou en tant qu'abonné, la réplication ajoute des tables système à la base de données. Ces tables sont supprimées lorsqu'une base de données utilisateur est supprimée d'une topologie de réplication. Pour connaître les règles générales relatives à l’utilisation des tables système, consultez [tables système &#40;&#41;Transact-SQL ](system-tables-transact-sql.md).  
  
## <a name="replication-tables"></a>Tables de réplication  
 La liste suivante répertorie les tables système utilisées par la réplication. Elles sont classées par base de données.  
  
### <a name="replication-tables-in-the-master-database"></a>Tables de réplication dans la base de données master  
  
|||  
|-|-|  
|[MSreplication_options &#40;Transact-SQL&#41;](msreplication-options-transact-sql.md)||  
| &nbsp; | &nbsp; |
 
### <a name="replication-tables-in-the-msdb-database"></a>Tables de réplication de la base de données msdb  

|||  
|-|-|  
|[MSagentparameterlist](msagentparameterlist-transact-sql.md)|[MSdbms](msdbms-transact-sql.md) |  
|[MSagent_parameters](msagent-parameters-transact-sql.md)    |[MSdbms_datatype](msdbms-datatype-transact-sql.md)|
|[MSagent_profiles](msagent-profiles-transact-sql.md)        |[MSdbms_datatype_mapping](msdbms-datatype-mapping-transact-sql.md)|
|[MSdistpublishers](msdistpublishers-transact-sql.md)        |[MSdbms_map](msdbms-map-transact-sql.md)|
|[MSdistributiondbs](msdistributiondbs-transact-sql.md)      |[MSreplmonthresholdmetrics](msreplmonthresholdmetrics-transact-sql.md)|
|[MSdistributor](msdistributor-transact-sql.md)              |[sysreplicationalerts](sysreplicationalerts-transact-sql.md)|
| &nbsp; | &nbsp; |

### <a name="replication-tables-in-the-distribution-database"></a>Tables de réplication dans la base de données de distribution  

|||  
|-|-|  
|[MSarticles](msarticles-transact-sql.md)                          |[MSrepl_backup_lsns](msrepl-backup-lsns-transact-sql.md)|
|[MScached_peer_lsns](mscached-peer-lsns-transact-sql.md)          |[MSrepl_commands](msrepl-commands-transact-sql.md)
|[MSdistribution_agents](msdistribution-agents-transact-sql.md)    |[MSrepl_errors](msrepl-errors-transact-sql.md)|
|[MSdistribution_history](msdistribution-history-transact-sql.md)  |[MSrepl_identity_range](msrepl-identity-range-transact-sql.md) |
|[MSlogreader_agents](mslogreader-agents-transact-sql.md)          |[MSrepl_originators](msrepl-originators-transact-sql.md)|
|[MSlogreader_history](mslogreader-history-transact-sql.md)        |[MSrepl_transactions](msrepl-transactions-transact-sql.md)      |
|[MSmerge_agents](msmerge-agents-transact-sql.md)                  |[MSrepl_version](msrepl-version-transact-sql.md)|  
|[MSmerge_articlehistory](msmerge-articlehistory-transact-sql.md)  |[MSreplication_monitordata](msreplication-monitordata-transact-sql.md)|
|[MSmerge_history](msmerge-history-transact-sql.md)                |[MSsnapshot_agents](mssnapshot-agents-transact-sql.md)
|[MSmerge_identity_range_allocations](msmerge-identity-range-allocations-transact-sql.md)|[MSsnapshot_history](mssnapshot-history-transact-sql.md)
|[MSmerge_sessions](msmerge-sessions-transact-sql.md)              |[MSsubscriber_info](mssubscriber-info-transact-sql.md) |
|[MSmerge_subscriptions](msmerge-subscriptions-transact-sql.md)    |[MSsubscriber_schedule](mssubscriber-schedule-transact-sql.md) |
|[MSpublication_access](mspublication-access-transact-sql.md)      |[MSsubscriptions](mssubscriptions-transact-sql.md)|
|[MSpublications](mspublications-transact-sql.md)                  |[MSsubscription_properties](mssubscription-properties-transact-sql.md)|
|[MSpublicationthresholds](mspublicationthresholds-transact-sql.md)|[MSsync_states](mssync-states-transact-sql.md) | 
|[MSpublisher_databases](mspublisher-databases-transact-sql.md)    |[MStracer_history](mstracer-history-transact-sql.md)|  
|[MSqreader_agents](msqreader-agents-transact-sql.md)              |[MStracer_tokens](mstracer-tokens-transact-sql.md)| 
|[MSqreader_history](msqreader-history-transact-sql.md)            ||
| &nbsp; | &nbsp; |
  
 Ces tables de la base de données de distribution sont utilisées pour la réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des données à partir d’un serveur de publication non-. Pour plus d’informations, consultez [éditeurs non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-publishers.md).  
  
|||  
|-|-|  
|[IHarticles](iharticles-transact-sql.md)                                    |[IHpublishercolumnindexes](ihpublishercolumnindexes-transact-sql.md)|
|[IHcolumns](ihcolumns-transact-sql.md)                                      |[IHpublishercolumns](ihpublishercolumns-transact-sql.md)|
|[IHconstrainttypes](ihconstrainttypes-transact-sql.md)                      |[IHpublisherconstraints](ihpublisherconstraints-transact-sql.md)|
|[IHindextypes](ihindextypes-transact-sql.md)                                |[IHpublisherindexes](ihpublisherindexes-transact-sql.md)|
|[IHindextypes](ihindextypes-transact-sql.md)                                |[IHpublishers](ihpublishers-transact-sql.md)|
|[IHpublications](ihpublications-transact-sql.md)                            |[IHpublishertables](ihpublishertables-transact-sql.md)|
|[IHpublishercolumnconstraints](ihpublishercolumnconstraints-transact-sql.md)|[IHsubscriptions](ihsubscriptions-transact-sql.md)|
| &nbsp; | &nbsp; | 
 

### <a name="replication-tables-in-the-publication-database"></a>Tables de réplication dans la base de données de publication  
 
|||  
|-|-|  
|[>_\<\<de la table de conflict_ de schéma>](conflict-schema-table-transact-sql.md)       |[MSpeer_request](mspeer-request-transact-sql.md)|
|[MSdynamicsnapshotjobs](msdynamicsnapshotjobs-transact-sql.md)             |[MSpeer_response](mspeer-response-transact-sql.md)|
|[MSdynamicsnapshotviews](msdynamicsnapshotviews-transact-sql.md)           |[MSpeer_topologyrequest](mspeer-topologyrequest-transact-sql.md)|  
|[MSmerge_altsyncpartners](msmerge-altsyncpartners-transact-sql.md)         |[MSpeer_topologyresponse](mspeer-topologyresponse-transact-sql.md)|  
|[MSmerge_conflicts_info](msmerge-conflicts-info-transact-sql.md)           |[MSpub_identity_range](mspub-identity-range-transact-sql.md)|  
|[MSmerge_contents](msmerge-contents-transact-sql.md)                       |[MSrepl_identity_range](msrepl-identity-range-transact-sql.md)| 
|[MSmerge_current_partition_mappings](msmerge-current-partition-mappings.md)|[sysarticlecolumns](sysarticlecolumns-transact-sql.md)|  
|[MSmerge_dynamic_snapshots](msmerge-dynamic-snapshots-transact-sql.md)     |[sysarticles](sysarticles-transact-sql.md)|  
|[MSmerge_errorlineage](msmerge-errorlineage-transact-sql.md)               |[sysarticleupdates](sysarticleupdates-transact-sql.md)|  
|[MSmerge_generation_partition_mappings](msmerge-generation-partition-mappings-transact-sql.md)|[sysmergearticlecolumns](sysmergearticlecolumns-transact-sql.md)|  
|[MSmerge_genhistory](msmerge-genhistory-transact-sql.md)                   |[sysmergearticles](sysmergearticles-transact-sql.md)|  
|[MSmerge_identity_range](msmerge-identity-range-transact-sql.md)           |[sysmergepartitioninfo](sysmergepartitioninfo-transact-sql.md)|  
|[MSmerge_metadataaction_request](msmerge-metadataaction-request-transact-sql.md)|[sysmergepublications](sysmergepublications-transact-sql.md)|  
|[MSmerge_partition_groups](msmerge-partition-groups-transact-sql.md)       |[sysmergeschemaarticles](sysmergeschemaarticles-transact-sql.md)|  
|[MSmerge_past_partition_mappings](msmerge-past-partition-mappings-transact-sql.md)|[sysmergeschemachange](sysmergeschemachange-transact-sql.md)|  
|[MSmerge_replinfo](msmerge-replinfo-transact-sql.md)                       |[sysmergesubscriptions](sysmergesubscriptions-transact-sql.md)|  
|[MSmerge_settingshistory](msmerge-settingshistory-transact-sql.md)         |[sysmergesubsetfilters](sysmergesubsetfilters-transact-sql.md)|  
|[MSmerge_tombstone](msmerge-tombstone-transact-sql.md)                     |[syspublications](syspublications-transact-sql.md)|  
|[MSpeer_conflictdetectionconfigrequest](mspeer-conflictdetectionconfigrequest-transact-sql.md)|[sysschemaarticles](sysschemaarticles-transact-sql.md)|  
|[MSpeer_conflictdetectionconfigresponse](mspeer-conflictdetectionconfigresponse-transact-sql.md)|[syssubscriptions](syssubscriptions-transact-sql.md)|  
|[MSpeer_lsns](mspeer-lsns-transact-sql.md)                                  |[systranschemas](../../relational-databases/system-views/systranschemas-transact-sql.md)| 
|[MSpeer_originatorid_history](mspeer-originatorid-history-transact-sql.md)  | | 
| &nbsp; | &nbsp; | 


### <a name="replication-tables-in-the-subscription-database"></a>Tables de réplication dans la base de données d'abonnement  
 
|||  
|-|-|  
|[MSdynamicsnapshotjobs](msdynamicsnapshotjobs-transact-sql.md)                   |[MSmerge_tombstone](msmerge-tombstone-transact-sql.md)|  
|[MSdynamicsnapshotviews](msdynamicsnapshotviews-transact-sql.md)                 |[MSpeer_lsns](mspeer-lsns-transact-sql.md)|  
|[MSmerge_altsyncpartners](msmerge-altsyncpartners-transact-sql.md)               |[MSrepl_identity_range](msrepl-identity-range-transact-sql.md)|  
|[MSmerge_conflicts_info](msmerge-conflicts-info-transact-sql.md)                 |[MSrepl_queuedtraninfo](msrepl-queuedtraninfo-transact-sql.md)|  
|[MSmerge_contents](msmerge-contents-transact-sql.md)                             |[MSreplication_objects](msreplication-objects-transact-sql.md)|
|[MSmerge_current_partition_mappings](msmerge-current-partition-mappings.md)      |[MSreplication_subscriptions](msreplication-subscriptions-transact-sql.md)|
|[MSmerge_dynamic_snapshots](msmerge-dynamic-snapshots-transact-sql.md)           |[MSsnapshotdeliveryprogress](mssnapshotdeliveryprogress-transact-sql.md)|  
|[MSmerge_errorlineage](msmerge-errorlineage-transact-sql.md)                     |[MSsubscription_properties](mssubscription-properties-transact-sql.md)|  
|[MSmerge_generation_partition_mappings](msmerge-generation-partition-mappings-transact-sql.md)|[sysmergearticles](sysmergearticles-transact-sql.md)|  
|[MSmerge_genhistory](msmerge-genhistory-transact-sql.md)                         |[sysmergepartitioninfo](sysmergepartitioninfo-transact-sql.md)|  
|[MSmerge_identity_range](msmerge-identity-range-transact-sql.md)                 |[sysmergepublications](sysmergepublications-transact-sql.md)|  
|[MSmerge_metadataaction_request](msmerge-metadataaction-request-transact-sql.md)  |[sysmergeschemaarticles](sysmergeschemaarticles-transact-sql.md)|  
|[MSmerge_partition_groups](msmerge-partition-groups-transact-sql.md)             |[sysmergeschemachange](sysmergeschemachange-transact-sql.md)|  
|[MSmerge_past_partition_mappings](msmerge-past-partition-mappings-transact-sql.md)|[sysmergesubscriptions](sysmergesubscriptions-transact-sql.md)|  
|[MSmerge_replinfo](msmerge-replinfo-transact-sql.md)                             |[sysmergesubsetfilters](sysmergesubsetfilters-transact-sql.md)|  
|[MSmerge_settingshistory](msmerge-settingshistory-transact-sql.md)               |[systranschemas](../../relational-databases/system-views/systranschemas-transact-sql.md)| 
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Voir aussi  
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Désactiver la publication et la distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
