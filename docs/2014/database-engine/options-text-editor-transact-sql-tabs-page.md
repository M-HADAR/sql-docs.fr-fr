---
title: Options (page éditeur de texte-Transact-SQL-onglets) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Tabs
dev_langs:
- TSQL
ms.assetid: a4499784-67f7-46ef-9f7c-2d0fdd117a52
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: cc649ee021012774a0f199b97ea3cbf6bae4adef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089134"
---
# <a name="options-text-editor---transact-sql---tabs-page"></a>Options (page éditeur de texte-Transact-SQL-onglets)
  Utilisez cette boîte de dialogue pour modifier le comportement de tabulation de l’Éditeur de requête [!INCLUDE[ssDE](../includes/ssde-md.md)], qui permet de programmer des scripts [!INCLUDE[tsql](../includes/tsql-md.md)]. Pour afficher ces paramètres, cliquez sur **Options** dans le menu **Outils**, développez le dossier **Éditeur de texte**, puis le sous-dossier **Transact-SQL**, et cliquez ensuite sur **Tabulations**.  
  
## <a name="setting-options-in-multiple-locations"></a>Définition d'options en plusieurs emplacements  
 Vous pouvez aussi définir les options de l’Éditeur de requête [!INCLUDE[ssDE](../includes/ssde-md.md)] dans la boîte de dialogue **Tous les langages Tabulations**. Si vous utilisez les boîtes de dialogue **tous les langages** pour définir des options [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] différentes pour les autres éditeurs, comme les éditeurs DMX ou MDX, vous [!INCLUDE[ssDE](../includes/ssde-md.md)] devez réinitialiser les options de l’éditeur de requête à l’aide de cette boîte de dialogue.  
  
## <a name="indenting"></a>Mise en retrait  
 **Aucun**  
 Lorsque cette option est activée, la nouvelle ligne créée grâce à la touche ENTRÉE n'est pas mise en retrait. Le curseur est placé au niveau de la première colonne de la nouvelle ligne.  
  
 **Plage**  
 Lorsque cette option est sélectionnée, la nouvelle ligne créée lorsque vous appuyez sur Entrée est automatiquement mise en retrait comme la ligne précédente.  
  
 **Intelligente**  
 Cette option n'est pas disponible.  
  
## <a name="tabs"></a>Onglets  
 **Taille des tabulation**  
 Définit la distance en espaces entre les taquets de tabulation. La valeur par défaut est quatre espaces.  
  
 **Taille du retrait**  
 Définit la taille en espaces d'une mise en retrait automatique. La valeur par défaut est quatre espaces. Des tabulations et/ou des espaces sont insérés pour occuper la taille spécifiée.  
  
 **Insérer des espaces**  
 Lorsque cette option est activée, les opérations de mise en retrait insèrent uniquement des espaces et non des tabulations. Si par exemple **taille du retrait** a la valeur 5, cinq espaces sont insérés à chaque fois que vous appuyez sur la touche Tab ou que vous cliquez sur le bouton augmenter le [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] **retrait** de la barre d’outils de la fenêtre principale.  
  
 **Conserver les tabulations**  
 Lorsque cette option est activée, les opérations de mise en retrait insèrent autant de tabulations que possible. Chaque tabulation remplit le nombre d'espaces spécifié dans **Taille de tabulation**. Si la valeur de **Taille du retrait** n'est pas un multiple pair de la valeur de **Taille de tabulation**, des espaces sont ajoutés pour remplir la différence.  
  
  
