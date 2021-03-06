---
title: CRÉER UNE STRUCTURE D’EXPLORATION DE DONNÉES (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 87b27f9e1c5927392b4ea221dcb6b7468a42ff9c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892823"
---
# <a name="create-mining-structure-dmx"></a>CREATE MINING STRUCTURE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Crée une structure d'exploration de données dans une base de données et, éventuellement, définit les partitions d'apprentissage et de test. Une fois que vous avez créé la structure d’exploration de données, vous pouvez utiliser l’instruction [ALTER Mining structure &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md) pour ajouter des modèles à la structure d’exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE [SESSION] MINING STRUCTURE <structure>  
(  
    [(<column definition list>)]  
)  
[WITH HOLDOUT (<holdout-specifier> [OR <holdout-specifier>])]  
[REPEATABLE(<holdout seed>)]  
<holdout-specifier>::=  <holdout-maxpercent> PERCENT | <holdout-maxcases> CASES  
```  
  
## <a name="arguments"></a>Arguments  
 *arborescence*  
 Nom unique de la structure.  
  
 *liste de définitions de colonnes*  
 Liste des définitions de colonnes séparées par des virgules.  
  
 *exclusion-MaxPercent*  
 Entier compris entre 1 et 100 qui indique le pourcentage de données à réserver au test.  
  
 *exclusion-MaxCases*  
 Entier qui indique le nombre maximal de cas à utiliser pour le test.  
  
 Si la valeur spécifiée pour le nombre maximal de cas est supérieure au nombre de cas d'entrée, tous les cas d'entrée sont utilisés pour le test et un avertissement est déclenché.  
  
> [!NOTE]  
>  Si le pourcentage et le nombre maximal de cas sont spécifiés, la plus petite des deux limites est utilisée.  
  
 *valeur initiale exclusion*  
 Entier utilisé comme valeur initiale pour commencer le partitionnement de données.  
  
 Si la valeur est 0, le hachage de l'ID de la structure d'exploration de données est utilisé comme valeur initiale.  
  
> [!NOTE]  
>  Vous devez spécifier une valeur initiale si vous devez vous assurer qu'une partition peut être reproduite.  
  
 Valeur par défaut : RÉPÉTABLE(0)  
  
## <a name="remarks"></a>Notes  
 Vous définissez une structure d'exploration de données en spécifiant une liste de colonnes, en spécifiant éventuellement des relations hiérarchiques entre les colonnes, puis en partitionnant éventuellement la structure d'exploration de données en jeux de données d'apprentissage et de test.  
  
 Le mot clé SESSION facultatif indique que la structure est une structure temporaire que vous pouvez utiliser uniquement pour la durée de la session active. Une fois la session terminée, la structure, ainsi que tous les modèles sur celle-ci, seront supprimés. Pour créer des modèles et des structures d’exploration de données temporaires, vous devez d’abord définir la propriété de base de données AllowSessionMiningModels,. Pour plus d’informations, consultez [Propriétés de l’exploration de données](https://docs.microsoft.com/analysis-services/server-properties/data-mining-properties).  
  
## <a name="column-definition-list"></a>Liste des définitions de colonnes  
 Pour définir une structure d'exploration de données, fournissez les informations suivantes pour chaque colonne de la liste des définitions de colonnes :  
  
-   Nom (obligatoire)  
  
-   Type de données (obligatoire)  
  
-   Distribution  
  
-   Liste des indicateurs de modélisation  
  
-   Type de contenu (obligatoire)  
  
-   Relation à une colonne d'attributs (obligatoire uniquement le cas échéant), indiquée par la clause RELATED TO.  
  
 Utilisez la syntaxe suivante pour la liste de définitions de colonnes pour définir une seule colonne :  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<column relationship>]  
```  
  
 Utilisez la syntaxe suivante pour la liste des définitions de colonne pour définir une colonne de table imbriquée :  
  
```  
<column name>    TABLE    ( <column definition list> )  
```  
  
 Pour la liste des types de données, types de contenu, distributions de colonnes et indicateurs de modélisation à utiliser pour définir une colonne de structure, consultez les rubriques suivantes :  
  
-   [Types de données &#40;&#41;d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-types-data-mining)  
  
-   [Types de contenu &#40;l’exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)  
  
-   [Distributions de colonnes &#40;&#41;d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/column-distributions-data-mining)  
  
-   [Indicateurs de modélisation &#40;&#41;d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/modeling-flags-data-mining)  
  
 Vous pouvez définir plusieurs valeurs d'indicateur de modélisation pour une colonne. Toutefois, vous ne pouvez avoir qu'un seul type de contenu et qu'un seul type de données pour une colonne.  
  
### <a name="column-relationships"></a>Relations de colonnes  
 Vous pouvez ajouter une clause à n'importe quelle instruction de définition de colonne pour décrire la relation entre deux colonnes. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]prend en charge l’utilisation de \<la clause de> de relation de colonne suivante.  
  
 **EN RAPPORT AVEC**  
 Indique une hiérarchie de valeur. La cible d'une colonne RELATED TO peut être une colonne clé dans une table imbriquée, une colonne de valeurs discrètes dans la ligne de cas ou une autre colonne RELATED TO qui indique une hiérarchie plus profonde.  
  
## <a name="holdout-parameters"></a>Paramètres d'exclusion  
 Lorsque vous spécifiez des paramètres d'exclusion, vous créez une partition des données de structure. Le montant que vous spécifiez pour l'exclusion est réservé pour le test, et les données restantes sont utilisées pour l'apprentissage. Par défaut, si vous créez une structure d'exploration de données à l'aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], la partition d'exclusion qui est créée contient 30 pour cent de données de test et 70 pour cent de données d'apprentissage. Pour plus d'informations, voir [Training and Testing Data Sets](https://docs.microsoft.com/analysis-services/data-mining/training-and-testing-data-sets).  
  
 Si vous créez une structure d'exploration de données à l'aide des extensions DMX (Data Mining Extensions), vous devez spécifier manuellement la création d'une partition d'exclusion.  
  
> [!NOTE]  
>  L’instruction **ALTER Mining structure** ne prend pas en charge exclusion.  
  
 Vous pouvez spécifier jusqu'à trois paramètres d'exclusion. Si vous spécifiez à la fois un nombre maximal de cas d'exclusion et un pourcentage d'exclusion, un pourcentage de cas est réservé jusqu'à ce que la limite de cas soit atteinte. Vous spécifiez le pourcentage de exclusion sous la forme d’un entier suivi du mot clé **percent** , puis vous spécifiez le nombre maximal de cas sous la forme d’un entier suivi du mot clé **cases** . Vous pouvez combiner les conditions dans n'importe quel ordre, comme le montrent les exemples suivants :  
  
```  
WITH HOLDOUT (20 PERCENT)   
WITH HOLDOUT (2000 CASES)   
WITH HOLDOUT (20 PERCENT OR 2000 CASES)   
WITH HOLDOUT (2000 CASES OR 20 PERCENT)  
```  
  
 La valeur initiale d'exclusion contrôle le point de départ du processus qui attribue aléatoirement les cas aux jeux de données d'apprentissage ou de test. En définissant une valeur initiale d'exclusion, vous pouvez vous assurer que la partition peut être répétée. Si vous ne spécifiez pas de valeur initiale d'exclusion, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise le nom de la structure d'exploration de données pour créer une valeur initiale. Si vous renommez la structure, la valeur initiale changera. Le paramètre de la valeur initiale d'exclusion peut être utilisé avec l'un ou l'autre des paramètres d'exclusion, ou les deux.  
  
> [!NOTE]  
>  Étant donné que les informations de partition sont mises en cache avec les données d’apprentissage, pour utiliser exclusion, vous devez vous assurer que la propriété **CacheMode** de la structure d’exploration de données est définie sur **KeepTrainingData**. Il s'agit du paramètre par défaut dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour les nouvelles structures d'exploration de données. La modification de la propriété **CacheMode** en **ClearTrainingCases** sur une structure d’exploration de données existante qui contient une partition exclusion n’affecte pas les modèles d’exploration de données qui ont été traités. Toutefois, si <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> n’a pas la valeur **KeepTrainingData**, les paramètres exclusion n’ont aucun effet. Cela signifie que toutes les données sources seront utilisées pour l'apprentissage et qu'aucun jeu de test ne sera disponible. La définition de la partition est mise en cache avec la structure ; si vous effacez le cache des cas d'apprentissage, vous effacez également le cache des données de test et la définition du jeu d'exclusion.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants montrent comment créer une structure d'exploration de données avec exclusion à l'aide de DMX.  
  
### <a name="example-1-adding-a-structure-with-no-training-set"></a>Exemple 1 : Ajout d'une structure sans jeu d'apprentissage  
 L'exemple suivant crée une structure d'exploration de données nommée `New Mailing` sans créer de modèle d'exploration de données associé et sans utiliser d'exclusion. Pour savoir comment ajouter un modèle d’exploration de données à la structure, consultez [ALTER Mining structure &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)  
```  
  
### <a name="example-2-specifying-holdout-percentage-and-seed"></a>Exemple 2 : Spécification d'un pourcentage et d'une valeur initiale d'exclusion  
 La clause suivante peut être ajoutée après la liste des définitions de colonnes pour définir un jeu de données qui peut être utilisé pour tester tous les modèles d'exploration de données associés à la structure d'exploration de données. L'instruction crée un jeu de test qui contient 25 % du nombre total de cas d'entrée, sans limite sur le nombre maximal de cas. La valeur 5 000 est utilisée comme valeur initiale pour la création de la partition. Lorsque vous spécifiez une valeur initiale, les mêmes cas sont choisis pour le jeu de test chaque fois vous traitez la structure d'exploration de données, tant que les données sous-jacentes ne changent pas.  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)   
WITH HOLDOUT(25 PERCENT) REPEATABLE(5000)  
```  
  
### <a name="example-3-specifying-holdout-percentage-and-max-cases"></a>Exemple 3 : Spécification du pourcentage d'exclusion et du nombre maximal de cas  
 La clause suivante crée un jeu de test qui contient soit 25 % du nombre total de cas d'entrée, soit 2 000 cas, la valeur la plus petite étant retenue. La valeur 0 étant spécifiée comme valeur initiale, le nom de la structure d'exploration de données est utilisé pour créer la valeur initiale utilisée pour commencer l'échantillonnage des cas d'entrée.  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)   
WITH HOLDOUT(25 PERCENT OR 2000 CASES) REPEATABLE(0)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
