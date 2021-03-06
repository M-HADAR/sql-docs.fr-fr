---
title: DeleteRecord, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 409c4e21395b7b903cf4ff03726fbd37a2a218d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919084"
---
# <a name="deleterecord-method-ado"></a>DeleteRecord, méthode (ADO)
Supprime une entité représentée par un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 facultatif. Valeur de **chaîne** qui contient une URL identifiant l’entité (par exemple, le fichier ou le répertoire) à supprimer. Si la *source* est omise ou qu’elle spécifie une chaîne vide, l’entité représentée par l' [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) en cours est supprimée. Si l’enregistrement est un enregistrement de collection ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) de **adCollectionRecord**, tel qu’un répertoire), tous les enfants (par exemple, les sous-répertoires) sont également supprimés.  
  
 *Suppr*  
 facultatif. Valeur **booléenne** qui, lorsque la **valeur est true**, spécifie que l’opération de suppression est asynchrone.  
  
## <a name="remarks"></a>Notes  
 Les opérations sur l’objet représenté par cet **enregistrement** peuvent échouer après la fin de cette méthode. Après l’appel de **DeleteRecord**, l' **enregistrement** doit être fermé, car le comportement de l' **enregistrement** peut devenir imprévisible, en fonction du moment où le fournisseur met à jour l' **enregistrement** avec la source de données.  
  
 Si cet **enregistrement** a été obtenu à partir d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), les résultats de cette opération ne seront pas reflétés immédiatement dans le **Recordset**. Actualisez le **Recordset** en le fermant et en le réouvrant, ou en exécutant la méthode de [rerequête](../../../ado/reference/ado-api/requery-method.md) **Recordset** , la méthode [Update](../../../ado/reference/ado-api/update-method.md) ou la méthode [Resync](../../../ado/reference/ado-api/resync-method.md) .  
  
> [!NOTE]
>  Les URL utilisant le schéma http appellera automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Delete, méthode (collection Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete, méthode (collection Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
