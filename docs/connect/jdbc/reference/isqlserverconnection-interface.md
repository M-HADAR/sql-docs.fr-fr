---
title: Interface ISQLServerConnection | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 031c01e2-2c65-4fe4-9700-fdbcc7a39f30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2fbe3b6c1721720720b06bdcf4122a289589e639
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977451"
---
# <a name="isqlserverconnection-interface"></a>Interface ISQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une connexion JDBC à une base de données [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Cette interface a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.sql.Connection  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public interface ISQLServerConnection  
```  
  
## <a name="remarks"></a>Notes  
 Cette interface est implémentée par la [classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Cette interface expose le champ spécifique au [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] suivant :  
  
|Champ|Pour plus d'informations, consultez|  
|-----------|-------------------------------|  
|public final static int TRANSACTION_SNAPSHOT|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|  
|public UUID getClientConnectionId()|[getClientConnectionID()](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
