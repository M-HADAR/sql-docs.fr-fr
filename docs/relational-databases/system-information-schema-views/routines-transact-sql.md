---
title: ROUTINEs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- ROUTINES_TSQL
- ROUTINES
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINES view
- INFORMATION_SCHEMA.ROUTINES view
ms.assetid: c75561b2-c9a1-48a1-9afa-a5896b6454cf
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1ec3836db241320beabfbd4672ffad9b22ccaf58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078523"
---
# <a name="routines-transact-sql"></a>ROUTINES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie une ligne pour chaque procédure stockée et chaque fonction accessibles à l'utilisateur actuel dans la base de données actuelle. Les colonnes qui décrivent la valeur de retour s'appliquent uniquement aux fonctions. Pour les procédures stockées, ces colonnes comportent la valeur NULL.  
  
 Pour récupérer des informations de ces vues, spécifiez le nom complet de INFORMATION_SCHEMA. *view_name*.  
  
> [!NOTE]  
>  La colonne ROUTINE_DEFINITION contient les instructions sources qui ont servi à créer la fonction ou la procédure stockée. Ces instructions sources sont susceptibles de contenir des retours-chariot imbriqués. Si vous renvoyez cette colonne à une application qui affiche les résultats au format texte, les retours-chariot imbriqués dans les résultats ROUTINE_DEFINITION peuvent modifier la mise en forme de l'ensemble de résultats global. Si vous sélectionnez la colonne ROUTINE_DEFINITION, vous devez ajuster les retours-chariot imbriqués, en transférant par exemple l'ensemble de résultats dans une grille ou en réintégrant ROUTINE_DEFINITION dans sa propre zone de texte.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|SPECIFIC_CATALOG|**nvarchar (** 128 **)**|Nom spécifique du catalogue Ce nom est le même que ROUTINE_CATALOG.|  
|SPECIFIC_SCHEMA|**nvarchar (** 128 **)**|Nom spécifique du schéma.<br /><br /> ** \* Important \* \* ** N’utilisez pas de vues de INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet consiste à interroger l’affichage catalogue sys. Objects.|  
|SPECIFIC_NAME|**nvarchar (** 128 **)**|Nom spécifique du catalogue Ce nom est le même que ROUTINE_NAME.|  
|ROUTINE_CATALOG|**nvarchar (** 128 **)**|Nom de catalogue de la fonction|  
|ROUTINE_SCHEMA|**nvarchar (** 128 **)**|Nom du schéma contenant cette fonction.<br /><br /> ** \* Important \* \* ** N’utilisez pas de vues de INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet consiste à interroger l’affichage catalogue sys. Objects.|  
|ROUTINE_NAME|**nvarchar (** 128 **)**|Nom de la fonction.|  
|ROUTINE_TYPE|**nvarchar (** 20 **)**|Renvoie la valeur PROCEDURE pour les procédures stockées et la valeur FUNCTION pour les fonctions.|  
|MODULE_CATALOG|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|MODULE_SCHEMA|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|MODULE_NAME|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|UDT_CATALOG|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|UDT_SCHEMA|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|UDT_NAME|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|DATA_TYPE|**nvarchar (** 128 **)**|Type de données de la valeur renvoyée de la fonction. Retourne la **table** si une fonction table.|  
|CHARACTER_MAXIMUM_LENGTH|**int**|Longueur maximale en caractères, lorsque la valeur renvoyée est de type caractère.<br /><br /> -1 pour les données de type **XML** et de valeur élevée.|  
|CHARACTER_OCTET_LENGTH|**int**|Longueur maximale en octets, lorsque la valeur renvoyée est de type caractère.<br /><br /> -1 pour les données de type **XML** et de valeur élevée.|  
|COLLATION_CATALOG|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|COLLATION_SCHEMA|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|COLLATION_NAME|**nvarchar (** 128 **)**|Nom de classement de la valeur renvoyée. Renvoie la valeur NULL pour les types non-caractère.|  
|CHARACTER_SET_CATALOG|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|CHARACTER_SET_SCHEMA|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|CHARACTER_SET_NAME|**nvarchar (** 128 **)**|Nom du jeu de caractères de la valeur renvoyée. Renvoie la valeur NULL pour les types non-caractère.|  
|NUMERIC_PRECISION|**smallint**|Précision numérique de la valeur renvoyée. Pour les types non numériques, retourne la valeur NULL.|  
|NUMERIC_PRECISION_RADIX|**smallint**|Base de la précision numérique de la valeur renvoyée. Renvoie la valeur NULL pour les types non numériques.|  
|NUMERIC_SCALE|**smallint**|Échelle de la valeur renvoyée. Renvoie la valeur NULL pour les types non numériques.|  
|DATETIME_PRECISION|**smallint**|Précision fractionnaire d’une seconde si la valeur de retour est de type **DateTime**. Dans le cas contraire, la valeur NULL est retournée.|  
|INTERVAL_TYPE|**nvarchar (** 30 **)**|NULL. réservé à une utilisation future.|  
|INTERVAL_PRECISION|**smallint**|NULL. réservé à une utilisation future.|  
|TYPE_UDT_CATALOG|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|TYPE_UDT_SCHEMA|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|TYPE_UDT_NAME|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|SCOPE_CATALOG|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|SCOPE_SCHEMA|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|SCOPE_NAME|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|MAXIMUM_CARDINALITY|**bigint**|NULL. réservé à une utilisation future.|  
|DTD_IDENTIFIER|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|ROUTINE_BODY|**nvarchar (** 30 **)**|Renvoie la valeur SQL pour une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] et la valeur EXTERNAL pour une fonction externe.<br /><br /> Les fonctions sont toujours en SQL.|  
|ROUTINE_DEFINITION|**nvarchar (** 4000 **)**|Retourne les 4 000 premiers caractères du texte de définition de la fonction ou de la procédure stockée, si ces dernières ne sont pas chiffrées. Dans le cas contraire, la valeur NULL est retournée.<br /><br /> Pour vous assurer que vous obtenez la définition complète, interrogez la fonction [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) ou la colonne de définition de l’affichage catalogue [sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) .|  
|EXTERNAL_NAME|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|EXTERNAL_LANGUAGE|**nvarchar (** 30 **)**|NULL. réservé à une utilisation future.|  
|PARAMETER_STYLE|**nvarchar (** 30 **)**|NULL. réservé à une utilisation future.|  
|IS_DETERMINISTIC|**nvarchar (** 10 **)**|Renvoie la valeur YES si la routine est déterministe.<br /><br /> Renvoie la valeur NO si la routine est non déterministe.<br /><br /> Renvoie toujours la valeur NO pour les procédures stockées.|  
|SQL_DATA_ACCESS|**nvarchar (** 30 **)**|Renvoie l'une des valeurs suivantes :<br /><br /> NONE = La fonction de contient pas de SQL.<br /><br /> CONTAINS = La fonction est susceptible de contenir du SQL.<br /><br /> READS = La fonction est susceptible de lire des données SQL.<br /><br /> MODIFIES = La fonction est susceptible de modifier des données SQL.<br /><br /> La valeur READS est renvoyée pour toutes les fonctions et la valeur MODIFIES est renvoyée pour toutes les procédures stockées.|  
|IS_NULL_CALL|**nvarchar (** 10 **)**|Indique si la routine est appelée lorsque l'un de ses arguments a la valeur NULL.|  
|SQL_PATH|**nvarchar (** 128 **)**|NULL. réservé à une utilisation future.|  
|SCHEMA_LEVEL_ROUTINE|**nvarchar (** 10 **)**|Renvoie YES dans le cas d'une fonction au niveau du schéma, ou NO dans le cas contraire.<br /><br /> Retourne toujours YES.|  
|MAX_DYNAMIC_RESULT_SETS|**smallint**|Nombre maximal d'ensembles de résultats dynamiques renvoyés par la routine.<br /><br /> Renvoie 0 dans le cas des fonctions.|  
|IS_USER_DEFINED_CAST|**nvarchar (** 10 **)**|Renvoie YES dans le cas d'une fonction CAST définie par l'utilisateur, ou NO dans le cas contraire.<br /><br /> Renvoie toujours NO.|  
|IS_IMPLICITLY_INVOCABLE|**nvarchar (** 10 **)**|Renvoie la valeur YES si la routine peut être appelée implicitement et NO dans le cas contraire.<br /><br /> Renvoie toujours NO.|  
|CREATED|**DATETIME**|Heure de création de la routine.|  
|LAST_ALTERED|**DATETIME**|Dernière date/heure de modification de la fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Vues de schémas d’informations &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. Columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)  
  
  
