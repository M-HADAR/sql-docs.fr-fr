---
title: PARAMÈTRES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- PARAMETERS_TSQL
- PARAMETERS
dev_langs:
- TSQL
helpviewer_keywords:
- PARAMETERS view
- INFORMATION_SCHEMA.PARAMETERS view
ms.assetid: 06ded0ca-7d21-4400-864a-b801e855b257
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e6d3880c4be8925e6b85a20af1324537e3977ecc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103284"
---
# <a name="parameters-transact-sql"></a>PARAMETERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une ligne pour chaque paramètre d'une fonction définie par l'utilisateur ou d'une procédure stockée accessible à l'utilisateur actuel dans la base de données active. Pour les fonctions, cette vue renvoie également une ligne avec des informations sur les valeurs de retour.  
  
 Pour récupérer des informations de ces vues, spécifiez le nom complet de **INFORMATION_SCHEMA.** _view_name_.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**SPECIFIC_CATALOG**|**nvarchar (** 128 **)**|Nom de catalogue de la routine pour laquelle cet élément constitue un paramètre|  
|**SPECIFIC_SCHEMA**|**nvarchar (** 128 **)**|Nom du schéma de la routine pour laquelle cet élément constitue un paramètre<br /><br /> <strong> \* Important \* \* </strong> N’utilisez pas de vues de INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet consiste à interroger l’affichage catalogue sys. Objects.|  
|**SPECIFIC_NAME**|**nvarchar (** 128 **)**|Nom de la routine pour laquelle cet élément constitue un paramètre|  
|**ORDINAL_POSITION**|**int**|Position ordinale du paramètre en commençant à 1. Dans le cas de la valeur de retour d'une fonction, il s'agit d'un 0.|  
|**PARAMETER_MODE**|**nvarchar (** 10 **)**|Retourne IN pour un paramètre d'entrée, OUT pour un paramètre de sortie et INOUT pour un paramètre d'entrée/sortie.|  
|**IS_RESULT**|**nvarchar (** 10 **)**|Retourne YES s'il s'agit du résultat de la routine qui est une fonction. Dans le cas contraire, la valeur retournée est NO.|  
|**AS_LOCATOR**|**nvarchar (** 10 **)**|Retourne YES si l'élément est déclaré comme localisateur. Dans le cas contraire, la valeur retournée est NO.|  
|**PARAMETER_NAME**|**nvarchar (** 128 **)**|Nom du paramètre. NULL si ceci correspond à la valeur retournée d'une fonction.|  
|**DATA_TYPE**|**nvarchar (** 128 **)**|Type de données fourni par le système.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Longueur maximale en caractères des données de type binaire ou caractère.<br /><br /> -1 pour les données de type **XML** et de valeur élevée. Dans le cas contraire, la valeur NULL est retournée.|  
|**CHARACTER_OCTET_LENGTH**|**int**|Longueur maximale en octets des données de type binaire ou caractère.<br /><br /> -1 pour les données de type **XML** et de valeur élevée. Dans le cas contraire, la valeur NULL est retournée.|  
|**COLLATION_CATALOG**|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|**COLLATION_SCHEMA**|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|Nom du classement du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|**CHARACTER_SET_CATALOG**|**nvarchar (** 128 **)**|Nom de catalogue du jeu de caractères du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|**CHARACTER_SET_SCHEMA**|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|Nom du jeu de caractères du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|**NUMERIC_PRECISION**|**tinyint**|Précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Base de précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**NUMERIC_SCALE**|**tinyint**|Échelle des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**DATETIME_PRECISION**|**smallint**|Précision en fractions de seconde si le type de paramètre est **DateTime** ou **smalldatetime**. Dans le cas contraire, la valeur NULL est retournée.|  
|**INTERVAL_TYPE**|**nvarchar (** 30 **)**|NULL. réservé à une utilisation future.|  
|**INTERVAL_PRECISION**|**smallint**|NULL. réservé à une utilisation future.|  
|**USER_DEFINED_TYPE_CATALOG**|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|**USER_DEFINED_TYPE_SCHEMA**|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|**USER_DEFINED_TYPE_NAME**|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|**SCOPE_CATALOG**|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|**SCOPE_SCHEMA**|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|**SCOPE_NAME**|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Vues de schémas d’informations &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. Columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. Parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  
