---
title: Item, exemple de propriété (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Item property [ADO], Visual Basic example
ms.assetid: b4476603-691b-4081-8797-a3d0b331dce5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c309319ceb81e9af4a8b84d0b96537d0be933e32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918340"
---
# <a name="item-property-example-vb"></a>Item, exemple de propriété (VB)
Cet exemple montre comment la propriété [Item](../../../ado/reference/ado-api/item-property-ado.md) accède aux membres d’une collection. L’exemple ouvre la table ***Authors*** de la base de données ***pubs*** avec une commande paramétrable.  
  
 Le paramètre de la commande exécutée sur la base de données est accessible à partir de la collection de [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) de l’objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) par index et par nom. Les champs de l’ensemble d' [enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) retourné sont ensuite accessibles à partir de la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) de cet objet par index et par nom.  
  
```  
'BeginItemVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn As ADODB.Connection  
    Dim rstAuthors As ADODB.Recordset  
    Dim cmd As ADODB.Command  
    Dim prm As ADODB.Parameter  
    Dim fld As ADODB.Field  
    Dim strCnxn As String  
  
    Dim ix As Integer  
    Dim limit As Long  
    Dim Column(0 To 8) As Variant  
  
    Set Cnxn = New ADODB.Connection  
    Set rstAuthors = New ADODB.Recordset  
    Set cmd = New ADODB.Command  
  
    'Set the array with the Authors table field (column) names  
    Column(0) = "au_id"  
    Column(1) = "au_lname"  
    Column(2) = "au_fname"  
    Column(3) = "phone"  
    Column(4) = "address"  
    Column(5) = "city"  
    Column(6) = "state"  
    Column(7) = "zip"  
    Column(8) = "contract"  
  
    cmd.CommandText = "SELECT * FROM Authors WHERE state = ?"  
    Set prm = cmd.CreateParameter("ItemXparm", adChar, adParamInput, 2, "CA")  
    cmd.Parameters.Append prm  
     ' set connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
    cmd.ActiveConnection = Cnxn  
     ' open recordset  
    rstAuthors.Open cmd, , adOpenStatic, adLockReadOnly  
    'Connection and CommandType are omitted because  
    'a Command object is provided  
  
    Debug.Print "The Parameters collection accessed by index..."  
    Set prm = cmd.Parameters.Item(0)  
    Debug.Print "Parameter name = '"; prm.Name; "', value = '"; prm.Value; "'"  
    Debug.Print  
  
    Debug.Print "The Parameters collection accessed by name..."  
    Set prm = cmd.Parameters.Item("ItemXparm")  
    Debug.Print "Parameter name = '"; prm.Name; "', value = '"; prm.Value; "'"  
    Debug.Print  
  
    Debug.Print "The Fields collection accessed by index..."  
  
    rstAuthors.MoveFirst  
    limit = rstAuthors.Fields.Count - 1  
    For ix = 0 To limit  
       Set fld = rstAuthors.Fields.Item(ix)  
       Debug.Print "Field "; ix; ": Name = '"; fld.Name; _  
                   "', Value = '"; fld.Value; "'"  
    Next ix  
  
    Debug.Print  
  
    Debug.Print "The Fields collection accessed by name..."  
  
    rstAuthors.MoveFirst  
    For ix = 0 To 8  
       Set fld = rstAuthors.Fields.Item(Column(ix))  
       Debug.Print "Field name = '"; fld.Name; "', Value = '"; fld.Value; "'"  
    Next ix  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    Set cmd = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
'EndItemVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Item, propriété (ADO)](../../../ado/reference/ado-api/item-property-ado.md)   
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
