---
title: sys. sensitivity_classifications (Transact-SQL) | Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- rank
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 376438a45d6b104cbf4e66dbdf8e5542cf3fd2c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74542052"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Retourne une ligne pour chaque élément classifié dans la base de données.

|Nom de la colonne|Type de données|Description|
|-----------------|---------------|-----------------|  
|**type**|**int**|Identifie la classe de l’élément sur lequel la classification existe. Aura toujours la valeur 1 (représentant une colonne)|  
|**class_desc**|**varchar (16)**|Description de la classe de l’élément sur lequel la classification existe. aura toujours la valeur *OBJECT_OR_COLUMN*|  
|**major_id**|**int**|Représente l’ID de la table contenant la colonne classifiée, correspondant à sys. all_objects. object_id|  
|**minor_id**|**int**|Représente l’ID de la colonne sur laquelle la classification existe, correspondant à sys. all_columns. column_id|   
|**label**|**sysname**|Étiquette (lisible) affectée à la classification de sensibilité|  
|**label_id**|**sysname**|ID associé à l’étiquette, qui peut être utilisé par un système de protection des informations tel que Azure Information Protection (AIP)|  
|**information_type**|**sysname**|Type d’information (lisible) affecté à la classification de sensibilité|  
|**information_type_id**|**sysname**|ID associé au type d’information, qui peut être utilisé par un système de protection des informations tel que Azure Information Protection (AIP)|  
|**moteurs**|**int**|Valeur numérique du rang : <br><br>0 pour aucun<br>10 pour faible<br>20 pour moyen<br>30 pour la haute<br>40 pour critique| 
|**rank_desc**|**sysname**|Représentation textuelle du classement :  <br><br>AUCUN, FAIBLE, MOYEN, ÉLEVÉ, CRITIQUE|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Notes  

- Cette vue fournit une visibilité de l’état de classification de la base de données. Il peut être utilisé pour gérer les classifications de base de données, ainsi que pour générer des rapports.
- Actuellement, seule la classification des colonnes de base de données est prise en charge.
 
## <a name="examples"></a>Exemples

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>R. Affichage de la liste de toutes les colonnes classées et de leur classification correspondante

L’exemple suivant retourne une table qui répertorie le nom de la table, le nom de la colonne, l’étiquette, l’ID de l’étiquette, le type d’informations, l’ID du type d’information pour chaque colonne classifiée de la base de données.

> [!NOTE]
> L’étiquette est un mot clé pour Azure SQL Data Warehouse.

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID], [Rank], [Rank_Desc]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation **View any Sensitivity classification** . 
 
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="see-also"></a>Voir aussi  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Prise en main de SQL Information Protection](https://aka.ms/sqlip)
