---
title: getMetaData, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.getMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ed49a53-ed61-4e95-ad67-45957aaabb6a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bbc0a0493498f3d216c9e1395f651d8afec70711
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981856"
---
# <a name="getmetadata-method-sqlserverpreparedstatement"></a>getMetaData, méthode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère un objet [SQLServerResultSetMetaData Class](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) contenant des informations sur les colonnes de l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) retourné à l’exécution de cet objet [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.sql.ResultSetMetaData getMetaData()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Objet ResultSetMetaData.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMetaData est spécifiée par la méthode getMetaData dans l’interface java. Sql. PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
