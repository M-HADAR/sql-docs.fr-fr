---
title: Détails de l’erreur de SQL Server | Microsoft Docs
description: Détails des erreurs SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
author: pmasl
ms.author: pelopes
ms.openlocfilehash: ddc9a1b1a242f9a92b1e854520d16abeb7baf809
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015649"
---
# <a name="sql-server-error-detail"></a>Détail des erreurs SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server définit l’interface d’erreur spécifique au fournisseur [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1). L'interface retourne davantage de détails sur une erreur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et s'avère utile en cas d'échec de l'exécution d'une commande ou d'opérations d'ensemble de lignes.  
  
 Vous pouvez accéder à l’interface **ISQLServerErrorInfo** de deux manières.  
  
 Le consommateur peut appeler **IErrorRecords::GetCustomerErrorObject** pour obtenir un pointeur **ISQLServerErrorInfo**, comme illustré dans l’exemple de code suivant. (Il n’est pas nécessaire d’obtenir **ISQLErrorInfo**). **ISQLErrorInfo** et **ISQLServerErrorInfo** sont tous deux des objets d’erreur OLE DB personnalisés, **ISQLServerErrorInfo** étant l’interface à utiliser pour obtenir des informations sur les erreurs de serveur, notamment des détails sur le nom de la procédure et les numéros de ligne.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 L’autre méthode permettant d’obtenir un pointeur **ISQLServerErrorInfo** consiste à appeler la méthode **QueryInterface** sur un pointeur **ISQLErrorInfo** qui a déjà été obtenu. Notez que comme **ISQLServerErrorInfo** contient un surensemble des informations disponibles auprès de **ISQLErrorInfo**, il est logique d’accéder directement à **ISQLServerErrorInfo** via **GetCustomerErrorObject**.  
  
 L’interface **ISQLServerErrorInfo** expose une fonction membre, [ISQLServerErrorInfo::GetErrorInfo](../../oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). La fonction retourne un pointeur à une structure SSERRORINFO et un pointeur à une mémoire tampon de chaîne. Les deux pointeurs référencent la mémoire que le consommateur doit libérer avec méthode **IMalloc::Free**.  
  
 Les membres de la structure SSERRORINFO sont interprétés par le consommateur comme suit.  
  
|Membre|Description|  
|------------|-----------------|  
|*pwszMessage*|Message d'erreur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Identique à la chaîne retournée dans **IErrorInfo::GetDescription**.|  
|*pwszServer*|Nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour la session.|  
|*pwszProcedure*|S'il y a lieu, nom de la procédure d'où provient l'erreur. Sinon, une chaîne vide.|  
|*lNative*|Numéro d'erreur natif [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Identique à la valeur retournée dans le paramètre *plNativeError* de **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|État d'un message d'erreur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravité d'un message d'erreur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|S'il y a lieu, numéro de ligne d'une procédure stockée sur laquelle s'est produite l'erreur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../oledb/ole-db-errors/errors.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
