---
title: executeUpdate, méthode (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2f44a689-65c8-4c94-9574-e9c08ea7918e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a5c905c11d76f6f9928cb621ce5a35caa4dd1419
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954749"
---
# <a name="executeupdate-method-javalangstring-javalangstring"></a>executeUpdate, méthode (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Exécute l’instruction SQL donnée et signale à [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] que les clés générées automatiquement indiquées dans le tableau donné doivent être récupérables.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 **Chaîne** qui contient une instruction SQL.  
  
 *columnNames*  
  
 Tableau de type **String** indiquant quels noms de colonnes des clés générées automatiquement doivent être disponibles.  
  
## <a name="return-value"></a>Valeur retournée  
 **Entier** qui indique le nombre de lignes affectées, 0 si vous utilisez une instruction DDL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode executeUpdate est spécifiée par la méthode executeUpdate de l’interface java.sql.Statement.  
  
 Si l’exécution d’une procédure stockée aboutit à plusieurs mises à jour, ou si cela génère plusieurs jeux de résultats, utilisez la méthode [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) pour exécuter la procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [executeUpdate, méthode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
