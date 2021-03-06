---
title: Définir des formules de membre personnalisées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- members [Analysis Services], custom
- custom rollup formulas [Analysis Services]
- MDX [Analysis Services], custom rollup formulas
- custom member formulas [Analysis Services]
ms.assetid: 258304e2-d900-4013-97e3-871f51dfdce2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 969a8f11926957ae19512e92b68e02d12011dd03
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077282"
---
# <a name="define-custom-member-formulas"></a>Définir des formules de membre personnalisées
  Vous pouvez définir une expression MDX (Multidimensional Expressions) appelée formule de membre personnalisée pour fournir les valeurs des membres d'un attribut spécifié. Une colonne d'une table issue d'une vue de source de données fournit, pour chaque membre d'un attribut, l'expression utilisée pour fournir la valeur de ce membre.  
  
 Les formules de membre personnalisées déterminent les valeurs de cellule associées aux membres et ont priorité sur les fonctions d'agrégation des mesures. Les formules de membres personnalisées sont écrites dans MDX. Chaque formule de membre personnalisée s'applique à un seul membre. Les formules de membre personnalisées sont stockées dans la table de dimension ou dans une autre table qui entretient une relation de clé étrangère avec la table de dimension.  
  
 La propriété `CustomRollupColumn` d'un attribut spécifie la colonne qui contient les formules de membre personnalisées pour les membres de l'attribut. Si une ligne de la colonne est vide, la valeur de la cellule pour le membre est retournée normalement. Si la formule figurant dans la colonne n'est pas valide, une erreur se produit au moment de l'exécution chaque fois qu'une valeur de cellule utilisant le membre est extraite.  
  
 Avant de spécifier des formules de membre personnalisées pour un attribut, assurez-vous que la table de dimension contenant l'attribut, ou une table qui lui est directement associée, contient une colonne de chaîne pour stocker les formules de membre personnalisées. Si c’est le cas, vous pouvez soit définir manuellement `CustomRollupColumn` la propriété sur un attribut, soit utiliser l’amélioration définir la formule de membre personnalisée de l’Assistant Business Intelligence pour activer une formule de membre personnalisée sur un attribut. Pour plus d’informations sur la façon d’utiliser cette amélioration, consultez [Définir des formules de membre personnalisées pour les attributs d’une dimension](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md).  
  
## <a name="evaluating-custom-member-formulas"></a>Évaluation des formules de membre personnalisées  
 Les formules de membre personnalisées sont différentes des membres calculés. Les formules de membre personnalisées s'appliquent à des membres qui existent dans des tables de dimension et fournissent seulement la valeur du membre. Pour leur part, les membres calculés ne sont pas stockés dans des tables de dimension, et les expressions de membre calculé définissent les données et les métadonnées de membres supplémentaires inclus dans une dimension ou une hiérarchie.  
  
 Les formules de membre personnalisées ont priorité sur les fonctions d'agrégation associées à des mesures. Par exemple, supposons qu'une mesure utilisant la fonction d'agrégation `Sum` présente, avant la spécification d'une formule de membre personnalisée, les valeurs ci-après pour les membres de la dimension Time :  
  
-   2003: 2100  
  
    -   Quarter 1: 700  
  
    -   Quarter 2: 500  
  
    -   Quarter 3: 100  
  
    -   Quarter 4: 800  
  
-   2004: 1500  
  
    -   Quarter 1: 600  
  
    -   Quarter 2: 200  
  
    -   Quarter 3: 300  
  
    -   Quarter 4 : 400  
  
 Avec une formule de membre personnalisée, la valeur du membre est fournie par la formule de cumul personnalisée. Par exemple, la formule de membre personnalisée suivante permet de fournir 450 comme valeur du membre Quarter 4 enfant du membre 2004 dans la dimension Time.  
  
```  
Time.[Quarter 3] * 1.5  
```  
  
 Les formules de membre personnalisées sont stockées dans une colonne de la table de dimension. Vous activez les formules de cumul personnalisées en définissant la propriété `CustomRollupColumn` d'un attribut.  
  
 Pour appliquer une seule expression MDX à tous les membres d'un attribut, créez sur la table de dimension un calcul nommé qui retourne une expression MDX sous forme de chaîne littérale. Ensuite, spécifiez le calcul nommé avec la valeur de la propriété `CustomRollupColumn` de l'attribut que vous voulez configurer. Un calcul nommé est une colonne d'une table de vue de source de données qui retourne des valeurs de ligne définies par une expression SQL. Pour plus d’informations sur la construction de calculs nommés, consultez [Définir des calculs nommés dans une vue de source de données &#40;Analysis Services&#41;](define-named-calculations-in-a-data-source-view-analysis-services.md).  
  
> [!NOTE]  
>  Pour appliquer une expression MDX aux membres d'un niveau particulier d'un attribut au lieu de l'appliquer aux membres de tous les niveaux, vous pouvez la définir comme script MDX sur le niveau concerné. Pour plus d’informations, consultez [Principes de base des scripts MDX &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md).  
  
 Si vous utilisez des membres calculés ainsi que des formules de cumul personnalisées pour les membres d'un attribut, vous devez être conscient de l'ordre d'évaluation. Les membres calculés sont résolus avant les formules de cumul personnalisées.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Définir des formules de membre personnalisées pour les attributs d’une dimension](bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)  
  
  
