---
title: sys. dm_resource_governor_external_resource_pool_affinity (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02ec95d318825c1759067455b62f3dae6a86c184
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053327"
---
# <a name="sysdm_resource_governor_external_resource_pool_affinity-transact-sql"></a>sys. dm_resource_governor_external_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**S’applique à :** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] et [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Retourne les informations d’affinité de l’UC relatives à la configuration actuelle du pool de ressources externes.
  
|Nom de la colonne|Type de données|Description|
|----------------|---------------|-----------------|
|pool_id|**int**|ID du pool de ressources externes. N'accepte pas la valeur NULL.|
|processor_group|**smallint**|ID du groupe de processeur logique Windows. N'accepte pas la valeur NULL.|
|cpu_mask|**bigint**|Masque binaire représentant les UC associées à ce pool. N'accepte pas la valeur NULL.|
  
## <a name="remarks"></a>Notes

Les pools créés avec une affinité de `AUTO` n’apparaissent pas dans cette vue, car ils n’ont pas d’affinité. Pour plus d’informations, consultez les instructions [Create External RESOURCE pool &#40;Transact-sql&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md) et [ALTER External resource pool &#40;transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md) .

## <a name="permissions"></a>Autorisations

Nécessite l'autorisation `VIEW SERVER STATE`.

## <a name="see-also"></a>Voir aussi

[Gouvernance des ressources pour Machine Learning dans SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[sys. dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[external scripts enabled (option de configuration de serveur)](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
