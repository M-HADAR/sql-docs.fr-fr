---
title: sys. xml_schema_component_placements (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_component_placements
- xml_schema_component_placements_TSQL
- xml_schema_component_placements
- sys.xml_schema_component_placements_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_component_placements catalog view
ms.assetid: 2d3c8828-e4b3-423d-bf11-990464c1341b
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 0bab2cda409d5715e1f6b5519e1b760eb1cad9c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103372"
---
# <a name="sysxml_schema_component_placements-transact-sql"></a>sys.xml_schema_component_placements (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne par emplacement pour les composants de schéma XML.  
   
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|ID du composant de schéma XML propriétaire de l'emplacement.|  
|**placement_id**|**int**|ID de l'emplacement. Cet identificateur est unique au sein du composant de schéma XML propriétaire.|  
|**placed_xml_component_id**|**int**|ID du composant de schéma XML placé.|  
|**is_default_fixed**|**bit**|1 = La valeur par défaut est une valeur fixe. Cette valeur ne peut pas être substituée dans une instance XML.<br /><br /> 0 = la valeur peut être remplacée (option par défaut).|  
|**min_occurrences**|**int**|Le nombre minimal d'occurrences du composant placé est utilisé.|  
|**max_occurrences**|**int**|Le nombre maximal d'occurrences du composant placé est utilisé.|  
|**default_value**|**nvarchar (4000)**|Valeur par défaut si elle est fournie. NULL si une valeur par défaut n'est pas fournie.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Schémas XML &#40;les affichages catalogue du système de type XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
