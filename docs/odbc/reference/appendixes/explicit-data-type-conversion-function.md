---
title: Fonction de conversion de type de données explicite | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- explicit data type conversion functions [ODBC]
- data type conversion functions [ODBC]
- functions [ODBC], explicit data type conversion functions
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6982f7b7caa71abc08c5b84ef1bb6211dcadaecd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67913612"
---
# <a name="explicit-data-type-conversion-function"></a>Fonctions de conversion de types de données explicites
La conversion de type de données explicite est spécifiée en termes de définitions de type de données SQL.  
  
 La syntaxe ODBC pour la fonction de conversion de type de données explicite ne limite pas les conversions. La validité de conversions spécifiques d’un type de données en un autre type de données est déterminée par chaque implémentation propre au pilote. Le pilote convertit la syntaxe ODBC en syntaxe native, en rejetant les conversions qui, bien que autorisées dans la syntaxe ODBC, ne sont pas prises en charge par la source de données. La fonction ODBC **SQLGetInfo**, avec les options de conversion (telles que SQL_CONVERT_BIGINT, SQL_CONVERT_BINARY, SQL_CONVERT_INTERVAL_YEAR_MONTH, etc.), offre un moyen d’obtenir des informations sur les conversions prises en charge par la source de données.  
  
 Le format de la fonction **Convert** est le suivant :  
  
 **Convert (** _value_exp_, _data_type_**)**  
  
 La fonction retourne la valeur spécifiée par *value_exp* convertie en la *data_type*spécifiée, où *data_type* est l’un des mots clés suivants :  
  
|||  
|-|-|  
|SQL_BIGINT|SQL_INTERVAL_HOUR_TO_MINUTE|  
|SQL_BINARY|SQL_INTERVAL_HOUR_TO_SECOND|  
|SQL_BIT|SQL_INTERVAL_MINUTE_TO_SECOND|  
|SQL_CHAR|SQL_LONGVARBINARY|  
|SQL_DECIMAL|SQL_LONGVARCHAR|  
|SQL_DOUBLE|SQL_NUMERIC|  
|SQL_FLOAT|SQL_REAL|  
|SQL_GUID|SQL_SMALLINT|  
|SQL_INTEGER|SQL_DATE|  
|SQL_INTERVAL_MONTH|SQL_TIME|  
|SQL_INTERVAL_YEAR|SQL_TIMESTAMP|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_TINYINT|  
|SQL_INTERVAL_DAY|SQL_VARBINARY|  
|SQL_INTERVAL_HOUR|SQL_VARCHAR|  
|SQL_INTERVAL_MINUTE|SQL_WCHAR|  
|SQL_INTERVAL_SECOND|SQL_WLONGVARCHAR|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_WVARCHAR|  
|SQL_INTERVAL_DAY_TO_MINUTE||  
|SQL_INTERVAL_DAY_TO_SECOND||  
  
 La syntaxe ODBC pour la fonction de conversion de type de données explicite ne prend pas en charge la spécification du format de conversion. Si la spécification de formats explicites est prise en charge par la source de données sous-jacente, un pilote doit spécifier une valeur par défaut ou implémenter la spécification de format.  
  
 L’argument *value_exp* peut être un nom de colonne, le résultat d’une autre fonction scalaire ou un littéral de chaîne ou numérique. Par exemple :  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 Convertit la sortie de la fonction scalaire caillé en une chaîne de caractères.  
  
 Comme ODBC n’impose pas de type de données pour les valeurs de retour des fonctions scalaires (étant donné que les fonctions sont souvent spécifiques à la source de données), les applications doivent utiliser la fonction de conversion scalaire chaque fois que cela est possible pour forcer la conversion du type de données.  
  
 Les deux exemples suivants illustrent l’utilisation de la fonction **Convert** . Ces exemples supposent l’existence d’une table appelée EMPLOYees, avec une colonne MATEMP de type SQL_SMALLINT et une colonne EMPNAME de type SQL_CHAR.  
  
 Si une application spécifie l’instruction SQL suivante :  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   Un pilote pour ORACLE traduit l’instruction SQL en :  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   Un pilote pour SQL Server traduit l’instruction SQL en :  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 Si une application spécifie l’instruction SQL suivante :  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   Un pilote pour ORACLE traduit l’instruction SQL en :  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   Un pilote pour SQL Server traduit l’instruction SQL en :  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Un pilote pour Ingres traduit l’instruction SQL en :  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
