---
title: La valeur de SQLGetInfo a été retournée pour les fichiers texte | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- SQLGetInfo function [ODBC], returned values for text files
- text file driver [ODBC], SQLGetInfo
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: 739a9d72-26aa-42dd-b9fd-76c679976d09
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3d2578c9abe6e2e3b1f99b0e680fc0fcf8c104f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898809"
---
# <a name="sqlgetinfo-returned-values-for-text-files"></a>Valeurs retournées par SQLGetInfo pour les fichiers texte
Le tableau suivant répertorie les #defines en langage C pour l’argument *fInfoType* et les valeurs correspondantes retournées par **SQLGetInfo**. Ces informations peuvent être récupérées en transmettant le #defines de langage C indiqué à **SQLGetInfo** dans l’argument *fInfoType* . Pour plus d’informations sur les valeurs retournées par **SQLGetInfo**, consultez le [Guide de référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
> [!NOTE]  
>  Où **SQLGetInfo** retourne un masque de bits 32 bits, une barre verticale (&#124;) représente une opération or au niveau du bit.  
  
|TypeInfo|Valeur renvoyée|  
|--------------|--------------------|  
|SQL_ACCESSIBLE_PROCEDURES|"N"|  
|SQL_ACCESSIBLE_TABLES|"Y"|  
|SQL_ACTIVE_ENVIRONMENTS|0|  
|SQL_AGGREGATE_FUNCTIONS|Tous les jeux|  
|SQL_ALTER_DOMAIN|0|  
|SQL_ALTER_TABLE|0|  
|SQL_ASYNC_MODE|0|  
|SQL_BATCH_ROW_COUNT|0|  
|SQL_BATCH_SUPPORT|0|  
|SQL_BOOKMARK_PERSISTENCE|Valeurs multiples|  
|SQL_CATALOG_LOCATION|SQL_QL_START|  
|SQL_CATALOG_NAME|"Y"|  
|SQL_CATALOG_NAME_SEPARATOR|"\\"|  
|SQL_CATALOG_TERM|Directory|  
|SQL_CATALOG_USAGE|Valeurs multiples|  
|SQL_COLLATION_SEQ|""|  
|SQL_COLUMN_ALIAS|"Y"|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_CB_NON_NULL|  
|SQL_CONVERT_BIGINT|0|  
|SQL_CONVERT_BINARY|Valeurs multiples|  
|SQL_CONVERT_BIT|0|  
|SQL_CONVERT_CHAR|Valeurs multiples|  
|SQL_CONVERT_DATE|Valeurs multiples|  
|SQL_CONVERT_DECIMAL|0|  
|SQL_CONVERT_DOUBLE|Valeurs multiples|  
|SQL_CONVERT_FLOAT|Valeurs multiples|  
|SQL_CONVERT_FUNCTIONS|SQL_FN_CVT_CONVERT|  
|SQL_CONVERT_INTEGER|Valeurs multiples|  
|SQL_CONVERT_LONGVARBINARY|Valeurs multiples|  
|SQL_CONVERT_LONGVARCHAR|Valeurs multiples|  
|SQL_CONVERT_NUMERIC|Valeurs multiples|  
|SQL_CONVERT_REAL|Valeurs multiples|  
|SQL_CONVERT_SMALLINT|Valeurs multiples|  
|SQL_CONVERT_TIME|Valeurs multiples|  
|SQL_CONVERT_TIMESTAMP|Valeurs multiples|  
|SQL_CONVERT_TINYINT|Valeurs multiples|  
|SQL_CONVERT_VARBINARY|Valeurs multiples|  
|SQL_CONVERT_VARCHAR|Valeurs multiples|  
|SQL_CORRELATION_NAME|SQL_CN_ANY|  
|SQL_CREATE_ASSERTION|0|  
|SQL_CREATE_CHARACTER_SET|0|  
|SQL_CREATE_COLLATION|0|  
|SQL_CREATE_DOMAIN|0|  
|SQL_CREATE_SCHEMA|0|  
|SQL_CREATE_TABLE|SQL_CT_CREATE_TABLE|  
|SQL_CREATE_TRANSLATION|0|  
|SQL_CREATE_VIEW|0|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_CB_CLOSE|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_CB_CLOSE|  
|SQL_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_DATA_SOURCE_NAME|Le nom de source de fichier ODBC. ini ou «» si le mot clé DRIVER est utilisé dans ODBC. ini|  
|SQL_DATA_SOURCE_READ_ONLY|"Y"|  
|SQL_DATABASE_NAME|Répertoire de base de données actuel|  
|SQL_DATETIME_LITERALS|0|  
|SQL_DBMS_NAME|FINANCIÈRE|  
|SQL_DBMS_VER|ISAM : texte<br /><br /> Version : 1,0<br /><br /> Format du numéro de version : 01.00.0000|  
|SQL_DDL_INDEX|0|  
|SQL_DEFAULT_TXN_ISOLATION|0|  
|SQL_DESCRIBE_PARAMETER|0|  
|SQL_DRIVER_HDBC|Géré par le gestionnaire de pilotes.|  
|SQL_DRIVER_HENV|Géré par le gestionnaire de pilotes.|  
|SQL_DRIVER_HLIB|Géré par le gestionnaire de pilotes.|  
|SQL_DRIVER_HSTMT|Géré par le gestionnaire de pilotes.|  
|SQL_DRIVER_NAME|« OdbcJt32. dll »|  
|SQL_DRIVER_ODBC_VER|"3.51.0000"|  
|SQL_DRIVER_VER|« 4,00.*nnnn*» (*nnnn* spécifie la date de génération)|  
|SQL_DROP_ASSERTION|0|  
|SQL_DROP_CHARACTER_SET|0|  
|SQL_DROP_COLLATION|0|  
|SQL_DROP_DOMAIN|0|  
|SQL_DROP_SCHEMA|0|  
|SQL_DROP_TABLE|SQL_DT_DROP_TABLE|  
|SQL_DROP_TRANSLATION|0|  
|SQL_DROP_VIEW|SQL_DV_DROP_VIEW|  
|SQL_EXPRESSIONS_IN_ORDERBY|"Y"|  
|SQL_FILE_USAGE|SQL_FILE_TABLE|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT|  
|SQL_GETDATA_EXTENSIONS|Valeurs multiples|  
|SQL_GROUP_BY|SQL_GB_GROUP_BY_CONTAINS_SELECT|  
|SQL_IDENTIFIER_CASE|SQL_IC_MIXED|  
|SQL_IDENTIFIER_QUOTE_CHAR|"\`" (guillemets de retour)|  
|SQL_KEYWORDS|Valeurs multiples|  
|SQL_LIKE_ESCAPE_CLAUSE|"N"|  
|SQL_MAX_BINARY_LITERAL_LEN|255|  
|SQL_MAX_CATALOG_NAME_LEN|66|  
|SQL_MAX_CHAR_LITERAL_LEN|255|  
|SQL_MAX_COLUMN_NAME_LEN|64|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|10|  
|SQL_MAX_COLUMNS_IN_INDEX|0|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|10|  
|SQL_MAX_COLUMNS_IN_SELECT|255|  
|SQL_MAX_COLUMNS_IN_TABLE|255|  
|SQL_MAX_CONCURRENT_ACTIVITIES|0|  
|SQL_MAX_CURSOR_NAME_LEN|64|  
|SQL_MAX_DRIVER_CONNECTIONS|64|  
|SQL_MAX_INDEX_SIZE|0|  
|SQL_MAX_PROCEDURE_NAME_LEN|0|  
|SQL_MAX_ROW_SIZE|65535|  
|SQL_MAX_ROW_SIZE_INCLUDES_LONG|"Y"|  
|SQL_MAX_SCHEMA_NAME_LEN|0|  
|SQL_MAX_STATEMENT_LEN|65 000|  
|SQL_MAX_TABLE_NAME_LEN|12|  
|SQL_MAX_TABLES_IN_SELECT|16|  
|SQL_MAX_USER_NAME_LEN|0|  
|SQL_MULT_RESULT_SETS|"N"|  
|SQL_MULTIPLE_ACTIVE_TXN|"Y"|  
|SQL_NEED_LONG_DATA_LEN|"N"|  
|SQL_NON_NULLABLE_COLUMNS|SQL_NNC_NON_NULL|  
|SQL_NULL_COLLATION|SQL_NC_LOW|  
|SQL_NUMERIC_FUNCTIONS|Valeurs multiples|  
|CONFORMITÉ SQL_ODBC_SAG_CLI_|SQL_OSCC_COMPLIANT|  
|SQL_ODBC_SQL_INTEGRITY|"N"|  
|SQL_ODBC_VER|À partir du gestionnaire de pilotes|  
|SQL_OJ_CAPABILITIES|Valeurs multiples|  
|SQL_ORDER_BY_COLUMNS_IN_SELECT|"N"|  
|SQL_OUTER_JOINS|"Y"|  
|SQL_PROCEDURE_TERM|""|  
|SQL_PROCEDURES|"N"|  
|SQL_QUOTED_IDENTIFIER_CASE|SQL_IC_MIXED|  
|SQL_ROW_UPDATES|"N"|  
|SQL_SCHEMA_TERM|""|  
|SQL_SCHEMA_USAGE|0|  
|SQL_SCROLL_OPTIONS|Valeurs multiples|  
|SQL_SEARCH_PATTERN_ESCAPE|"\\"|  
|SQL_SERVER_NAME|FINANCIÈRE|  
|SQL_SPECIAL_CHARACTERS|"~\`@ # $% ^& * _-+ =\\} {" ';:?/><,. ! ' [] &#124;»|  
|SQL_STRING_FUNCTIONS|Valeurs multiples|  
|SQL_SUBQUERIES|Valeurs multiples|  
|SQL_SYSTEM_FUNCTIONS|0|  
|SQL_TABLE_TERM|Tableau|  
|SQL_TIMEDATE_ADD_INTERVALS|0|  
|SQL_TIMEDATE_DIFF_INTERVALS|0|  
|SQL_TIMEDATE_FUNCTIONS|Valeurs multiples|  
|SQL_TXN_CAPABLE|SQL_TC_NONE|  
|SQL_TXN_ISOLATION_OPTION|0|  
|SQL_UNION|Valeurs multiples|  
|SQL_USER_NAME|""|
