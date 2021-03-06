---
title: Volet Résultats (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- result sets [SQL Server], queries
- synchronization [SQL Server], query results with definition
- displaying query results in grid
- grid showing query results [SQL Server]
- showing query results in grid
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- viewing query results
- queries [SQL Server], results
- Results pane
ms.assetid: 6309a1bc-a628-4141-8bb5-b35924bd19f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 87bfaef1ad5dc4c9b1f907c27955ca3f156038a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067805"
---
# <a name="results-pane-visual-database-tools"></a>Volet Résultats (Visual Database Tools)
  Le volet Résultats montre les résultats de la dernière requête SELECT exécutée. (Les résultats des autres types de requêtes sont affichés dans des boîtes de messages.) Pour ouvrir le volet Résultats, ouvrez ou créez une requête ou encore une vue, ou retournez les données d'une table. Si le volet Résultats ne s'affiche pas par défaut, dans le menu **Concepteur de requêtes** , pointez sur **Volet**, puis cliquez sur **Résultats**.  
  
## <a name="what-you-can-do-in-the-results-pane"></a>Actions autorisées dans le volet Résultats  
  
-   Afficher l'ensemble des résultats de la dernière requête SELECT exécutée dans une grille de type feuille de calcul.  
  
-   Pour les requêtes ou les vues affichant des données qui proviennent d'une table ou vue unique, vous pouvez modifier les valeurs dans les différentes colonnes du jeu de résultats, ajouter de nouvelles lignes et supprimer des lignes existantes.  
  
## <a name="limitations-in-the-results-pane"></a>Limitations dans le volet Résultats  
  
-   Les résultats retournés par les fonctions table ne peuvent être mis à jour que dans certains cas.  
  
-   Les requêtes ou vues qui comprennent des colonnes provenant de plusieurs tables ou vues ne peuvent pas être mises à jour.  
  
-   Les résultats retournés par une procédure stockée ne peuvent pas être mis à jour.  
  
-   Les requêtes ou vues utilisant des clauses GROUP BY or DISTINCT ne peuvent pas être mises à jour.  
  
## <a name="navigating-in-the-results-pane"></a>Navigation dans le volet Résultats  
 Vous pouvez naviguer rapidement au sein des enregistrements à l'aide de la barre de navigation située au bas du volet Résultats.  
  
 Vous disposez de boutons permettant d'accéder aux premiers et aux derniers enregistrements, aux enregistrements suivants et précédents, ainsi qu'à un enregistrement particulier.  
  
 Pour accéder à un enregistrement particulier, tapez le numéro de la ligne dans la zone de texte située dans la barre de navigation, puis appuyez sur ENTRÉE.  
  
 Pour plus d’informations sur l’utilisation des raccourcis clavier dans le Concepteur de requêtes et de vues, consultez [Naviguer dans le Concepteur de requêtes et de vues &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a>Préserver la synchronisation du jeu de résultats avec la définition de la requête  
 Lorsque vous travaillez sur les résultats d'une requête ou d'une vue, il est possible que les enregistrements du volet Résultats ne soient plus synchronisés avec la définition de la requête. Par exemple, si vous exécutez une requête pour quatre des cinq colonnes dans une table, puis utilisez le volet Schéma pour ajouter la cinquième colonne à la définition de la requête, les données de cette cinquième colonne ne seront pas automatiquement ajoutées au volet Résultats. Pour que le volet Résultats reflète la nouvelle définition de requête, exécutez à nouveau la requête.  
  
 Si une requête est modifiée, une icône d'alerte avec le texte « Requête modifiée » apparaît dans le coin inférieur droit du volet Résultats. L'icône apparaît également dans le coin supérieur gauche du volet.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des requêtes &#40;Visual Database Tools&#41;](create-queries-visual-database-tools.md)   
 [Exécuter des requêtes &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md)   
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Volet Schéma &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md)   
 [Volet critères &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md)   
 [Utiliser des données du volet de résultats &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)  
  
  
