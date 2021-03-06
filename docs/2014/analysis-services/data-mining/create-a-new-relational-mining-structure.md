---
title: Créer une structure d’exploration de données relationnelle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], relational
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4ec4bc871723b829d9ce9ec805d4b52b1c649e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66085390"
---
# <a name="create-a-new-relational-mining-structure"></a>créer une structure d'exploration de données relationnelle
  Utilisez l’Assistant Exploration de données pour créer une nouvelle structure d’exploration de données, en utilisant les données d’une base de données relationnelle ou d’une autre source, puis [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enregistrer la structure et tous les modèles associés dans une base de données.  
  
### <a name="to-create-a-relational-mining-structure"></a>Pour créer une structure d'exploration de données relationnelle  
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier **Structures d’exploration de données** d’un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis cliquez sur **Nouvelle structure d’exploration de données**.  
  
     L'Assistant Exploration de données s'ouvre.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner la méthode de définition** , sélectionnez **À partir d'une base de données relationnelles ou d'un entrepôt de données qui existent déjà**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Sélectionner la technique d’exploration de données** , sélectionnez l’algorithme d’exploration de données à utiliser, puis cliquez sur **Suivant**.  
  
     Pour plus d’informations sur les algorithmes d’exploration de données, consultez [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md).  
  
5.  Dans la page **Sélectionner une vue de source de données** , sous **Vues de sources de données disponibles**, cliquez sur la vue de source de données à utiliser, puis cliquez sur **Suivant**.  
  
     Pour plus d’informations sur la création d’une vue de source de données, consultez [Vues de sources de données dans les modèles multidimensionnels](../multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
6.  Dans la page **Spécifier les types des tables** sous **Tables d’entrée**, sélectionnez une table de cas et une table imbriquée.  
  
7.  Dans la page **Spécifier les données d’apprentissage** , sous **Structure du modèle d’exploration de données**, sélectionnez les colonnes clés, d’entrée et prédictibles.  
  
     Après avoir sélectionné la colonne prédictible, cliquez sur le bouton **Suggérer** pour ouvrir la boîte de dialogue **Suggérer des colonnes associées** . Vous pouvez accepter les colonnes suggérées en cliquant sur **OK** dans cette boîte de dialogue pour inclure les colonnes sélectionnées dans la structure d’exploration de données, ou vous pouvez changer les sélections dans la colonne **Entrée** , puis cliquer sur **OK**. Pour ignorer les suggestions, cliquez sur **Annuler**.  
  
8.  Cliquez sur **Suivant**.  
  
9. Dans la page **Spécifier le type de contenu et de données des colonnes** , sous **Structure du modèle d’exploration de données**, vous pouvez définir le type de contenu et le type de données de chaque colonne.  
  
    > [!NOTE]  
    >  Cliquez sur **Détecter** pour détecter automatiquement si une colonne contient des données continues ou des données discrètes. Après avoir cliqué sur ce bouton, le type de contenu et le type de données sont mis à jour dans les colonnes **Type de contenu** et **Type de données** . Pour plus d’informations sur les types de contenu et les types de données, consultez [Types de contenu &#40;Exploration de données&#41;](content-types-data-mining.md) et [Types de données &#40;Exploration de données&#41;](data-types-data-mining.md).  
  
10. Cliquez sur **Suivant**.  
  
11. Dans la page **Fin de l'Assistant** , entrez le nom de la structure d’exploration de données et le modèle d’exploration de données associé initial à créer, puis cliquez sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la structure d'exploration de données et procédures](mining-structure-tasks-and-how-tos.md)  
  
  
