---
title: EndOfRecordset, événement (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a83f101d46a94a4ea43a85424677fc1c8da08be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918940"
---
# <a name="endofrecordset-event-ado"></a>EndOfRecordset, événement (ADO)
L’événement **EndOfRecordset** est appelé en cas de tentative de déplacement vers une ligne située au-delà de la fin du [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *fMoreData*  
 Valeur **VARIANT_BOOL** qui, si elle est définie sur VARIANT_TRUE, indique que des lignes supplémentaires ont été ajoutées au **Recordset**.  
  
 *Statu*  
 Valeur d’état [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 Lorsque **EndOfRecordset** est appelé, ce paramètre a la valeur **adStatusOK** si l’opération à l’origine de l’événement a réussi. Elle a la valeur **adStatusCantDeny** si cet événement ne peut pas demander l’annulation de l’opération qui a provoqué cet événement.  
  
 Avant le retour de **EndOfRecordset** , définissez ce paramètre sur **adStatusUnwantedEvent** pour empêcher les notifications suivantes.  
  
 *jeu d’enregistrements*  
 Objet **Recordset** . **Jeu d’enregistrements** pour lequel cet événement s’est produit.  
  
## <a name="remarks"></a>Notes  
 Un événement **EndOfRecordset** peut se produire si l’opération [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) échoue.  
  
 Ce gestionnaire d’événements est appelé en cas de tentative de déplacement au-delà de la fin de l’objet **Recordset** , peut-être en raison de l’appel de **MoveNext**. Toutefois, dans ce cas, vous pouvez récupérer plus d’enregistrements à partir d’une base de données et les ajouter à la fin de l’ensemble d' **enregistrements**. Dans ce cas, affectez à *fMoreData* la valeur VARIANT_TRUE et retournez à partir de **EndOfRecordset**. Appelez ensuite **MoveNext** à nouveau pour accéder aux enregistrements récupérés récemment.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
