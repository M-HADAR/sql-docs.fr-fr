---
title: sp_change_agent_parameter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_agent_parameter_TSQL
- sp_change_agent_parameter
helpviewer_keywords:
- sp_change_agent_parameter
ms.assetid: f1fbecc7-e64f-405c-8067-6b38c1f3c0a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd737be5a1e71e46750f6c80fd68ad254cb6436f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68768940"
---
# <a name="sp_change_agent_parameter-transact-sql"></a>sp_change_agent_parameter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Modifie un paramètre d’un profil d’agent de réplication stocké dans la table système [MSagent_parameters](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) . Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de distribution sur lequel l'agent est en cours d'exécution.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_change_agent_parameter [ @profile_id= ] profile_id, [ @parameter_name= ] 'parameter_name', [ @parameter_value= ] 'parameter_value'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_id = ] profile_id,`ID du profil. *profile_id* est de **type int**, sans valeur par défaut.  
  
`[ @parameter_name = ] 'parameter_name'`Nom du paramètre. *parameter_name* est de **type sysname**, sans valeur par défaut. Pour les profils système, les paramètres modifiables dépendent du type d'Agent. Pour savoir quel type d’agent ce *profile_id* représente, localisez la colonne *profile_id* dans la table **Msagent_profiles** et notez la valeur *agent_type* .  
  
> [!NOTE]  
>  Si un paramètre est pris en charge pour un *agent_type*donné, mais qu’il n’a pas été défini dans le profil d’agent, une erreur est retournée. Pour ajouter un paramètre à un profil d’agent, vous devez exécuter [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 Pour une agent d’instantané (*agent_type*=**1**), si elle est définie dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **70Subscribers**  
  
-   **BcpBatchSize**  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxNetworkOptimization**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **Taille paquet**  
  
-   **QueryTimeout**  
  
-   **StartQueueTimeout**  
  
-   **UsePerArticleContentsView**  
  
 Pour un agent de lecture du journal (*agent_type*=**2**), s’il est défini dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MessageInterval**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **Taille paquet**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ReadBatchSize**  
  
-   **ReadBatchThreshold**  
  
 Pour une agent de distribution (*agent_type*=**3**), si elle est définie dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **BcpBatchSize**  
  
-   **CommitBatchSize**  
  
-   **CommitBatchThreshold**  
  
-   **FileTransferType**  
  
-   **HistoryVerboseLevel**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDeliveredTransactions**  
  
-   **MessageInterval**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **Taille paquet**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **QuotedIdentifier**  
  
-   **SkipErrors**  
  
-   **TransactionsPerHistory**  
  
 Pour une agent de fusion (*agent_type*=**4**), si elle est définie dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **AltSnapshotFolder au maximum**  
  
-   **BcpBatchSize**  
  
-   **ChangesPerHistory**  
  
-   **DestThreads**  
  
-   **DownloadGenerationsPerBatch**  
  
-   **DownloadReadChangesPerBatch**  
  
-   **DownloadWriteChangesPerBatch**  
  
-   **DynamicSnapshotLocation**  
  
-   **ExchangeType**  
  
-   **FastRowCount**  
  
-   **FileTransferType**  
  
-   **GenerationChangeThreshold**  
  
-   **HistoryVerboseLevel**  
  
-   **InputMessageFile**  
  
-   **InteractiveResolution**  
  
-   **InterruptOnMessagePattern**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDownloadChanges**  
  
-   **MaxUploadChanges**  
  
-   **MetadataRetentionCleanup**  
  
-   **NumDeadlockRetries**  
  
-   **Output**  
  
-   **OutputMessageFile**  
  
-   **OutputVerboseLevel**  
  
-   **Taille paquet**  
  
-   **ParallelUploadDownload**  
  
-   **PauseOnMessagePattern**  
  
-   **PauseTime**  
  
-   **PollingInterval**  
  
-   **ProcessMessagesAtPublisher**  
  
-   **ProcessMessagesAtSubscriber**  
  
-   **QueryTimeout**  
  
-   **QueueSizeMultiplier**  
  
-   **SrcThreads**  
  
-   **StartQueueTimeout**  
  
-   **SyncToAlternate**  
  
-   **UploadGenerationsPerBatch**  
  
-   **UploadReadChangesPerBatch**  
  
-   **UploadWriteChangesPerBatch**  
  
-   **UseInprocLoader**  
  
-   **Valider**  
  
-   **ValidateInterval**  
  
 Pour une agent de lecture de la file d’attente (*agent_type*=**9**), si elle est définie dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ResolverState**  
  
-   **SQLQueueMode**  
  
 Pour voir quels paramètres ont été définis pour un profil donné, exécutez **sp_help_agent_profile** et notez le *profile_name* associé à la *profile_id*. Avec la *profile_id*appropriée, exécutez à présent **sp_help_agent_parameters** à l’aide de ce *profile_id* pour voir les paramètres associés au profil. Les paramètres peuvent être ajoutés à un profil en exécutant [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
`[ @parameter_value = ] 'parameter_value'`Nouvelle valeur du paramètre. *parameter_value* est de type **nvarchar (255)**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_change_agent_parameter** est utilisé dans tous les types de réplications.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_change_agent_parameter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Profils de l’agent de réplication](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replication Log Reader Agent](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agent de lecture de la file d'attente de réplication](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Agent d’instantané de réplication](../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
