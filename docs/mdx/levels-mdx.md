---
title: Niveaux (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 24e15602593f9116d499345ffca093f86ecfa135
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905642"
---
# <a name="levels-mdx"></a>Levels (MDX)


  Retourne le niveau dont la position dans une dimension ou une hiérarchie est spécifiée par une expression numérique ou dont le nom est spécifié par une expression de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Level_Number*  
 Expression numérique valide qui spécifie un numéro de niveau.  
  
 *Level_Name*  
 Expression de chaîne valide qui spécifie un nom de niveau.  
  
## <a name="remarks"></a>Notes  
 Si un numéro de niveau est spécifié, la fonction **levels** retourne le niveau associé à la position de base zéro spécifiée.  
  
 Si un nom de niveau est spécifié, la fonction **levels** retourne le niveau spécifié.  
  
> [!NOTE]  
>  Utilisez la syntaxe d'une expression de chaîne pour des fonctions définies par l'utilisateur.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent chacun des syntaxes de fonction **levels** .  
  
### <a name="numeric"></a>Numérique  
 L'exemple ci-dessous retourne le niveau Country :  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 L'exemple ci-dessous retourne le niveau Country :  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
