---
title: IBCPSession::BCPExec (OLE DB) | Microsoft Docs
description: IBCPSession::BCPExec (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPExec (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPExec method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 6ace2ccd8fbba9c8c3566ad706754ed314152d4a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015496"
---
# <a name="ibcpsessionbcpexec-ole-db"></a>IBCPSession::BCPExec (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Effectue l'opération de copie en bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPExec(   
      DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a>Notes  
 La méthode **BCPExec** copie des données à partir d’un fichier utilisateur vers une table de base de données ou vice versa, selon la valeur du paramètre *eDirection* utilisé avec la méthode [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md).  
  
 Avant d'appeler **BCPExec**, appelez la méthode **BCPInit** avec un nom de fichier utilisateur valide. L'échec de cette opération entraîne une erreur. La seule exception est si une requête doit être utilisée pour une opération de copie en bloc sortante. Dans ce cas, spécifiez NULL pour le nom de table dans la méthode **BCPInit** , puis spécifiez la requête à l'aide de l'option BCP_OPTION_HINTS.  
  
 La méthode **BCPExec** est la seule méthode de copie en bloc qui est susceptible d'être en attente pendant une durée prolongée. Il s'agit par conséquent de la seule méthode de copie en bloc qui prend en charge le mode asynchrone. Pour utiliser le mode asynchrone, affectez la valeur VARIANT_TRUE à la propriété de session spécifique au fournisseur SSPROP_ASYNCH_BULKCOPY avant d'appeler la méthode **BCPExec** . Cette propriété est disponible dans le jeu de propriétés DBPROPSET_SQLSERVERSESSION. Pour tester l'achèvement, appelez la méthode **BCPExec** avec les mêmes paramètres. Si la copie en bloc n'est pas encore terminée, la méthode **BCPExec** retourne DB_S_ASYNCHRONOUS. Elle retourne également dans l'argument *pRowsCopied* le nombre de lignes qui ont été envoyées ou reçues à partir du serveur. Les lignes envoyées au serveur sont validées uniquement une fois la fin du lot atteinte.  
  
## <a name="arguments"></a>Arguments  
 *pRowsCopied*[out]  
 Pointeur vers une valeur DWORD. La méthode **BCPExec** remplit la valeur DWORD avec le nombre de lignes copiées avec succès. Si l'argument *pRowsCopied* a la valeur NULL, il est ignoré par la méthode **BCPExec** .  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite. Pour obtenir des informations détaillées, utilisez l’interface [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode **BCPInit** n'a pas été appelée avant cette méthode. Se produit également si l'opération a été abandonnée suite à l'utilisation de l'option BCP_OPTION_ABORT et que la méthode **BCPExec** a été appelée ensuite.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
 DB_S_ENDOFROWSET  
 L'opération de copie en bloc s'est terminée et tout le transfert de données a été effectué.  
  
 DB_S_ASYNCHRONOUS  
 Le lot actuel de lignes a été copié. Rappelez la méthode **BCPExec** pour transférer le lot suivant.  
  
 DB_S_ERRORSOCCURRED  
 Des erreurs se sont produites pendant l'opération de copie en bloc et certaines lignes n'ont pas pu être copiées. Le nombre d'erreurs est inférieur au nombre maximal d'erreurs autorisé.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
