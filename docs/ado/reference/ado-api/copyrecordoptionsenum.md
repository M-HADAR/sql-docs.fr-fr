---
title: CopyRecordOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CopyRecordOptionsEnum
helpviewer_keywords:
- CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6692125b7323bedc7a416e51555c373ef850ce0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919370"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Spécifie le comportement de la méthode [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|Indique que le fournisseur *source* tente de simuler la copie à l’aide des opérations de téléchargement et de téléchargement si cette méthode échoue en raison de la *destination*sur un autre serveur ou par un fournisseur différent de la *source*. Notez que des fonctionnalités de fournisseur différentes peuvent nuire aux performances ou perdre des données.|  
|**adCopyNonRecursive**|2|Copie le répertoire actif, mais aucun de ses sous-répertoires, vers la destination. L’opération de copie n’est pas récursive.|  
|**adCopyOverWrite**|1|Remplace le fichier ou le répertoire si la *destination* pointe vers un fichier ou un répertoire existant.|  
|**adCopyUnspecified**|-1|valeur par défaut. Effectue l’opération de copie par défaut : l’opération échoue si le fichier ou le répertoire de destination existe déjà et que l’opération copie de manière récursive.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [CopyRecord, méthode (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
