---
title: Objet dimension (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension object [ADO MD]
ms.assetid: 66adbbd2-23a3-4c19-a91b-84c31309aa1b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f7a13ad87d56f5e7855070d8fe577bb408d6ce9e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938536"
---
# <a name="dimension-object-ado-md"></a>Dimension, objet (ADO MD)
Représente l’une des dimensions d’un cube multidimensionnel, contenant une ou plusieurs hiérarchies de membres.  
  
## <a name="remarks"></a>Notes  
 Avec les collections et les propriétés d’un objet **dimension** , vous pouvez effectuer les opérations suivantes :  
  
-   Identifiez la **dimension** avec les propriétés [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) et [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) .  
  
-   Retourne une chaîne significative qui décrit la **dimension** avec la propriété [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Retourne les objets [Hierarchy](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) qui composent la **dimension** avec la collection [Hierarchies](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md) .  
  
-   Utilisez la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) ADO standard pour obtenir des informations supplémentaires sur l’objet **dimension** .  
  
 La collection **Properties** contient des propriétés fournies par le fournisseur. Le tableau suivant répertorie les propriétés qui peuvent être disponibles. La liste de propriétés réelle peut varier en fonction de l’implémentation du fournisseur. Pour obtenir une liste plus complète des propriétés disponibles, consultez la documentation de votre fournisseur.  
  
|Name|Description|  
|----------|-----------------|  
|CatalogName|Nom du catalogue auquel appartient ce cube.|  
|CubeName|Nom du cube.|  
|DefaultHierarchy|Nom unique de la hiérarchie par défaut.|  
|Description|Description significative du cube.|  
|DimensionCaption|Étiquette ou légende associée à la dimension.|  
|DimensionCardinality|Nombre de membres dans la dimension.|  
|DimensionGUID|GUID de la dimension.|  
|DimensionName|Nom de la dimension.|  
|DimensionOrdinal|Numéro ordinal de la dimension dans le groupe de dimensions qui forment le cube.|  
|DimensionType|Type de dimension.|  
|DimensionUniqueName|Nom non ambigu de la dimension.|  
|SchemaName|Nom du schéma auquel appartient ce cube.|  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CubeDef, exemple (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [CubeDef, objet (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [Dimensions, collection (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Collections Hierarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
