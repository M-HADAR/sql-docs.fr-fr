---
title: toString, méthode (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f3acffe6a922084fd63e38a8e212b5cf86d6b278
ms.sourcegitcommit: c0fd28306a3b42895c2ab673734fbae2b56f9291
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096908"
---
# <a name="tostring-method-datetimeoffset"></a>Méthode toString (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une représentation sous forme de chaîne de l’objet **DateTimeOffset** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Représentation sous forme de chaîne de l’objet **DateTimeOffset** .  
  
## <a name="remarks"></a>Notes  
 La chaîne respecte le format `YYYY-MM-DD HH:mm:ss[.fffffff] [+|-]HH:mm`.  
  
 Les fractions de seconde de la chaîne renvoyée sont remplies avec des zéros jusqu'à la précision déclarée. Par exemple, un **DateTimeOffset (6)** avec une valeur de «2010-03-10 12:34:56.78-08:00» sera mis en forme par DateTimeOffset. ToString comme «2010-03-10 12:34:56.780000-08:00».  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
