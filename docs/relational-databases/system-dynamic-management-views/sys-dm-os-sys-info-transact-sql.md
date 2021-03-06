---
title: sys. dm_os_sys_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_sys_info_TSQL
- dm_os_sys_info
- dm_os_sys_info_TSQL
- sys.dm_os_sys_info
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_info dynamic management view
- time [SQL Server], instance started
- starting time
ms.assetid: 20f6bc9c-839a-4fa4-b3f3-a6c47d1b69af
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ddc70ef475eb5e4ddc91095ce251c383ca4cdbf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73983159"
---
# <a name="sysdm_os_sys_info-transact-sql"></a>sys.dm_os_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Retourne un ensemble diversifié d'informations utiles sur l'ordinateur et sur les ressources dont dispose et que consomme [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  
  
> **Remarque :** Pour appeler cette valeur [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] à [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]partir de ou, utilisez le nom **sys. dm_pdw_nodes_os_sys_info**.  
  
|Nom de la colonne|Type de données|Description et remarques spécifiques à la version |  
|-----------------|---------------|-----------------|  
|**cpu_ticks**|**bigint**|Spécifie le nombre de cycles UC actuel. Les cycles de l'UC sont fournis par le compteur RDTSC du processeur. Il s'agit d'une valeur à croissance monotone. N'accepte pas la valeur NULL.|  
|**ms_ticks**|**bigint**|Spécifie le nombre de millisecondes écoulées depuis le démarrage de l'ordinateur. N'accepte pas la valeur NULL.|  
|**cpu_count**|**int**|Spécifie le nombre d'UC logiques dans le système. N'accepte pas la valeur NULL.|  
|**hyperthread_ratio**|**int**|Spécifie le rapport entre le nombre de noyaux logiques et le nombre de noyaux physiques exposés par un package de processeurs physiques. N'accepte pas la valeur NULL.|  
|**physical_memory_in_bytes**|**bigint**|**S’applique à :** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu' [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]à.<br /><br /> Spécifie la quantité totale de mémoire physique sur l'ordinateur. N'accepte pas la valeur NULL.|  
|**physical_memory_kb**|**bigint**|**S’applique à :** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Spécifie la quantité totale de mémoire physique sur l'ordinateur. N'accepte pas la valeur NULL.|  
|**virtual_memory_in_bytes**|**bigint**|**S’applique à :** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu' [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]à.<br /><br /> Quantité de mémoire virtuelle dont dispose le processus en mode utilisateur. Cette information peut être utilisée pour déterminer si SQL Server a été démarré à l'aide d'un commutateur 3-GB.|  
|**virtual_memory_kb**|**bigint**|**S’applique à :** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Spécifie la quantité totale d'espace d'adressage virtuel disponible au processus en mode utilisateur. N'accepte pas la valeur NULL.|  
|**bpool_commited**|**int**|**S’applique à :** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu' [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]à.<br /><br /> Représente la mémoire validée, en kilo-octet (Ko), dans le gestionnaire de mémoire. Elle ne comprend pas la mémoire réservée dans le gestionnaire de mémoire. N'accepte pas la valeur NULL.|  
|**committed_kb**|**int**|**S’applique à :** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Représente la mémoire validée, en kilo-octet (Ko), dans le gestionnaire de mémoire. Elle ne comprend pas la mémoire réservée dans le gestionnaire de mémoire. N'accepte pas la valeur NULL.|  
|**bpool_commit_target**|**int**|**S’applique à :** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu' [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]à.<br /><br /> Représente la quantité de mémoire, en kilo-octet (KB), qui peut être consommée par le gestionnaire de mémoire SQL Server.|  
|**committed_target_kb**|**int**|**S’applique à :** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Représente la quantité de mémoire, en kilo-octet (KB), qui peut être consommée par le gestionnaire de mémoire SQL Server. Le montant cible est calculé à l'aide de diverses entrées, telles que :<br /><br /> -état actuel du système, y compris sa charge<br /><br /> -mémoire demandée par les processus en cours<br /><br /> -la quantité de mémoire installée sur l’ordinateur<br /><br /> -paramètres de configuration<br /><br /> Si **committed_target_kb** est supérieure à **committed_kb**, le gestionnaire de mémoire essaiera d’obtenir de la mémoire supplémentaire. Si **committed_target_kb** est inférieure à **committed_kb**, le gestionnaire de mémoire tente de réduire la quantité de mémoire allouée. Le **committed_target_kb** comprend toujours le vol et la mémoire réservée. N'accepte pas la valeur NULL.|  
|**bpool_visible**|**int**|**S’applique à :** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu' [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]à.<br /><br /> Nombre de tampons de 8 Ko dans le pool de mémoires tampons directement accessibles dans l'espace d'adressage virtuel de processus. Si vous n'utilisez pas Address Windowing Extensions (AWE), si le pool de mémoires tampons a obtenu sa cible de mémoire (bpool_committed = bpool_commit_target), la valeur de bpool_visible est égale à la valeur de bpool_committed. Lorsque vous utilisez AWE sur une version 32 bits de SQL Server, bpool_visible représente la taille de la fenêtre de mappage AWE utilisée pour accéder à la mémoire physique allouée par le pool de mémoires tampons. La taille de cette fenêtre de mappage étant tributaire de l'espace d'adressage de processus, la quantité visible sera inférieure à la quantité validée et peut être davantage réduite si les composants internes consomment de la mémoire à des fins qui sont sans rapport avec les pages de base de données. Si la valeur de bpool_visible est trop basse, vous pouvez obtenir des messages indiquant une insuffisance de mémoire.|  
|**visible_target_kb**|**int**|**S’applique à :** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Est identique à **committed_target_kb**. N'accepte pas la valeur NULL.|  
|**stack_size_in_bytes**|**int**|Spécifie la taille de la pile d'appels pour chaque thread créé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|**os_quantum**|**bigint**|Représente le quantum associé à une tâche non préemptive, mesuré en millisecondes. Quantum (en secondes) = **os_quantum** /fréquence d’horloge du processeur. N'accepte pas la valeur NULL.|  
|**os_error_mode**|**int**|Spécifie le mode d'erreur pour le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|**os_priority_class**|**int**|Spécifie la classe de priorité du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Autorise la valeur Null.<br /><br /> 32 = Standard (le journal des erreurs indiquera qu'[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commence à la priorité de base normale (=7).)<br /><br /> 128 = Élevé (le journal des erreurs indiquera qu'[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute à la priorité de base supérieure.  (=13).)<br /><br /> Pour plus d’informations, consultez [Configurer l’option de configuration du serveur priority boost](../../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md).|  
|**max_workers_count**|**int**|Représente le nombre maximum de processus de travail pouvant être créés. N'accepte pas la valeur NULL.|  
|**scheduler_count**|**int**|Représente le nombre de planificateurs utilisateur configurés dans le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|**scheduler_total_count**|**int**|Représente le nombre total de planificateurs dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|**deadlock_monitor_serial_number**|**int**|Spécifie l'identificateur de la séquence en cours du moniteur d'interblocage. N'accepte pas la valeur NULL.|  
|**sqlserver_start_time_ms_ticks**|**bigint**|Représente le nombre **ms_tick** lors [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du dernier démarrage de. À comparer à la colonne ms_ticks actuelle. N'accepte pas la valeur NULL.|  
|**sqlserver_start_time**|**DATETIME**|Spécifie la date et l'heure du dernier démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|**affinity_type**|**int**|**S’applique à :** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et versions ultérieures.<br /><br /> Spécifie le type d'affinité de processus UC serveur en cours d'utilisation. N'accepte pas la valeur NULL. Pour plus d’informations, consultez [ALTER Server CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md).<br /><br /> 1 = MANUAL<br /><br /> 2 = AUTO|  
|**affinity_type_desc**|**varchar(60)**|**S’applique à :** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et versions ultérieures.<br /><br /> Décrit la colonne **affinity_type** . N'accepte pas la valeur NULL.<br /><br /> MANUAL = l'affinité a été définie pour au moins une UC.<br /><br /> AUTO = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut déplacer librement des threads entre des UC.|  
|**process_kernel_time_ms**|**bigint**|**S’applique à :** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et versions ultérieures.<br /><br /> Durée totale en millisecondes passée par tous les threads [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode noyau. Cette valeur peut être plus grande qu'une horloge de processeur unique parce qu'elle inclut l'heure pour tous les processeurs sur le serveur. N'accepte pas la valeur NULL.|  
|**process_user_time_ms**|**bigint**|**S’applique à :** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et versions ultérieures.<br /><br /> Durée totale en millisecondes passée par tous les threads [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode utilisateur. Cette valeur peut être plus grande qu'une horloge de processeur unique parce qu'elle inclut l'heure pour tous les processeurs sur le serveur. N'accepte pas la valeur NULL.|  
|**time_source**|**int**|**S’applique à :** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et versions ultérieures.<br /><br /> Indique l'API que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise pour récupérer la durée totale d'exécution. N'accepte pas la valeur NULL.<br /><br /> 0 = QUERY_PERFORMANCE_COUNTER<br /><br /> 1 = MULTIMEDIA_TIMER|  
|**time_source_desc**|**nvarchar (60)**|**S’applique à :** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et versions ultérieures.<br /><br /> Décrit la colonne **time_source** . N'accepte pas la valeur NULL.<br /><br /> QUERY_PERFORMANCE_COUNTER = l’API [QueryPerformanceCounter](https://go.microsoft.com/fwlink/?LinkId=163095) récupère le temps horloge.<br /><br /> MULTIMEDIA_TIMER = l’API de [minuteur multimédia](https://go.microsoft.com/fwlink/?LinkId=163094) qui récupère le temps horloge.|  
|**virtual_machine_type**|**int**|**S’applique à :** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et versions ultérieures.<br /><br /> Indique si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute dans un environnement virtualisé.  N'accepte pas la valeur NULL.<br /><br /> 0 = AUCUN<br /><br /> 1 = HYPERVISOR<br /><br /> 2 = OTHER|  
|**virtual_machine_type_desc**|**nvarchar (60)**|**S’applique à :** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] et versions ultérieures.<br /><br /> Décrit la colonne **virtual_machine_type** . N'accepte pas la valeur NULL.<br /><br /> NONE = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas exécuté sur une machine virtuelle.<br /><br /> Hyperviseur = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute à l’intérieur d’un ordinateur virtuel hébergé par un système d’exploitation exécutant hyperviseur (un système d’exploitation hôte qui utilise la virtualisation d’assistance matérielle).<br /><br /> OTHER = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute à l’intérieur d’un ordinateur virtuel hébergé par un système d’exploitation qui n’utilise pas l’assistant matériel tel que Microsoft Virtual PC.|  
|**softnuma_configuration**|**int**|**S’applique à :** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et versions ultérieures.<br /><br /> Spécifie la façon dont les nœuds NUMA sont configurés. N'accepte pas la valeur NULL.<br /><br /> 0 = désactivé indique la valeur par défaut du matériel<br /><br /> 1 = soft-NUMA automatisé<br /><br /> 2 = soft-NUMA manuel via le registre|  
|**softnuma_configuration_desc**|**nvarchar (60)**|**S’applique à :** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et versions ultérieures.<br /><br /> OFF = la fonctionnalité soft-NUMA est désactivée<br /><br /> ON = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] détermine automatiquement la taille des nœuds NUMA pour soft-NUMA<br /><br /> Manuel = soft-NUMA configuré manuellement|
|**process_physical_affinity**|**nvarchar (3072)** |**S’applique à :** À partir [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]de.<br /><br />Des informations encore à venir. |
|**sql_memory_model**|**int**|**S’applique à :** [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] , SP1 et versions ultérieures.<br /><br />Spécifie le modèle de mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé par pour allouer de la mémoire. N'accepte pas la valeur NULL.<br /><br />1 = modèle de mémoire conventionnelle<br />2 = verrouiller les pages en mémoire<br /> 3 = grandes pages en mémoire|
|**sql_memory_model_desc**|**nvarchar (120)**|**S’applique à :** [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] , SP1 et versions ultérieures.<br /><br />Spécifie le modèle de mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé par pour allouer de la mémoire. N'accepte pas la valeur NULL.<br /><br />**** =  Conventionnel[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le modèle de mémoire conventionnel pour allouer de la mémoire. Il s’agit du modèle de mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL par défaut lorsque le compte de service ne dispose pas de privilèges de verrouillage des pages en mémoire au cours du démarrage.<br />**** =  LOCK_PAGES[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le verrouillage des pages en mémoire pour allouer de la mémoire. Il s’agit du gestionnaire de mémoire SQL par défaut quand SQL Server compte de service dispose du privilège verrouiller les pages en mémoire pendant le démarrage de SQL Server.<br /> **** =  LARGE_PAGES[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des pages de grande taille en mémoire pour allouer de la mémoire. SQL Server utilise l’allocation de pages de grande taille pour allouer de la mémoire uniquement avec l’édition Enterprise lorsque SQL Server compte de service possède le privilège verrouiller les pages en mémoire pendant le démarrage du serveur et lorsque l’indicateur de trace 834 est activé.|
|**pdw_node_id**|**int**|**S’applique à :** [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
|**socket_count** |**int** | **S’applique à :** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 et versions ultérieures.<br /><br />Spécifie le nombre de sockets de processeur disponibles sur le système. |  
|**cores_per_socket** |**int** | **S’applique à :** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 et versions ultérieures.<br /><br />Spécifie le nombre de processeurs par Socket disponibles sur le système. |  
|**numa_node_count** |**int** | **S’applique à :** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 et versions ultérieures.<br /><br />Spécifie le nombre de nœuds NUMA disponibles sur le système. Cette colonne comprend des nœuds NUMA physiques, ainsi que des nœuds NUMA souples. |  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   

## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server vues de gestion dynamique liées au système d’exploitation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  



