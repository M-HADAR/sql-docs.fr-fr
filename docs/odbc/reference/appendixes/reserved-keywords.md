---
title: Mots clés réservés | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC function call reserved words [ODBC]
- reserved keywords [ODBC]
ms.assetid: 8eeede59-a828-44bf-866c-1ca9a77a2c5e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a89a24ddbbe14938824819e24fd9112597168507
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057209"
---
# <a name="reserved-keywords"></a>Mots clés réservés
Les mots suivants sont réservés et utilisés dans les appels de fonction ODBC. Ces mots ne limitent pas la grammaire SQL minimale ; Toutefois, pour garantir la compatibilité avec les pilotes qui prennent en charge la grammaire SQL de base, les applications doivent éviter d’utiliser l’un de ces mots clés. La valeur #**define** SQL_ODBC_KEYWORDS contient une liste séparée par des virgules de ces mots clés.  
  
|||  
|-|-|  
|ABSOLUTE|IS|  
|ACTION|ISOLATION|  
|ADA|JOIN|  
|ADD|KEY|  
|ALL|LANGUAGE|  
|ALLOCATE|LAST|  
|ALTER|LEADING|  
|AND|LEFT|  
|ANY|LEVEL|  
|ARE|LIKE|  
|AS|LOCAL|  
|ASC|LOWER|  
|ASSERTION|MATCH|  
|AT|MAX|  
|AUTHORIZATION|MIN|  
|AVG|MINUTE|  
|BEGIN|MODULE|  
|BETWEEN|MONTH|  
|BIT|NAMES|  
|BIT_LENGTH|NATIONAL|  
|BOTH|NATURAL|  
|BY|NCHAR|  
|CASCADE|NEXT|  
|CASCADED|NON|  
|CASE|Aucune|  
|CAST|NOT|  
|CATALOG|NULL|  
|CHAR|NULLIF|  
|CHAR_LENGTH|NUMERIC|  
|CHARACTER|OCTET_LENGTH|  
|CHARACTER_LENGTH|OF|  
|CHECK|ACTIVÉ|  
|CLOSE|ONLY|  
|COALESCE|OPEN|  
|COLLATE|OPTION|  
|COLLATION|OR|  
|COLUMN|ORDER|  
|COMMIT|OUTER|  
|CONNECT|OUTPUT|  
|CONNECTION|OVERLAPS|  
|CONSTRAINT|PAD|  
|CONTRAINTES|PARTIAL|  
|CONTINUE|PASCAL|  
|CONVERT|ENDROIT|  
|CORRESPONDING|PRECISION|  
|COUNT|PREPARE|  
|CREATE|PRESERVE|  
|CROSS|PRIMARY|  
|CURRENT|PRIOR|  
|CURRENT_DATE|PRIVILEGES|  
|CURRENT_TIME|PROCEDURE|  
|CURRENT_TIMESTAMP|PUBLIC|  
|CURRENT_USER|READ|  
|CURSOR|real|  
|DATE|REFERENCES|  
|DAY|RELATIVE|  
|DEALLOCATE|RESTRICT|  
|DEC|REVOKE|  
|DECIMAL|RIGHT|  
|DECLARE|ROLLBACK|  
|DEFAULT|ROWS|  
|DEFERRABLE|SCHEMA|  
|DEFERRED|SCROLL|  
|Suppression|SECOND|  
|DESC|SECTION|  
|DESCRIBE|SELECT|  
|DESCRIPTOR|SESSION|  
|DIAGNOSTICS|SESSION_USER|  
|DISCONNECT|SET|  
|DISTINCT|TAILLE appropriée|  
|DOMAIN|SMALLINT|  
|DOUBLE|SOME|  
|DROP|SPACE|  
|ELSE|SQL|  
|END|SQLCA|  
|END-EXEC|SQLCODE|  
|ESCAPE|SQLERROR|  
|EXCEPT|SQLSTATE|  
|EXCEPTION|SQLWARNING|  
|EXEC|SUBSTRING|  
|Exécutez|SUM|  
|EXISTS|SYSTEM_USER|  
|EXTERNAL|TABLE|  
|EXTRACT|TEMPORARY|  
|FALSE|THEN|  
|FETCH|TEMPS|  
|FIRST|timestamp|  
|FLOAT|TIMEZONE_HOUR|  
|FOR|TIMEZONE_MINUTE|  
|FOREIGN|TO|  
|FORTRAN|TRAILING|  
|FOUND|TRANSACTION|  
|FROM|TRANSLATE|  
|FULL|TRANSLATION|  
|GET|TRIM|  
|GLOBAL|TRUE|  
|GO|UNION|  
|GOTO|UNIQUE|  
|GRANT|UNKNOWN|  
|GROUP|UPDATE|  
|HAVING|UPPER|  
|HOUR|USAGE|  
|IDENTITÉ|Utilisateur|  
|IMMEDIATE|USING|  
|IN|VALEUR|  
|INCLUDE|VALUES|  
|INDEX|VARCHAR|  
|INDICATOR|VARYING|  
|INITIALLY|VIEW|  
|INNER|WHEN|  
|INPUT|WHENEVER|  
|INSENSITIVE|WHERE|  
|INSERT|WITH|  
|INT|WORK|  
|INTEGER|WRITE|  
|INTERSECT|YEAR|  
|INTERVAL|ZONE|  
|INTO||
