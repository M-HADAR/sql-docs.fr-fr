---
title: Établissement d’une connexion à une source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [SQL Server Native Client]
- connections [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, data source connections
- CoCreateInstance method
- OLE DB data sources [SQL Server Native Client]
ms.assetid: 7ebd1394-cc8d-4bcf-92f3-c374a26e7ba0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 263728218fd032c0814d73197cde56fc2d661e9c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63183737"
---
# <a name="establishing-a-connection-to-a-data-source"></a>Établissement d'une connexion à une source de données
  Pour accéder au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client, le consommateur doit d’abord créer une instance d’un objet source de données en appelant la méthode **CoCreateInstance** . Un identificateur de classe unique (CLSID) identifie chaque fournisseur OLE DB. Pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client, l’identificateur de classe est CLSID_SQLNCLI10. Vous pouvez également utiliser le symbole SQLNCLI_CLSID qui sera résolu en fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB utilisé dans le sqlncli. h que vous référencez.  
  
 L’objet de source de données expose l’interface **IDBProperties**, que le consommateur utilise pour fournir les informations d’authentification de base, comme le nom du serveur, le nom de la base de données, l’ID d’utilisateur et le mot de passe. La méthode **IDBProperties::SetProperties** est appelée pour définir ces propriétés.  
  
 S'il existe plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s'exécutent sur l'ordinateur, le nom du serveur est spécifié sous la forme NomServeur\NomInstance.  
  
 L’objet de source de données expose également l’interface **IDBInitialize**. Une fois les propriétés définies, la connexion à la source de données est établie en appelant la méthode **IDBInitialize::Initialize**. Par exemple :  
  
```  
CoCreateInstance(CLSID_SQLNCLI10,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 Cet appel à **CoCreateInstance** crée un objet unique de la classe associée à CLSID_SQLNCLI10 (CSLID associé aux données et au code qui sera utilisé pour créer l’objet). IID_IDBInitialize est une référence à l’identificateur de l’interface (**IDBInitialize**) à utiliser pour communiquer avec l’objet.  
  
 Les éléments suivants sont un exemple de fonction qui initialise et établit une connexion à la source de données.  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.  
   hr = CoCreateInstance(CLSID_SQLNCLI10,   
                         NULL,   
                         CLSCTX_INPROC_SERVER,  
                         IID_IDBInitialize,   
                         (void **) &pIDBInitialize);  
   // Initialize property values needed to establish connection.  
   for (i = 0 ; i < 4 ; i++)   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   // See DBPROP structure for more information on InitProperties  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt    = VT_BSTR;  
   InitProperties[0].vValue.bstrVal=   
                     SysAllocString(L"Server");  
   InitProperties[0].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid       = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt    = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"database");  
   InitProperties[1].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid       = DB_NULLID;  
  
   // Username (login).  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt    = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid       = DB_NULLID;  
   InitProperties[3].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid       = DB_NULLID;  
  
   // Construct the DBPROPSET structure(rgInitPropSet). The   
   // DBPROPSET structure is used to pass an array of DBPROP   
   // structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties   = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties,   
                           (void **)&pIDBProperties);  
   hr = pIDBProperties->SetProperties(1, rgInitPropSet);   
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   pIDBInitialize->Initialize();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création d'une application de fournisseur OLE DB de SQL Server Native Client](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
