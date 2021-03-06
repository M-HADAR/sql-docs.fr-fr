---
title: TopS (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 373fe2f1458b30412f4ee5852baa57b930af4878
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68893046"
---
# <a name="topsum-dmx"></a>TopSum (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne, dans l'ordre décroissant, les lignes supérieures d'une table dont le total cumulé est au moins égal à la valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TopSum(<table expression>, <rank expression>, <sum>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Expression qui retourne une table, telle qu’une référence \<de colonne de table>, ou une fonction qui retourne une table.  
  
## <a name="return-type"></a>Type de retour  
 \<expression de table>  
  
## <a name="remarks"></a>Notes  
 La fonction **Tops** retourne les lignes les plus hauts dans l’ordre décroissant de classement en fonction de la valeur évaluée de l' \<expression de classement> argument pour chaque ligne, de telle \<sorte que la somme de l’expression de classement> valeurs soit au moins égale \<au total spécifié par l’argument Sum>. **Tops** retourne le plus petit nombre d’éléments possible tout en respectant la valeur de somme spécifiée.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une requête de prédiction sur le modèle d’association que vous générez à l’aide du didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
 Pour comprendre comment fonctionne le pourcentage de fonctionnement, il peut être utile d’exécuter d’abord une requête de prédiction qui retourne uniquement la table imbriquée.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  Dans cet exemple, la valeur fournie en tant qu'entrée contient un guillemet simple et doit donc être placée dans une séquence d'échappement en la préfaçant avec un autre guillemet simple. Si vous n'êtes pas certain de la syntaxe permettant d'insérer un caractère d'échappement, vous pouvez utiliser le Générateur de requêtes de prédiction pour créer la requête. Lorsque vous sélectionnez la valeur dans la liste déroulante, le caractère d'échappement requis est inséré pour vous. Pour plus d’informations, consultez [créer une requête singleton dans le concepteur d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer).  
  
 Résultats de l’exemple :  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,291283016|0,252695851|  
|Water Bottle|2866|0,192620472|0,175205052|  
|Patch kit|2113|0,142012232|0,132389356|  
|Mountain Tire Tube|1992|0,133879965|0,125304948|  
|Mountain-200|1755|0,117951475|0,111260823|  
|Road Tire Tube|1588|0,106727603|0,101229538|  
|Cycling Cap|1473|0,098998589|0,094256014|  
|Fender Set - Mountain|1415|0,095100477|0,090718432|  
|Mountain Bottle Cage|1367|0,091874454|0,087780332|  
|Road Bottle Cage|1195|0,080314537|0,077173962|  
  
 La fonction **Tops** prend les résultats de cette requête et retourne les lignes avec les plus grandes valeurs qui se résument au nombre spécifié.  
  
```  
SELECT   
TopSum  
    (  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $PROBABILITY,  
    .5)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Le premier argument de la fonction **Tops** est le nom d’une colonne de table. Dans cet exemple, la table imbriquée est retournée en appelant la fonction Predict et en utilisant l’argument INCLUDE_STATISTICS.  
  
 Le deuxième argument de la fonction **Tops** est la colonne de la table imbriquée que vous utilisez pour classer les résultats. Dans cet exemple, l'option INCLUDE_STATISTICS retourne les colonnes $SUPPORT, $PROBABILTY et $ADJUSTED PROBABILITY. Cet exemple utilise $PROBABILITY pour retourner les lignes dont la somme est au moins égale à une probabilité de 50 %.  
  
 Le troisième argument de la fonction **Tops** spécifie la somme cible, sous la forme d’un double. Pour obtenir les lignes des produits principaux dont la somme est égale à une probabilité de 50 pour cent, tapez .5.  
  
 Résultats de l’exemple :  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,29...|0,25...|  
|Water Bottle|2866|0,19...|0,17...|  
|Patch kit|2113|0,14...|0,13...|  
  
 **Remarque** Cet exemple est fourni uniquement pour illustrer l’utilisation de **Tops**. L'exécution de cette requête peut prendre beaucoup de temps, en fonction de la taille de votre jeu de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [&#41;DMX &#40;](../dmx/toppercent-dmx.md)  
  
  
