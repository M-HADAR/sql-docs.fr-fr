---
title: FetchProgress, événement (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ab93d8117a5fb3d2bbc95ea33bbacdc7fba3f151
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932828"
---
# <a name="fetchprogress-event-ado"></a>FetchProgress, événement (ADO)
L’événement **FetchProgress**est appelé régulièrement au cours d’une longue opération asynchrone pour signaler le nombre de lignes qui ont été récupérées actuellement dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Avancement*  
 Valeur de **type long** indiquant le nombre d’enregistrements qui ont été récupérés actuellement par l’opération d’extraction.  
  
 *MaxProgress*  
 Valeur de **type long** indiquant le nombre maximal d’enregistrements qui doivent être récupérés.  
  
 *Statu*  
 Valeur d’état [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 *jeu d’enregistrements*  
 Objet **Recordset** qui est l’objet pour lequel les enregistrements sont récupérés.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous utilisez **FetchProgress** avec un **Recordset**enfant, sachez que les valeurs de paramètre *Progress* et *MaxProgress* sont dérivées de l’ensemble de lignes de [service de curseur](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) sous-jacent. Les valeurs retournées représentent le nombre total d’enregistrements dans l’ensemble de lignes sous-jacent, et pas seulement le nombre d’enregistrements dans le chapitre actuel.  
  
> [!NOTE]
>  Pour utiliser **FetchProgress** avec Microsoft Visual Basic, Visual Basic 6,0 ou version ultérieure est requis.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
