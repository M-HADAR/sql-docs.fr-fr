---
title: Fichiers d’en-tête | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- header files [ODBC]
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d20f2535038b13eac0b8d5ca20dfa77bfc12588
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139025"
---
# <a name="header-files"></a>Fichiers d’en-tête
Le fichier d’en-tête SQL. h contient des prototypes pour les fonctions et les fonctionnalités dans le niveau de conformité de l’interface ODBC de base. Le fichier d’en-tête Sqlext. h contient des prototypes pour les fonctions et les fonctionnalités dans les niveaux de conformité de l’API de niveau 1 et 2. Le fichier d’en-tête SqlTypes. h contient des définitions de type et des indicateurs pour les types de données SQL.  
  
 Les fichiers d’en-tête contiennent tous un **#define**, ODBCVER, qu’une application ou un pilote peut définir pour être compilé pour différentes versions d’ODBC.  
  
 Pour aligner avec l’interface CLI ISO et ouvrir l’interface CLI de groupe, les fichiers d’en-tête contiennent des alias pour les types d’informations utilisés dans les appels à **SQLGetInfo**. Dans le tableau suivant, la colonne « nom ODBC » indique le nom ODBC pour le type d’informations dans référence de l' [API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md). La colonne « alias dans le fichier d’en-tête » indique le nom utilisé dans l’interface CLI ISO et l’interface CLI Open Group. La valeur numérique réelle de ces noms de manifeste est la même dans ODBC et dans la CLI standard. Ces alias permettent à une application ou à un pilote conforme aux normes de se compiler avec les fichiers d’en-tête ODBC *3. x* .  
  
 Ces alias incluent des expansions d’abréviations dans les noms ODBC afin que les noms soient plus compréhensibles. « MAX » est étendu à « MAXIMUM », « NBCAR » à « longueur », « MULT » à « MULTIPLE », « JO » à « OUTER_JOIN » et « TXN » à « TRANSACTION ».  
  
|Nom ODBC|Alias dans le fichier d’en-tête|  
|---------------|--------------------------|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAXIMUM_CATALOG_NAME_LENGTH|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAXIMUM_COLUMN_NAME_LENGTH|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAXIMUM_COLUMNS_IN_GROUP_BY|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAXIMUM_COLUMNS_IN_ORDER_BY|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAXIMUM_COLUMNS_IN_SELECT|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAXIMUM_COLUMNS_IN_TABLE|  
|SQL_MAX_CONCURRENT_ACTIVITIES|SQL_MAXIMUM_CONCURRENT_ACTIVITIES|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAXIMUM_CURSOR_NAME_LENGTH|  
|SQL_MAX_DRIVER_CONNECTIONS|SQL_MAXIMUM_DRIVER_CONNECTIONS|  
|SQL_MAX_IDENTIFIER_LEN|SQL_MAXIMUM_IDENTIFIER_LENGTH|  
|SQL_MAX_SCHEMA_NAME_LEN|SQL_MAXIMUM_SCHEMA_NAME_LENGTH|  
|SQL_MAX_STATEMENT_LEN|SQL_MAXIMUM_STATEMENT_LENGTH|  
|SQL_MAX_TABLE_NAME_LEN|SQL_MAXIMUM_TABLE_NAME_LENGTH|  
|SQL_MAX_TABLES_IN_SELECT|SQL_MAXIMUM_TABLES_IN_SELECT|  
|SQL_MAX_USER_NAME_LEN|SQL_MAXIMUM_USER_NAME_LENGTH|  
|SQL_MULT_RESULT_SETS|SQL_MULTIPLE_RESULT_SETS|  
|SQL_OJ_CAPABILITIES|SQL_OUTER_JOIN_CAPABILITIES|  
|SQL_TXN_CAPABLE|SQL_TRANSACTION_CAPABLE|  
|SQL_TXN_ISOLATION_OPTION|SQL_TRANSACTION_ISOLATION_OPTION|
