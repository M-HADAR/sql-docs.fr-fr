---
title: Référence aux fonctions d’agrégation (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: db6542ee-02d0-4073-90e6-cba8f9510fbb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f4c61c346452664557396032cb4ea14f89da66c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105333"
---
# <a name="aggregate-functions-reference-report-builder-and-ssrs"></a>Référence aux fonctions d'agrégation (Générateur de rapports et SSRS)
  Pour inclure des valeurs agrégées dans votre rapport, vous pouvez utiliser des fonctions d'agrégation intégrées dans des expressions. La fonction d'agrégation par défaut pour les champs de type numérique est SUM. Vous pouvez modifier l'expression et utiliser une fonction d'agrégation intégrée différente ou spécifier une étendue différente. L'étendue identifie le jeu de données à utiliser pour le calcul.  
  
 Les expressions de chaque élément de rapport sont évaluées à mesure que le processeur de rapports combine des données de rapport et la disposition de rapport. Lorsque vous consultez une page du rapport, vous affichez les résultats de chaque expression dans les éléments de rapport rendus.  
  
 Le tableau suivant répertorie les catégories de fonctions intégrées que vous pouvez inclure dans une expression :  
  
-   [Fonctions d’agrégation intégrées](#CalculatingAggregates)  
  
-   [Restrictions sur les champs prédéfinis, les collections et les fonctions d’agrégation](#Restrictions)  
  
-   [Restrictions sur les agrégats imbriqués](#NestedRestrictions)  
  
-   [Calcul des valeurs en cours d’exécution](#CalculatingRunningValues)  
  
-   [Récupération de nombres de lignes](#RetrievingRowCounts)  
  
-   [Recherche de valeurs à partir d’un autre jeu de données](#LookupFunctions)  
  
-   [Récupération de valeurs dépendantes du tri](#RetrievingPostsortValues)  
  
-   [Récupération des agrégats de serveur](#RetrievingServerAggregates)  
  
-   [Récupération du niveau récursif](#RetrievingRecursiveLevel)  
  
-   [Test de l’étendue](#TestingforScope)  
  
 Pour déterminer les étendues valides pour une fonction, consultez la rubrique de référence à la fonction en question Pour plus d’informations et pour obtenir des exemples, consultez [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="CalculatingAggregates"></a>Fonctions d’agrégation intégrées  
 Les fonctions intégrées suivantes calculent des valeurs résumées pour un jeu de données numériques non Null dans l'étendue par défaut ou l'étendue nommée.  
  
|**Fonctionnalités**|**Description**|  
|------------------|---------------------|  
|[AVG](report-builder-functions-avg-function.md)|Retourne la moyenne de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée dans l'étendue donnée.|  
|[Saut](report-builder-functions-count-function.md)|Retourne le nombre de valeurs non Null spécifiées par l'expression, évaluée dans le contexte de l'étendue donnée.|  
|[CountDistinct](report-builder-functions-countdistinct-function.md)|Retourne le nombre de toutes les valeurs non Null distinctes spécifiées par l'expression, évaluée dans le contexte de l'étendue donnée.|  
|[Max](report-builder-functions-max-function.md)|Retourne la valeur maximale de toutes les valeurs numériques non Null spécifiées par l'expression, dans le contexte de l'étendue donnée. Vous pouvez utiliser cette fonction pour spécifier une valeur maximale d'axe de graphique afin de contrôler l'échelle.|  
|[Min](report-builder-functions-min-function.md)|Retourne la valeur minimale de toutes les valeurs numériques non Null spécifiées par l'expression, dans le contexte de l'étendue donnée. Vous pouvez utiliser cette fonction pour spécifier une valeur minimale d'axe de graphique afin de contrôler l'échelle.|  
|[StDev](report-builder-functions-stdev-function.md)|Retourne l'écart type de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée dans l'étendue donnée.|  
|[StDevP](report-builder-functions-stdevp-function.md)|Retourne l'écart type de remplissage de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée dans le contexte de l'étendue donnée.|  
|[Checksum](report-builder-functions-sum-function.md)|Retourne la somme de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée dans l'étendue donnée.|  
|[UE](report-builder-functions-union-function.md)|Retourne l'union de toutes les valeurs de données spatiales non Null du type `SqlGeometry` ou `SqlGeography` spécifiées par l'expression, évaluées dans l'étendue donnée.|  
|[Var](report-builder-functions-var-function.md)|Retourne la variance de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée dans l'étendue donnée.|  
|[Var](report-builder-functions-varp-function.md)|Retourne la variance de remplissage de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée dans le contexte de l'étendue donnée.|  
  
##  <a name="Restrictions"></a>Restrictions sur les champs prédéfinis, les collections et les fonctions d’agrégation  
 Le tableau suivant résume les restrictions dans les emplacements de rapport où vous pouvez ajouter des expressions qui contiennent des références aux collections intégrées globales.  
  
|Emplacement dans le rapport|Champs|Paramètres|ReportItems|PageNumber<br /><br /> TotalPages|DataSource<br /><br /> DataSet|Variables|RenderFormat|  
|------------------------|------------|----------------|-----------------|-------------------------------|----------------------------|---------------|------------------|  
|En-tête de page<br /><br /> Pied de page|Oui|Oui|Un au plus<br /><br /> Remarque 1|Oui|Oui|Oui|Oui|  
|body|Oui<br /><br /> Remarque 2|Oui|Seuls les éléments dans l'étendue active ou une étendue contenante<br /><br /> Remarque 3|Non|Oui|Oui|Oui|  
|Paramètre de rapport|Non|Seuls les premiers paramètres dans la liste<br /><br /> Remarque 4|Non|Non|Non|Non|Non|  
|Champ|Oui|Oui|Non|Non|Non|Non|Non|  
|Paramètre de requête|Non|Oui|Non|Non|Non|Non|Non|  
|Expression de groupe|Oui|Oui|Non|Non|Oui|Non|Non|  
|Expression de tri|Oui|Oui|Non|Non|Oui|Oui<br /><br /> Remarque 5|Non|  
|Expression de filtre|Oui|Oui|Non|Non|Oui|Oui<br /><br /> Remarque 6|Non|  
|Code|Non|Oui<br /><br /> Remarque 7|Non|Non|Non|Non|Non|  
|Report.Language|Non|Oui|Non|Non|Non|Non|Non|  
|Variables|Oui|Oui|Non|Non|Oui|Étendue active ou contenante|Non|  
|Agrégats|Oui|Oui|Uniquement dans l'en-tête de page/le pied de page|Uniquement dans les agrégats d'élément de rapport|Oui|Non|Non|  
|Fonctions de recherche|Oui|Oui|Oui|Non|Oui|Non|Non|  
  
-   **Remarque 1.** ReportItems doit exister dans la page de rapport rendue, sinon sa valeur est Null. Si la visibilité d'un élément de rapport dépend d'une expression qui prend la valeur False, l'élément de rapport n'existe pas dans la page.  
  
-   **Remarque 2.** Si une référence de champ est utilisée dans une étendue de groupe et que cette référence n'est pas incluse dans l'expression de groupe, la valeur du champ n'est pas définie, sauf s'il existe une seule valeur dans l'étendue. Pour spécifier une valeur, utilisez la fonction First ou Last et l'étendue du groupe.  
  
-   **Remarque 3.** Les expressions qui incluent une référence à ReportItems peuvent spécifier des valeurs pour d'autres éléments ReportItems dans la même étendue de groupe ou dans une étendue de groupe contenante.  
  
-   **Remarque 4.** Les valeurs de propriété des premiers paramètres peuvent être Null.  
  
-   **Remarque 5.** Dans les tris Membres uniquement. Utilisation impossible dans les expressions de tri de la région de données.  
  
-   **Remarque 6.** Dans les filtres Membres uniquement. Utilisation impossible dans la région de données ou les expressions de filtre de dataset.  
  
-   **Remarque 7.** La collection Parameters n'est pas initialisée tant que le bloc de code n'a pas été traité afin que les méthodes ne puissent pas être utilisées pour contrôler des paramètres lors de l'initialisation.  
  
-   **Remarque 8.** Le type de données de tous les agrégats à l'exception de Count et CountDistinct doit être le même, ou Null, pour toutes les valeurs.  
  
##  <a name="NestedRestrictions"></a>Restrictions sur les agrégats imbriqués  
 Le tableau suivant résume les restrictions concernant les fonctions d'agrégation qui peuvent spécifier d'autres fonctions d'agrégation comme agrégats imbriqués.  
  
|Context|RunningValue|RowNumber|Premier<br /><br /> Dernier|Précédent|Sum et autres fonctions Presort|Agrégats ReportItem|Fonctions de recherche|Fonction d'agrégation|  
|-------------|------------------|---------------|--------------------|--------------|-------------------------------------|---------------------------|----------------------|------------------------|  
|Valeur d'exécution|Non|Non|Non|Non|Oui|Non|Oui|Non|  
|Premier<br /><br /> Dernier|Non|Non|Non|Non|Oui|Non|Non|Non|  
|Précédent|Oui|Oui|Oui|Non|Oui|Non|Oui|Non|  
|Sum et autres fonctions Presort|Non|Non|Non|Non|Oui|Non|Oui|Non|  
|Agrégats ReportItem|Non|Non|Non|Non|Non|Non|Non|Non|  
|Fonctions de recherche|Oui|Oui<br /><br /> Remarque 1|Oui<br /><br /> Remarque 1|Oui<br /><br /> Remarque 1|Oui<br /><br /> Remarque 1|Oui<br /><br /> Remarque 1|Non|Non|  
|Fonction d'agrégation|Non|Non|Non|Non|Non|Non|Non|Non|  
  
-   **Remarque 1.** Les fonctions d’agrégation sont autorisées uniquement à l’intérieur de l’expression *Source* d’une fonction Lookup si cette dernière n’est pas contenue dans un agrégat. Les fonctions d'agrégation ne sont pas autorisées à l'intérieur des expressions *Destination* ou *Result* d'une fonction Lookup.  
  
##  <a name="CalculatingRunningValues"></a>Calcul des valeurs en cours d’exécution  
 Les fonctions intégrées suivantes calculent des valeurs d'exécution pour un jeu de données. 
  `RowNumber` est semblable à `RunningValue` en ce sens qu'il retourne la valeur d'exécution d'un nombre qui s'incrémente pour chaque ligne de l'étendue contenante. Le paramètre d'étendue de ces fonctions doit spécifier une étendue contenante, laquelle contrôle le moment où le nombre redémarre.  
  
|**Fonctionnalités**|**Description**|  
|------------------|---------------------|  
|[RowNumber](report-builder-functions-rownumber-function.md)|Retourne un nombre évolutif du nombre de lignes pour l'étendue spécifiée. La fonction `RowNumber` redémarre le comptage à 1, et non à 0.|  
|[RunningValue](report-builder-functions-runningvalue-function.md)|Retourne un agrégat cumulé de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée pour l'étendue donnée.|  
  
##  <a name="RetrievingRowCounts"></a>Récupération de nombres de lignes  
 La fonction intégrée suivante calcule le nombre de lignes d'une étendue donnée. Utilisez-la pour compter toutes les lignes, y compris celles contenant des valeurs Null.  
  
|**Fonctionnalités**|**Description**|  
|------------------|---------------------|  
|[CountRows](report-builder-functions-countrows-function.md)|Retourne le nombre de lignes dans l'étendue spécifiée, y compris celles contenant des valeurs Null.|  
  
##  <a name="LookupFunctions"></a>Recherche de valeurs à partir d’un autre jeu de données  
 Les fonctions de recherche suivantes récupèrent des valeurs à partir d'un dataset spécifié.  
  
|**Fonctionnalités**|**Description**|  
|------------------|---------------------|  
|[Fonction Lookup](report-builder-functions-lookup-function.md)|Retourne une valeur à partir d'un dataset pour une expression spécifiée.|  
|[Fonction LookupSet](report-builder-functions-lookupset-function.md)|Retourne un ensemble de valeurs à partir d'un dataset pour une expression spécifiée.|  
|[Fonction Multilookup](report-builder-functions-multilookup-function.md)|Retourne le jeu de valeurs de première correspondance pour un ensemble de noms à partir d'un dataset contenant des paires nom/valeur.|  
  
##  <a name="RetrievingPostsortValues"></a>Récupération de valeurs dépendantes du tri  
 Les fonctions intégrées suivantes retournent la première valeur, la dernière valeur ou la valeur précédente dans une étendue donnée. Ces fonctions dépendent de l'ordre de tri des valeurs de données. Utilisez ces fonctions pour, par exemple, rechercher les première et dernière valeurs d'une page afin de créer un en-tête de page de type dictionnaire. Utilisez `Previous` pour comparer une valeur d'une ligne avec la valeur de la ligne précédente dans une étendue spécifique pour, par exemple, rechercher des valeurs d'une année sur l'autre en pourcentage dans une table.  
  
|**Fonctionnalités**|**Description**|  
|------------------|---------------------|  
|[Premier](report-builder-functions-first-function.md)|Retourne la première valeur dans l'étendue donnée de l'expression spécifiée.|  
|[Famille](report-builder-functions-last-function.md)|Retourne la dernière valeur dans l'étendue donnée de l'expression spécifiée.|  
|[Premier](report-builder-functions-previous-function.md)|Retourne la valeur ou la valeur d'agrégation spécifiée pour l'instance précédente d'un élément dans l'étendue spécifiée.|  
  
##  <a name="RetrievingServerAggregates"></a>Récupération des agrégats de serveur  
 La fonction intégrée suivante récupère des agrégats personnalisés du fournisseur de données. Par exemple, un type de la source de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vous permet d'extraire des agrégats calculés sur le serveur de source de données pour une utilisation dans un en-tête de groupe.  
  
|**Fonctionnalités**|**Description**|  
|------------------|---------------------|  
|[Rassemble](report-builder-functions-aggregate-function.md)|Retourne un agrégat personnalisé de l'expression spécifiée, comme défini par le fournisseur de données.|  
  
##  <a name="TestingforScope"></a>Test de l’étendue  
 La fonction intégrée suivante teste le contexte actuel d'un élément de rapport pour voir s'il est membre d'une étendue spécifique.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[InScope](report-builder-functions-inscope-function.md)|Indique si l'instance active d'un élément se trouve dans l'étendue spécifiée.|  
  
##  <a name="RetrievingRecursiveLevel"></a>Récupération du niveau récursif  
 La fonction intégrée suivante récupère le niveau actuel lorsqu'une hiérarchie récursive est traitée. Utilisez le résultat de cette fonction avec la propriété `Padding` dans une zone de texte pour contrôler le niveau de retrait d'une hiérarchie visuelle pour un groupe récursif. Pour plus d’informations, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Level](report-builder-functions-level-function.md)|Retourne le niveau de profondeur actuel d'une hiérarchie récursive.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
