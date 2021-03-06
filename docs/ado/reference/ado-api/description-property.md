---
title: Description, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Description
- Error::GetDescription
- Error::get_Description
helpviewer_keywords:
- Description property
ms.assetid: 4b5d6790-6c29-42aa-bf78-d9cfb8ad7965
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 48b3a6987e6c7b6c3754f5041d90d248520345ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933086"
---
# <a name="description-property"></a>Description, propriété
Décrit un objet d' [erreur](../../../ado/reference/ado-api/error-object.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **chaîne** qui contient une description de l’erreur.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **Description** pour obtenir une brève description de l’erreur. Affichez cette propriété pour alerter l’utilisateur en cas d’erreur que vous ne pouvez pas ou ne souhaitez pas gérer. La chaîne provient de ADO ou d’un fournisseur.  
  
 Les fournisseurs sont responsables du passage du texte d’erreur spécifique à ADO. ADO ajoute un objet [Error](../../../ado/reference/ado-api/error-object.md) à la collection **Errors** pour chaque erreur de fournisseur ou avertissement qu’il reçoit. Énumérez la collection **Errors** pour tracer les erreurs que le fournisseur passe.  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [HelpContext, HelpFile, propriétés](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number, propriété (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source, propriété (objet Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
