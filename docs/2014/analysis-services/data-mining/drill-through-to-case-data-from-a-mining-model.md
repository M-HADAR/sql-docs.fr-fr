---
title: Extraction des données de cas à partir d’un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d683c9dc9a201b1f4351ee00d718ad0d7917606
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084609"
---
# <a name="drill-through-to-case-data-from-a-mining-model"></a>Extraire des données de cas à partir d'un modèle d'exploration de données
  Si un modèle d'exploration de données a été configuré pour vous autoriser à extraire des cas de modèles, lorsque vous parcourez le modèle, vous pouvez extraire des informations détaillées à propos des cas utilisés pour créer le modèle. De plus, si la structure d'exploration de données sous-jacente a été configurée pour autoriser l'extraction de cas de structure et que vous avez les autorisations appropriées, vous pouvez retourner des informations à partir de la structure d'exploration de données. Cela peut inclure des colonnes qui n'ont pas été incluses dans le modèle d'exploration de données.  
  
 Si la structure d'exploration de données ne vous autorise pas à extraire les données sous-jacentes, mais que le modèle d'exploration de données vous y autorise, vous pouvez afficher des informations des cas de modèle, mais pas de la structure d'exploration de données.  
  
> [!NOTE]  
>  Vous pouvez ajouter la possibilité d'extraire un modèle d'exploration de données existant en affectant la valeur `AllowDrillthrough` à la propriété `True`. Toutefois, après l'activation de l'extraction, le modèle doit être recyclé pour que vous puissiez afficher les données de cas. Pour plus d’informations, consultez [Activer l’extraction pour un modèle d’exploration de données](enable-drillthrough-for-a-mining-model.md).  
  
 Selon le type de visionneuse que vous utilisez, vous pouvez sélectionner le nœud pour effectuer une extraction des manières suivantes :  
  
|Nom de la visionneuse|Nom du volet ou de l'onglet|Sélection du nœud|  
|-----------------|----------------------|-----------------|  
|**Visionneuse d’arborescences Microsoft**|Onglet **arbre de décision**|Cliquez sur un nœud d'arborescence.<br /><br /> **Remarque** Évitez d’utiliser l’extraction `All` sur le nœud, car le renvoi des résultats peut prendre beaucoup de temps.|  
|**Visionneuse de clusters Microsoft**|**Diagramme de cluster**|Cliquez sur un nœud de cluster.|  
|**Visionneuse de clusters Microsoft**|**Profils de cluster**|Cliquez n'importe où dans la colonne de cluster.|  
|**Visionneuse d’associations Microsoft**|Onglet **règles**|Cliquez sur une ligne qui contient un ensemble de règles.|  
|**Visionneuse d’associations Microsoft**|Onglet **jeux d’éléments**|Cliquez sur une ligne qui contient un jeu d'éléments.|  
|**Visionneuse Microsoft Sequence Clustering**|Onglet **règles**|Cliquez sur une ligne qui contient un ensemble de règles.|  
|**Visionneuse Microsoft Sequence Clustering**|Onglet **jeux d’éléments**|Cliquez sur une ligne qui contient un jeu d'éléments.|  
  
> [!NOTE]  
>  Certains modèles ne peuvent pas utiliser la fonctionnalité d'extraction. La capacité à utiliser la fonctionnalité d'extraction dépend de l'algorithme qui a été utilisé pour créer le modèle. Pour obtenir une liste des types de modèles d’exploration de données qui prennent en charge l’extraction, consultez [Requêtes d’extraction &#40;exploration de données&#41;](drillthrough-queries-data-mining.md).  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>Pour afficher des données d'extraction à partir d'un modèle d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez la structure d'exploration de données qui contient le modèle d'exploration de données souhaité.  
  
2.  Dans le Concepteur d'exploration de données, cliquez sur l'onglet **Visionneuse de modèle d'exploration de données** .  
  
3.  Sélectionnez le modèle dans la liste déroulante **Modèle d’exploration de données** .  
  
4.  Dans la liste déroulante **Visionneuse** , sélectionnez une visionneuse, puis cliquez avec le bouton droit sur le nœud spécifique.  
  
5.  Sélectionnez **Extraire**, puis sélectionnez **Colonnes de modèle uniquement**ou **Colonnes de structure et de modèle** pour ouvrir la fenêtre **Extraire** .  
  
6.  Pour copier les données vers le Presse-papiers, cliquez avec le bouton droit sur une ligne dans la table et sélectionnez **Copier tout**.  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes d’extraction &#40;l’exploration de données&#41;](drillthrough-queries-data-mining.md)  
  
  
