---
title: sys. dm_os_volume_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_volume_stats_TSQL
- dm_os_volume_stats
- sys.dm_os_volume_stats
- sys.dm_os_volume_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_volume_stats dynamic management function
ms.assetid: fa1c58ad-8487-42ad-956c-983f2229025f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7ec8171b569adbf887c1e153fb2b41619778f48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899718"
---
# <a name="sysdm_os_volume_stats-transact-sql"></a>sys.dm_os_volume_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-2008R2SP1-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-2008R2sp1-xxxx-xxxx-xxx-md.md)]

  Retourne les informations relatives au volume du système d'exploitation (répertoire) sur lequel les bases de données et fichiers spécifiés sont stockés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez cette fonction de gestion dynamique pour vérifier les attributs du lecteur de disque physique ou retourner les informations relatives à l'espace disque disponible pour le répertoire.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sys.dm_os_volume_stats (database_id, file_id)  
```  
  
##  <a name="Arguments"></a> Arguments  
 *database_id*  
 ID de la base de données. *database_id* est de **type int**, sans valeur par défaut. Ne peut pas avoir la valeur NULL.  
  
 *file_id*  
 ID du fichier. *file_id* est de **type int**, sans valeur par défaut. Ne peut pas avoir la valeur NULL.  
  
## <a name="table-returned"></a>Table retournée  
  
||||  
|-|-|-|  
|**Colonne**|**Type de données**|**Description**|  
|**database_id**|**int**|ID de la base de données. Ne peut pas avoir la valeur null.|  
|**file_id**|**int**|ID du fichier. Ne peut pas avoir la valeur null.|  
|**volume_mount_point**|**nvarchar(512)**|Point de montage à la racine duquel le volume est attaché. Peut retourner une chaîne vide.|  
|**volume_id**|**nvarchar(512)**|Identificateur du volume du système d'exploitation. Peut retourner une chaîne vide|  
|**logical_volume_name**|**nvarchar(512)**|Nom du volume logique. Peut retourner une chaîne vide|  
|**file_system_type**|**nvarchar(512)**|Type du volume du système de fichiers (par exemple, NTFS, FAT, RAW). Peut retourner une chaîne vide|  
|**total_bytes**|**bigint**|Taille totale (en octets) du volume. Ne peut pas avoir la valeur null.|  
|**available_bytes**|**bigint**|Espace disponible sur le volume. Ne peut pas avoir la valeur null.|  
|**supports_compression**|**bit**|Indique si le volume prend en charge la compression du système d'exploitation. Ne peut pas avoir la valeur null.|  
|**supports_alternate_streams**|**bit**|Indique si le volume prend en charge les flux de remplacement. Ne peut pas avoir la valeur null.|  
|**supports_sparse_files**|**bit**|Indique si le volume prend en charge les fichiers partiellement alloués.  Ne peut pas avoir la valeur null.|  
|**is_read_only**|**bit**|Indique si le volume est actuellement marqué comme étant en lecture seule. Ne peut pas avoir la valeur null.|  
|**is_compressed**|**bit**|Indique si ce volume est actuellement compressé. Ne peut pas avoir la valeur null.|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation `VIEW SERVER STATE`.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-return-total-space-and-available-space-for-all-database-files"></a>R. Retour de l'espace total et de l'espace disponible pour tous les fichiers de base de données  
 L'exemple suivant retourne l'espace total et l'espace disponible (en octets) pour tous les fichiers de base de données dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
SELECT f.database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.master_files AS f  
CROSS APPLY sys.dm_os_volume_stats(f.database_id, f.file_id);  
```  
  
### <a name="b-return-total-space-and-available-space-for-the-current-database"></a>B. Retour de l'espace total et de l'espace disponible pour la base de donnée actuelle  
 L'exemple suivant retourne l'espace total et l'espace disponible (en octets) pour les fichiers de base de données dans la base de données actuelle.  
  
```sql  
SELECT database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.database_files AS f  
CROSS APPLY sys.dm_os_volume_stats(DB_ID(f.name), f.file_id);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys. master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
  
  
