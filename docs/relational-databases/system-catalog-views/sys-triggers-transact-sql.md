---
title: sys. Triggers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- triggers
- triggers_TSQL
- sys.triggers
- sys.triggers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.triggers catalog view
ms.assetid: cefa4fc4-b8b9-4cd7-b124-eed5283acbfc
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 33eb5a1c4176041d64ba60a3a684b75bc4816350
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091928"
---
# <a name="systriggers-transact-sql"></a>sys.triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contient une ligne pour chaque objet qui est un déclencheur de type TR ou TA. Les noms de déclencheurs DML sont étendus au niveau du schéma et, par conséquent, sont visibles dans **sys. Objects**. Les noms de déclencheurs DDL ont une portée définie par l'entité parente et ils sont visibles uniquement dans cette vue.  
  
 Les colonnes **parent_class** et **Name** identifient de manière unique le déclencheur dans la base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nomme**|**sysname**|Nom du déclencheur. Les noms de déclencheurs DML ont une portée de schéma. Les noms de déclencheurs DDL ont une portée définie par rapport à l'entité parente.|  
|**object_id**|**int**|Numéro d'identification de l'objet. Unique dans une base de données.|  
|**parent_class**|**tinyint**|Classe du parent du déclencheur.<br /><br /> 0 = Base de données, pour les déclencheurs DDL.<br /><br /> 1 = Objet ou colonne pour les déclencheurs DML.|  
|**parent_class_desc**|**nvarchar (60)**|Description de la classe parente du déclencheur.<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_id**|**int**|ID du parent du déclencheur, comme suit :<br /><br /> 0 = Déclencheurs apparentés à une base de données.<br /><br /> Pour les déclencheurs DML, il s’agit de la **object_id** de la table ou de la vue sur laquelle le déclencheur DML est défini.|  
|**entrer**|**Char (2)**|Type d’objet :<br /><br /> TA = Déclencheur assembly (CLR)<br /><br /> TR = Déclencheur SQL|  
|**type_desc**|**nvarchar (60)**|Description du type d’objet.<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**DATETIME**|Date de création du déclencheur.|  
|**modify_date**|**DATETIME**|Date de la dernière modification de l'objet avec l'instruction ALTER.|  
|**is_ms_shipped**|**bit**|Déclencheur créé pour l'utilisateur par un composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interne.|  
|**is_disabled**|**bit**|Déclencheur désactivé.|  
|**is_not_for_replication**|**bit**|Déclencheur créé sous la forme NOT FOR REPLICATION.|  
|**is_instead_of_trigger**|**bit**|1 = Déclencheurs INSTEAD OF<br /><br /> 0 = Déclencheurs AFTER|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
