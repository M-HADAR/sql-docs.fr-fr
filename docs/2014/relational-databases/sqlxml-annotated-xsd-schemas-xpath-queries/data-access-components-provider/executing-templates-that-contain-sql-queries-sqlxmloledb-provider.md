---
title: Exécution de modèles contenant des requêtes SQL (fournisseur SQLXMLOLEDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- templates [SQLXML]
- SQLXMLOLEDB Provider, executing template files
- templates [SQLXML], SQL queries
- XML templates [SQLXML]
- SQL queries [SQLXML]
ms.assetid: ff2bc36f-e3fb-4d8f-8e3a-2680a39eda11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cdf149720e853725a7f2fc9d0c03b24ea2caf9f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013116"
---
# <a name="executing-templates-that-contain-sql-queries-sqlxmloledb-provider"></a>Exécution de modèles contenant des requêtes SQL (fournisseur SQLXMLOLEDB)
  Cet exemple illustre l’utilisation de la propriété SQLXMLOLEDB spécifique au fournisseur ClientSideXML. Dans cet exemple d'application ADO côté client, un modèle XML contenant une requête SQL est exécuté sur le serveur.  
  
 Étant donné que la propriété ClientSideXML a la valeur true, l’instruction SELECT sans la clause FOR XML est envoyée au serveur. Le serveur exécute la requête et retourne un ensemble de lignes au client. Le client applique ensuite la transformation FOR XML à l'ensemble de lignes et génère un document XML.  
  
 Le modèle XML fournit un élément racine unique de niveau supérieur (\<> racine) pour le document XML généré ; par conséquent, la propriété racine XML n’est pas fournie.  
  
 Pour exécuter des modèles XML, le dialecte {5d531cb2-e6ed-11d2-b252-00c04f681b71} doit être spécifié.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion. En outre, cet exemple spécifie l’utilisation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de Native Client (SQLNCLI11) pour le fournisseur de données qui requiert l’installation d’un logiciel client réseau supplémentaire. Pour plus d’informations, consultez [Configuration système requise pour SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
  
Sub Main()  
  Dim oTestStream As New ADODB.Stream  
  Dim oTestConnection As New ADODB.Connection  
  Dim oTestCommand As New ADODB.Command  
  oTestConnection.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
  
  Set oTestCommand.ActiveConnection = oTestConnection  
  oTestCommand.Properties("ClientSideXML") = True  
  oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:query> " & _  
        "   SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
  oTestStream.Open  
  ' You need the dialect if you are executing   
  ' XML templates (not for SQL queries).  
  oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  oTestCommand.Properties("Output Stream").Value = oTestStream  
  oTestCommand.Execute , , adExecuteStream  
  
  oTestStream.Position = 0  
  oTestStream.Charset = "utf-8"  
  Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
  
Sub Form_Load()  
  Main  
End Sub  
```  
  
  
