---
title: Indicateurs de performance clés (KPI) dans les modèles multidimensionnels | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- viewing Key Performance Indicators
- Key Performance Indicators [Analysis Services]
- KPIs [Analysis Services]
- OLAP objects [Analysis Services], performance indicators
- weights [Analysis Services]
- displaying Key Performance Indicators
- parent KPIs [Analysis Services]
- child KPIs
ms.assetid: 73aee2da-da30-44f1-829c-0a4c078a7768
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 35482dc6206f0ad8807cb0f9a3e46902d14061ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074796"
---
# <a name="key-performance-indicators-kpis-in-multidimensional-models"></a>Indicateurs de performance clés (KPI) dans les modèles multidimensionnels
  Dans la terminologie d'entreprise, un indicateur de performance clé (KPI) est une mesure quantifiable des performances d'une activité économique.  
  
 Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], un KPI est un ensemble de calculs associés à un groupe de mesures dans un cube qui servent à évaluer les performances de l’entreprise. Généralement, ces calculs sont une combinaison d'expressions MDX (Multidimensional Expressions) ou de membres calculés. Les indicateurs de performance clés contiennent également des métadonnées supplémentaires qui fournissent des informations sur la manière dont les applications clientes doivent afficher les résultats des calculs d'un indicateur de performance clé.  
  
 Un indicateur de performance clé gère des informations à propos d'un ensemble d'objectifs, de la formule réelle de la performance enregistrée dans le cube et de la mesure utilisée pour afficher la tendance et l'état de la performance. AMO est utilisé pour définir les formules et d'autres définitions à propos des valeurs d'un indicateur de performance clé. Une interface de requête, telle qu'ADOMD.NET, est utilisée par l'application cliente pour récupérer et exposer les valeurs KPI à l'utilisateur final. Pour plus d’informations, consultez [Développement avec ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net).  
  
 Un objet <xref:Microsoft.AnalysisServices.Kpi> simple est composé d’informations de base, de l’objectif, de la valeur réelle atteinte, d’une valeur d’état, d’une valeur de tendance et d’un dossier où l’indicateur de performance clé est affiché. Les informations de base comprennent le nom et la description de l'indicateur de performance clé. L'objectif est une expression MDX qui prend la valeur d'un nombre. La valeur réelle est une expression MDX qui prend la valeur d'un nombre. Les valeurs d'état et de tendance sont des expressions MDX dont l'évaluation aboutit à un nombre. Le dossier est un emplacement suggéré pour l'indicateur de performance clé à présenter au client.  
  
 Dans la terminologie d'entreprise, un indicateur de performance clé (KPI) est une mesure quantifiable des performances d'une activité économique. Un KPI est fréquemment évalué dans le temps. Le service commercial d'une entreprise, par exemple, peut utiliser le bénéfice brut mensuel comme KPI, alors que le service Ressources Humaines de l'entreprise peut utiliser la rotation trimestrielle des employés. Chacun est un exemple de KPI. Les décideurs utilisent fréquemment des KPI qui sont regroupés dans un tableau de bord de l'entreprise pour obtenir une synthèse historique rapide et précise de l'activité.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], un indicateur de performance clé est une collection de calculs, qui sont associés à un groupe de mesures dans un cube, qui sont utilisés pour évaluer la réussite de l’entreprise. Généralement, ces calculs sont une combinaison d'expressions MDX (Multidimensional Expressions) et de membres calculés. Les indicateurs de performance clés contiennent également des métadonnées supplémentaires qui fournissent des informations sur la manière dont les applications clientes doivent afficher les résultats du calcul d'un indicateur de performance clé.  
  
 Un des avantages principaux des KPI dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est qu’ils sont basés sur le serveur et donc utilisables par différentes applications clientes. Les indicateurs de performance clés basés sur le serveur prennent en charge une version unique de la version de vérité comparé aux versions séparées de la vérité des applications clientes distinctes. De plus, le fait d'effectuer les calculs parfois complexes sur le serveur au lieu de les réaliser sur chaque ordinateur client peut améliorer les performances.  
  
## <a name="common-kpi-terms"></a>Termes KPI courants  
 Le tableau suivant fournit les définitions des termes couramment associés aux indicateurs de performance clés dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Terme|Définition|  
|----------|----------------|  
|Objectif|Une expression numérique MDX ou un calcul qui retourne la valeur cible de l'indicateur de performance clé.|  
|Valeur|Une expression numérique MDX qui retourne la valeur réelle de l'indicateur de performance clé.|  
|Statut|Une expression MDX qui représente l'état de l'indicateur de performance clé à un point spécifié dans le temps.<br /><br /> L'expression MDX d'état doit retourner une valeur normalisée comprise entre -1 et 1. Les valeurs inférieures ou égales à -1 sont considérées comme « mauvaises » ou « basses ». La valeur zéro (0) est considérée comme « acceptable » ou « moyenne ». Les valeurs supérieures ou égales à 1 sont considérées comme « bonnes » ou « élevées ».<br /><br /> Un nombre illimité de valeurs intermédiaires peut éventuellement être retourné, ces valeurs pouvant être utilisées pour afficher n'importe quel nombre d'états supplémentaires, si l'application cliente les prend en charge.|  
|Tendance|Une expression MDX qui évalue la valeur de l’indicateur de performance clé au fil du temps. La tendance peut être n'importe quel critère de temps utile dans un contexte d’entreprise spécifique.<br /><br /> L'expression MDX de tendance permet à un utilisateur professionnel de déterminer si le KPI s'améliore ou se dégrade au fil du temps.|  
|Indicateur d’état|Élément visuel qui fournit une indication rapide de l'état d'un KPI. L'affichage de l'élément est déterminé par la valeur de l'expression MDX qui évalue l'état.|  
|Indicateur de tendance|Élément visuel qui fournit une indication rapide de la tendance d'un KPI. L'affichage de l'élément est déterminé par la valeur de l'expression MDX qui évalue la tendance.|  
|Dossier d’affichage|Dossier dans lequel le KPI apparaît lorsqu'un utilisateur effectue un parcours du cube.|  
|Indicateur de performance clé parent|Référence à un KPI existant qui utilise la valeur du KPI enfant dans le cadre du calcul du KPI parent. Parfois, un seul KPI peut correspondre à un calcul qui se compose des valeurs d'autres KPI. Cette propriété facilite l'affichage correct des KPI enfants sous le KPI parent dans les applications clientes.|  
|Membre à l'heure actuelle|Expression MDX qui renvoie le membre qui identifie le contexte temporel du KPI.|  
|Poids|Expression numérique MDX qui affecte une importance relative à un KPI. Si le KPI est affecté à un KPI parent, le poids est utilisé pour ajuster proportionnellement les résultats de la valeur du KPI enfant lors du calcul de la valeur du KPI parent.|  
  
## <a name="parent-kpis"></a>KPI parents  
 Une entité peut suivre des mesures économiques différentes à différents niveaux. Par exemple, deux ou trois KPI peuvent être utilisés pour évaluer les performances économiques de l'ensemble de l'entreprise, mais ces KPI étendus à l'ensemble de l'entreprise peuvent être basés sur trois ou quatre autres KPI suivis par les différentes divisions de l'entreprise. En outre, les divisions de l'entreprise peuvent utiliser des statistiques différentes pour calculer un même KPI, le résultat étant cumulé avec le KPI étendu à l'entreprise.  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] permet de définir une relation parent-enfant entre les KPI. Cette relation parent-enfant permet d'utiliser les résultats du KPI enfant pour calculer les résultats du KPI parent. Les applications clientes peuvent également utiliser cette relation pour afficher de manière approximative les KPI parents et enfants.  
  
## <a name="weights"></a>Weights  
 Des poids peuvent également être affectés aux KPI enfants. Les poids permettent à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d'ajuster proportionnellement les résultats des KPI enfants lors du calcul du KPI parent.  
  
## <a name="retrieving-and-displaying-kpis"></a>Extraction et affichage des KPI  
 L'affichage des KPI dépend de l'implémentation de l'application cliente. Par exemple, le fait de sélectionner **Mode Navigateur** dans la barre d’outils de l’onglet **KPI** du Concepteur de cube constitue une implémentation cliente possible, avec des graphiques utilisés pour afficher les indicateurs d’état et de tendance, les dossiers d’affichage utilisés pour regrouper les KPI, ainsi que les KPI enfants sous les KPI parents.  
  
 Vous pouvez utiliser des fonctions MDX pour extraire des sections d'un KPI, telles que la valeur ou l'objectif, pour les utiliser dans des expressions, instructions et scripts MDX.  
  
  
