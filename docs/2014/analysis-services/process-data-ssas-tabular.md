---
title: Traiter des données (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d88f2dc9-2933-4be5-9bf3-48ffbc2d0a1a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a0ca45681866e0ba96edaa81c21445a89f94275
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070699"
---
# <a name="process-data-ssas-tabular"></a>Traiter les données (SSAS Tabulaire)
  Lorsque vous importez des données dans un modèle tabulaire, en mode mis en cache, vous capturez un instantané de ces données au moment de l'importation. Dans certains cas, ces données peuvent ne jamais changer et elles n'ont pas besoin d'être mises à jour dans le modèle. Toutefois, il est plus probable que les données que vous importez subissent des modifications régulièrement, et pour que votre modèle reflète les données les plus récentes des sources de données, il est nécessaire de traiter (actualiser) ces données et de recalculer les données calculées. Pour mettre à jour les données dans votre modèle, effectuez une action de traitement sur toutes les tables, sur une table individuelle, par partition ou par connexion de source de données.  
  
 Lors de la création de votre projet de modèle, toutes les actions de traitement doivent être initiées manuellement dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Une fois qu'un modèle a été déployé, les opérations de traitement peuvent être effectuées en utilisant [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou planifiées à l'aide d'un script. Les tâches décrites ici concernent toutes des actions de traitement que vous pouvez effectuer pendant la création de modèles dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour plus d'informations sur les actions de traitement pour un modèle déployé, consultez [Process Database, Table, or Partition](tabular-models/process-database-table-or-partition-analysis-services.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Traiter manuellement les données &#40;tabulaires SSAS&#41;](manually-process-data-ssas-tabular.md)|Explique comment traiter manuellement des données de l'espace de travail de modèle.|  
|[Résoudre les problèmes liés aux données de processus &#40;&#41;SSAS tabulaire](troubleshoot-process-data-ssas-tabular.md)|Explique comment résoudre les problèmes liés aux opérations de traitement.|  
  
  
