---
title: NativeError, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetNativeError
- Error::get_NativeError
- Error::NativeError
helpviewer_keywords:
- NativeError property [ADO]
ms.assetid: b9b47e57-18a4-4186-aef5-5bd18d7b1d74
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 42888190dcd7b5e41987e6e8ec7194242549aa9c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918020"
---
# <a name="nativeerror-property-ado"></a>NativeError, propriété (ADO)
Indique le code d’erreur spécifique au fournisseur pour un objet d' [erreur](../../../ado/reference/ado-api/error-object.md) donné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **type long** qui indique le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **NativeError** pour récupérer les informations d’erreur propres à la base de données pour un objet d' **erreur** particulier. Par exemple, lorsque vous utilisez le fournisseur Microsoft ODBC pour OLE DB avec une base de données Microsoft SQL Server, les codes d’erreur natifs qui proviennent de SQL Server passent par ODBC et le fournisseur ODBC à la propriété **Native NativeError** .  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
