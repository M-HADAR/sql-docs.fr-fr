---
title: Recommendation, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bcc0a95028b1f107f15752692d3dcad090fbe8b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62659577"
---
# <a name="recommendation-element-dta"></a>Recommendation, élément (Assistant Paramétrage de base de données)
  Contient des informations sur les index hypothétiques qui font partie d'une configuration spécifiée par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|facultatif. Peut être utilisé une seule fois pour chaque élément `Table`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Table, élément pour les schémas &#40;Assistant Paramétrage de base de données&#41;](table-element-for-schema-dta.md)|  
|**Éléments enfants**|[Create, élément &#40;Assistant Paramétrage de base de données&#41;](create-element-dta.md)<br /><br /> `Drop`appartient. Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="remarks"></a>Notes  
 Cet élément porte le nom **RecommendationTypecomplexType** dans le schéma XML de l’Assistant Paramétrage du moteur de base de données. Il est utilisé pour spécifier des index dans une configuration hypothétique. Ne confondez pas cet élément `Recommendation` avec les autres types d'éléments qui peuvent être utilisés pour spécifier le partitionnement (`RecommendationPType`) ou les vues (`RecommendationViewType`). Pour plus d’informations sur `Recommendation` ces autres types d’éléments, consultez la [Assistant Paramétrage du moteur de base de données schéma XML](https://go.microsoft.com/fwlink/?linkid=43100).  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez l’[Exemple de fichier d’entrée XML avec une configuration spécifiée par l’utilisateur &#40;Assistant Paramétrage de base de données&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
