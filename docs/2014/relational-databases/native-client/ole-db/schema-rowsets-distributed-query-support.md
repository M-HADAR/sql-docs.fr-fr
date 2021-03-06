---
title: Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 24411ceb757414f1a70f0f10bdf5b2c7660e2cd8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62667595"
---
# <a name="distributed-query-support-in-schema-rowsets"></a>Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma
  Pour prendre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en charge les requêtes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distribuées, l’interface **IDBSchemaRowset** du fournisseur OLE DB Native Client retourne des métadonnées sur les serveurs liés.  
  
 Si la propriété DBPROPSET_SQLSERVERSESSION SSPROP_QUOTEDCATALOGNAMES est VARIANT_TRUE, un identificateur entre guillemets peut être spécifié pour le nom de catalogue (par exemple "my.catalog"). Lors de la restriction de la sortie de l’ensemble de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lignes de schéma par catalogue, le fournisseur de OLE DB Native Client reconnaît un nom en deux parties contenant le serveur lié et le nom du catalogue. Pour les ensembles de lignes de schéma dans le tableau ci-dessous, en spécifiant un nom de catalogue en deux parties comme _linked_server_**.** _Catalog_ limite la sortie au catalogue applicable du serveur lié nommé.  
  
|Ensemble de lignes de schéma|Restriction de catalogue|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMNS|TABLE_CATALOG|  
|DBSCHEMA_PRIMARY_KEYS|TABLE_CATALOG|  
|DBSCHEMA_TABLES|TABLE_CATALOG|  
|DBSCHEMA_FOREIGN_KEYS|PK_TABLE_CATALOG FK_TABLE_CATALOG|  
|DBSCHEMA_INDEXES|TABLE_CATALOG|  
|DBSCHEMA_COLUMN_PRIVILEGES|TABLE_CATALOG|  
|DBSCHEMA_TABLE_PRIVILEGES|TABLE_CATALOG|  
  
> [!NOTE]  
>  Pour restreindre un ensemble de lignes de schéma à tous les catalogues d’un serveur lié, utilisez la syntaxe *serveur_lié* (où le point séparateur fait partie de la spécification du nom). Cette syntaxe équivaut à spécifier NULL pour la restriction du nom de catalogue ; elle est également utilisée lorsque le serveur lié indique une source de données qui ne prend pas en charge les catalogues.  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client définit l’ensemble de lignes de schéma LinkedServers, en renvoyant une liste de sources de données OLE DB inscrites en tant que serveurs liés.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des ensembles de lignes de schéma &#40;OLE DB&#41;](schema-rowset-support-ole-db.md)   
 [&#40;de l’ensemble de lignes LINKEDSERVERS OLE DB&#41;](schema-rowsets-linkedservers-rowset.md)  
  
  
