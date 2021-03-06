---
title: Zones de région de données de tableau matriciel (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f6c13407-2887-4287-9396-a58dba619d9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0f3fb342593e24ce97a550186065a22ec3ee2498
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104721"
---
# <a name="tablix-data-region-areas-report-builder-and-ssrs"></a>Zones de région de données de tableau matriciel (Générateur de rapports et SSRS)
  Une région de données de tableau matriciel contient quatre zones qui contiennent des cellules de tableau matriciel : l’angle, la zone de groupe de lignes, la zone de groupe de colonnes et le corps. Les cellules de chaque zone remplissent une fonction distincte. Les cellules ajoutées à la zone du corps du tableau matriciel permettent d'afficher des données détaillées ainsi que des données groupées. Le Générateur de rapports et le Concepteur de rapports ajoutent des cellules à la zone de groupe de lignes ou à la zone de groupe de colonnes lorsque vous créez un groupe pour afficher les valeurs d'instance de groupe. Le Générateur de rapports et le Concepteur de rapports créent des cellules d'angle de tableau matriciel lorsqu'il existe à la fois des groupes de lignes et des groupes de colonnes.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Sur l'aire de conception, les traits en pointillés délimitent les quatre zones d'une région de données de tableau matriciel. L'illustration suivante montre les zones d'une région de tableau matriciel contenant : des groupes de lignes imbriqués dépendant de la catégorie et de la sous-catégorie, des groupes de colonnes imbriqués dépendant de la géographie, du pays et/ou de la région, ainsi qu'un groupe de colonnes adjacent dépendant de l'année.  
  
 ![Zones de région de données de tableau matriciel](../media/rs-tablixareas.gif "Zones de région de données de tableau matriciel")  
  
 La liste suivante présente chaque zone :  
  
-   **Zone d’angle**de tableau matriciel. (Facultatif) L'angle du tableau matriciel se trouve en haut, à gauche ou en haut, à droite pour les dispositions de droite à gauche (RTL). Cette zone est créée automatiquement lorsque vous ajoutez des groupes de lignes et des groupes de colonnes à la région de données du tableau matriciel. Dans cette zone, vous pouvez fusionner des cellules et ajouter une étiquette ou incorporer un autre élément de rapport. Sur l'illustration donnée en exemple, les cellules fusionnées qui apparaissent dans l'angle affichent l'étiquette Ventes par zone et par année.  
  
-   **Zone groupes de colonnes**du tableau matriciel. (Facultatif) Les groupes de colonnes du tableau matriciel se trouvent en haut, à droite (ou en haut, à gauche pour les dispositions RTL). Cette zone est créée automatiquement lorsque vous ajoutez un groupe de colonnes. Les cellules de cette zone contiennent les membres de la hiérarchie des groupes de colonnes et affichent les valeurs d'instance des groupes de colonnes. Dans l'illustration donnée en exemple, les cellules qui affichent les données [Geography] et [CountryRegion] correspondent à des groupes de colonnes imbriqués et la cellule qui affiche les données [Year] correspond à un groupe de colonnes adjacent. La colonne [Total] affiche les totaux agrégés sur chaque ligne.  
  
-   **Zone des groupes de lignes du tableau matriciel**. (Facultatif) Les groupes de lignes du tableau matriciel se trouvent en bas, à gauche (ou en bas, à droite pour les dispositions RTL). Cette zone est créée automatiquement lorsque vous ajoutez des groupes de lignes. Les cellules de cette zone contiennent les membres de la hiérarchie des groupes de lignes et affichent les valeurs d'instance du groupe de lignes. Dans l'illustration donnée en exemple, les cellules qui affichent les données [Category] et [Subcat] correspondent à des groupes de lignes imbriqués. La ligne Total située au-dessous des cellules Subcat est répétée pour chaque groupe de catégorie distinct afin d'afficher les sous-totaux agrégés de chaque colonne. La ligne du total global contient le total de toutes les catégories.  
  
-   **Zone du corps du tableau matriciel**. Le corps du tableau matriciel se trouve en bas, à droite (ou en bas, à gauche pour les dispositions RTL). Le corps du tableau matriciel affiche les données détaillées et les données groupées. Dans cet exemple, seules les données agrégées sont utilisées. L'étendue de l'expression est déterminée par les groupes, auxquels la zone de texte appartient, dont le niveau est le plus profond. Les cellules du corps du tableau matriciel affichent des données détaillées quand elles figurent dans des lignes de détail et des données agrégées quand elles appartiennent à des lignes ou colonnes associées à des groupes. Par défaut, les cellules des lignes ou colonnes de groupe qui contiennent des expressions simples ne comportant pas de fonction d'agrégation affichent la première valeur du groupe. Sur l'illustration donnée en exemple, les cellules affichent les totaux agrégés pour les totaux de ligne de l'intégralité des bons de commande.  
  
 Pendant l’exécution du rapport, les groupes de colonne s’affichent en détail sur la droite (ou sur la gauche, quand la propriété Direction de la région de données de tableau matriciel est définie sur RTL) pour chaque colonne définie, des valeurs uniques étant attribuées aux expressions de groupe. Les groupes de ligne s'affichent en détail en bas de la page. Pour plus d’informations, consultez [Cellules, lignes et colonnes de région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
 L'illustration suivante montre la région de données du tableau matriciel telle qu'elle apparaît dans l'Aperçu.  
  
 ![Aperçu, angle de tableau matriciel, ligne & groupes de colonnes, corps](../media/rs-tablixareaspreview.gif "Aperçu, angle de tableau matriciel, groupes de lignes et de colonnes, corps")  
  
 La zone de groupe de lignes affiche deux instances de groupe de catégorie, l'une correspondant à la catégorie Clothing et l'autre à la catégorie Components. Le groupe de colonnes affiche une instance de groupe géographique correspondant à l'Amérique du Nord (North America) ainsi que des instances de groupe pays/région imbriquées correspondant respectivement au Canada (CA) et aux États-Unis (US). En outre, la colonne adjacente affiche deux instances de groupe pour les années 2003 et 2004. La ligne de colonne Total affiche les totaux de ligne, la ligne des totaux qui est répétée pour chaque groupe de catégorie affiche les totaux de sous-catégorie et la ligne du total global affiche les totaux de catégorie une seule fois pour la région de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Didacticiels &#40;Générateur de rapports&#41;](../report-builder-tutorials.md)   
 [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Listes &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)  
  
  
