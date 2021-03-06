---
title: IHpublishercolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumns
- IHpublishercolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumns system table
ms.assetid: a5347750-224c-40d9-ae12-57e7213b7db9
author: stevestein
ms.author: sstein
ms.openlocfilehash: a5e2f64294652586a87fcd25fda3c29517dc295d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990267"
---
# <a name="ihpublishercolumns-transact-sql"></a>IHpublishercolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table système **IHpublishercolumns** représente les métadonnées stockées sur le serveur de publication. Cette table contient une ligne par colonne répliquée à partir des serveurs de publication non SQL Server à l'aide du serveur de distribution actuel. Les informations sur les types de données dans **IHpublishercolumns** sont spécifiques au système de gestion de base de données non SQL Server (SGBD) à partir duquel les données sont publiées. Cette table est stockée dans la base de données de distribution.  
  
## <a name="definition"></a>Définition  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Identifie une colonne publiée.|  
|**table_id**|**int**|Identifie la table source de [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) à laquelle la colonne appartient.|  
|**publisher_id**|**smallint**|Identifie le serveur de publication non SQL Server à partir duquel la colonne est publiée.|  
|**nomme**|**sysname**|Nom de la colonne publiée.|  
|**column_ordinal**|**int**|Identifie la colonne par ordre.|  
|**entrer**|**varchar(255**|Type de données de la colonne source sur le serveur de publication.|  
|**base**|**bigint**|Longueur de la colonne source sur le serveur de publication.|  
|**prec**|**int**|Précision de la colonne source sur le serveur de publication.|  
|**scale**|**int**|Échelle de la colonne source sur le serveur de publication.|  
|**IsNullable**|**bit**|Indique si la colonne accepte les valeurs NULL, où **1** signifie que les valeurs NULL sont acceptées.|  
|**iscaptured**|**bit**|Indique si un déclencheur existe sur la colonne, ce qui peut être le cas même si celle-ci n'est pas publiée dans un article. La valeur **1** signifie que le déclencheur existe sur la colonne.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sysarticlecolumns &#40;vue système&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
