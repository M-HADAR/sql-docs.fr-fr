---
title: Partitions (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- incremental updates [Analysis Services]
- data sources [Analysis Services], partitions
- data storage [Analysis Services]
- aggregations [Analysis Services], partitions
- OLAP objects [Analysis Services], partitions
- storing data [Analysis Services], partitions
- partitions [Analysis Services], about partitions
- cubes [Analysis Services], partitions
- partitions [Analysis Services]
- remote partitions [Analysis Services]
- measure groups [Analysis Services], partitions
ms.assetid: cd10ad00-468c-4d49-9f8d-873494d04b4f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 47a7b4c2b11a6d17a52af20aef71ee13863ea29c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702616"
---
# <a name="partitions-analysis-services---multidimensional-data"></a>Partitions (Analysis Services - Données multidimensionnelles)
  Une partition est un conteneur d'une portion des données d'un groupe de mesures. Les partitions ne sont pas considérées comme des requêtes MDX ; toutes les requêtes reflètent le contenu entier du groupe de mesures, indépendamment du nombre de partitions défini pour le groupe de mesures. Le contenu des données d'une partition est défini par les liaisons de requête de la partition et par l'expression de découpage.  
  
 Un objet <xref:Microsoft.AnalysisServices.Partition> simple est composé des informations de base, de la définition de découpage, de la conception d'agrégation et d'autres données. Les informations de base incluent le nom de la partition, le mode de stockage, le mode de traitement et d'autres informations. La définition de découpage est une expression MDX qui spécifie un tuple ou un jeu. La définition de découpage a les mêmes restrictions que la fonction MDX StrToSet. Avec le paramètre CONSTRAINED, la définition de découpage peut utiliser la dimension, la hiérarchie, les noms de niveau et de membre, les clés, les noms uniques ou d'autres objets nommés dans le cube, mais ne peut pas utiliser de fonctions MDX. La conception d'agrégation est une collection de définitions d'agrégation qu'il est possible de partager sur plusieurs partitions dans une base de données. La valeur par défaut est prise de la conception d'agrégation du cube parent.  
  
 Les partitions sont utilisées par [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour gérer et stocker des données et des agrégations pour un groupe de mesures dans un cube. Chaque groupe de mesures possède au moins une partition qui est créée lors de la définition du groupe de mesures. Lorsque vous créez une nouvelle partition pour un groupe de mesures, celle-ci s'ajoute à l'ensemble de partitions existant déjà pour ce groupe de mesures. Le groupe de mesures reflète la combinaison des données contenues dans l'ensemble de ses partitions. Vous devez donc veiller à ce que les données d'une partition dans un groupe de mesures ne contiennent pas les données d'une autre partition du groupe de mesures. Ainsi, les données ne figurent qu'une seule fois dans le groupe de mesures. La partition d'origine d'un groupe de mesures est basée sur une table de faits unique dans la vue de source de données du cube. Lorsqu'un groupe de mesures comporte plusieurs partitions, chacune d'entre elles peut faire référence à une table différente, soit de la vue de source de données, soit de la source de données relationnelles sous-jacente du cube. Plusieurs partitions d'un même groupe de mesures peuvent faire référence à la même table à condition de limiter chaque partition à différentes lignes de la table.  
  
 Les partitions constituent un outil puissant et souple permettant de gérer les cubes, en particulier s'ils sont volumineux. Par exemple, un cube qui contient des informations sur les ventes peut réserver une partition pour les données de chaque année écoulée et utiliser d'autres partitions pour chaque trimestre de l'année en cours. Seule la partition du trimestre en cours doit être traitée si des informations sont ajoutées à un cube ; le traitement d'une plus petite quantité de données réduit le temps de traitement et améliore donc les performances de traitement. À la fin de l'année, les quatre partitions pour les trimestres peuvent être fusionnées dans une seule partition pour l'année et une nouvelle partition peut être créée pour le premier trimestre de l'année suivante. En outre, la création de cette partition peut être automatisée dans le cadre des procédures de chargement de l'entrepôt de données et de traitement du cube.  
  
 Les utilisateurs professionnels d'un cube ne peuvent pas voir les partitions. Par contre, les administrateurs peuvent configurer, ajouter ou supprimer des partitions. Chaque partition est stockée dans un jeu de fichiers distinct. Les données agrégées de chaque partition peuvent être stockées sur l'instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans laquelle la partition est définie, sur une autre instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ou dans la source de données qui fournit les données sources de la partition. Les partitions permettent de répartir les données sources et les données agrégées d'un cube sur plusieurs disques durs et sur plusieurs serveurs. Pour un cube de taille moyenne à grande, les partitions peuvent considérablement améliorer l'efficacité des requêtes, les performances de chargement et la facilité de maintenance du cube. Pour plus d’informations sur les partitions distantes, consultez [Partitions distantes](partitions-remote-partitions.md).  
  
 Le mode de stockage de chaque partition peut être configuré indépendamment des autres partitions du groupe de mesures. Les partitions peuvent être stockées à l'aide de différentes combinaisons d'options en ce qui concerne l'emplacement des données sources, le mode de stockage, la mise en cache proactive et la conception d'agrégation. Grâce au traitement analytique en ligne (OLAP) en temps réel et à la mise en cache proactive, il est possible d'équilibrer vitesse des requêtes et latence lors de la création d'une partition. Les options de stockage peuvent aussi être appliquées à des dimensions associées et à des faits d'un groupe de mesures. Cette souplesse vous permet de créer des stratégies de stockage de cube appropriées à vos besoins. Pour plus d’informations, consultez [partitionnement et modes de stockage des partitions](partitions-partition-storage-modes-and-processing.md), [agrégations et conceptions d’agrégation](aggregations-and-aggregation-designs.md) et [mise en cache proactive &#40;partitions&#41;](partitions-proactive-caching.md).  
  
## <a name="partition-structure"></a>Structure des partitions  
 La structure d'une partition doit correspondre à la structure de son groupe de mesures. Les mesures qui définissent le groupe de mesures doivent donc également être définies dans la partition, ainsi que toutes les dimensions associées. Ainsi, au moment de sa création, une partition hérite automatiquement de l'ensemble de mesures et de dimensions associées qui a été défini pour son groupe de mesures.  
  
 Cependant, chaque partition d'un groupe de mesures peut posséder une table de faits différente provenant de différentes sources de données. Lorsque des partitions différentes d'un groupe de mesures possèdent des tables de faits différentes, les tables doivent être suffisamment semblables pour conserver la structure du groupe de mesures. La requête de traitement retourne donc les mêmes colonnes et les mêmes types de données pour toutes les tables de faits de toutes les partitions.  
  
 Lorsque les tables de faits de différentes partitions proviennent de différentes sources de données, les tables sources des éventuelles dimensions associées et des tables de faits intermédiaires doivent également se trouver dans toutes les sources de données et avoir la même structure dans toutes les bases de données. Par ailleurs, toutes les colonnes de tables de dimension utilisées pour définir les attributs des dimensions du cube associées au groupe de mesures doivent être présentes dans toutes les sources de données. Il n'est pas nécessaire de définir toutes les jointures entre la table source d'une partition et une table de dimension associée si la table source de la partition a la même structure que la table source du groupe de mesures.  
  
 Les colonnes qui n'ont pas servi à définir les mesures du groupe de mesures peuvent être présentes dans certaines tables de faits, mais absentes dans d'autres. De même, les colonnes qui n'ont pas servi à définir les attributs des tables des dimensions associées peuvent être présentes dans certaines bases de données, mais absentes dans d'autres. Des tables qui ne sont utilisées ni pour les tables de faits, ni pour les tables des dimensions associées, peuvent être présentes dans certaines bases de données, mais absentes dans d'autres.  
  
## <a name="data-sources-and-partition-storage"></a>Sources de données et stockage des partitions  
 Une partition est basée soit sur une table, soit sur une vue dans une source de données, ou sur une table ou une requête nommée dans une vue de source de données. L'emplacement dans lequel sont stockées les données d'une partition est défini par la liaison de la source de données. En règle générale, vous pouvez partitionner un groupe de mesures horizontalement ou verticalement :  
  
-   Dans un groupe de mesures partitionné horizontalement, chaque partition du groupe de mesures est basée sur une table distincte. Ce type de partitionnement convient lorsque les données sont réparties dans plusieurs tables. Par exemple, certaines bases de données relationnelles contiennent une table distincte pour chaque mois.  
  
-   Dans un groupe de mesures partitionné verticalement, le groupe de mesures est basé sur une table unique, par conséquent chaque partition est basée sur une requête système source qui filtre les données pour la partition. Par exemple, si une table unique contient les données de plusieurs mois, le groupe de mesures peut quand même être partitionné par mois en appliquant une clause WHERE Transact-SQL qui renvoie des données mensuelles distinctes pour chaque partition.  
  
 Chaque partition possède des paramètres de stockage qui déterminent si les données et les agrégations de la partition sont stockées dans l'instance locale d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou dans une partition distante d'une autre instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les paramètres de stockage permettent également de spécifier le mode de stockage et d'indiquer si la mise en cache proactive est utilisée pour contrôler la latence d'une partition. Pour plus d’informations, consultez [partitionnement et modes de stockage des partitions](partitions-partition-storage-modes-and-processing.md), [mise en cache proactive &#40;les partitions&#41;](partitions-proactive-caching.md)et les [partitions distantes](partitions-remote-partitions.md).  
  
## <a name="incremental-updates"></a>Mises à jour incrémentielles  
 Lorsque vous créez et gérez des partitions dans des groupes de mesures à partitions multiples, vous devez observer certaines précautions pour préserver la cohérence des données du cube. Bien que ces précautions ne concernent généralement pas les groupes de mesures à partition unique, elles s'appliquent lorsque vous procédez à une mise à jour incrémentielle des partitions. Lors de la mise à jour incrémentielle d'une partition, une nouvelle partition temporaire présentant une structure identique à celle de la partition source est créée. Cette partition temporaire est traitée, puis fusionnée avec la partition source. Par conséquent, vous devez vérifier que la requête de traitement qui peuple la partition temporaire ne duplique pas les données déjà présentes dans une partition existante.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés de mesure](../multidimensional-models/configure-measure-properties.md)   
 [Cubes dans les modèles multidimensionnels](../multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
