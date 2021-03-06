---
title: 'Leçon 10 : créer des hiérarchies | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb70d7d495d88ee62e98bf27f2b92bf569c98387
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078188"
---
# <a name="lesson-10-create-hierarchies"></a>Leçon 10 : Créer des hiérarchies
  Dans cette leçon, vous allez créer des hiérarchies. Les hiérarchies sont des groupes de colonnes organisées en niveaux. Par exemple, la hiérarchie Géographie peut avoir des sous-niveaux correspondant à des pays, des régions, des départements et des villes. Les hiérarchies peuvent être affichées séparément des autres colonnes, dans une liste de champs d’applications clientes de création de rapports, ce qui permet aux utilisateurs clients de naviguer facilement parmi les hiérarchies et de les inclure dans un rapport. Pour plus d’informations, consultez [Hiérarchies &#40;SSAS Tabulaire&#41;](tabular-models/hierarchies-ssas-tabular.md).  
  
 Pour créer des hiérarchies, vous allez utiliser le concepteur de modèles dans la *Vue du diagramme*. La création et la gestion des hiérarchies n'est pas prise en charge dans le générateur de modèles dans la vue de données.  
  
 Durée estimée pour suivre cette leçon : **20 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 9 : Créer des perspectives](lesson-8-create-perspectives.md).  
  
## <a name="create-hierarchies"></a>Créer des hiérarchies  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a>Pour créer une hiérarchie de catégorie dans la table Product  
  
1.  Dans le générateur de modèles, cliquez sur `Model` le menu, pointez sur **vue du modèle**, puis cliquez sur vue de **diagramme**.  
  
    > [!TIP]  
    >  Utilisez les contrôles de la minicarte dans l'angle supérieur droit du concepteur de modèles pour ajuster la vue des objets dans la vue du diagramme. Si vous replacez les objets dans la vue de diagramme, cette vue sera conservée lorsque vous enregistrerez le projet.  
  
2.  Dans le générateur de modèles, cliquez avec le `Product` bouton droit sur la table, puis cliquez sur **créer une hiérarchie**. Une nouvelle hiérarchie s’affiche au bas de la table.  
  
3.  Dans le nom de la hiérarchie, renommez la `Category`hiérarchie en tapant, puis appuyez sur entrée.  
  
4.  Dans le `Product` tableau, cliquez sur la colonne **Product Category Name** , puis faites-la `Category` glisser vers la hiérarchie, puis relâchez `Category` -la au-dessus du nom.  
  
5.  Dans la `Category` hiérarchie, cliquez avec le bouton droit sur la colonne **Product Category Name** , puis cliquez sur **Renommer**et tapez `Category`.  
  
    > [!NOTE]  
    >  Le fait de renommer une colonne dans une hiérarchie ne renomme pas cette colonne dans la table. Une colonne de hiérarchie n’est que la représentation de cette colonne dans la table.  
  
6.  Dans le `Product` tableau, cliquez avec le bouton droit sur la colonne nom de la **sous-catégorie de produit** , puis dans le menu contextuel, pointez sur **Ajouter à la hiérarchie**, puis cliquez sur. `Category`  
  
7.  Renommez le nom de la `Subcategory`sous-catégorie du **produit** en.  
  
8.  En utilisant les commandes cliquer et faire glisser, ou en utilisant la commande **Ajouter à la hiérarchie** dans le menu contextuel, ajoutez les colonnes nom du **modèle** et **nom du produit** (dans l’ordre) et placez-les sous la colonne nom de la sous- **catégorie de produit** . Renommez ces `Model` colonnes `Product`et, respectivement.  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a>Pour créer des hiérarchies dans la table Date  
  
1.  Dans le concepteur de modèles, cliquez avec le bouton droit sur la table **Date**, puis cliquez sur **Créer une hiérarchie**.  
  
2.  Renommez la hiérarchie en **Calendar**.  
  
3.  Ajoutez les colonnes suivantes, dans l'ordre, puis renommez-les :  
  
    |Colonne|Renommer en :|  
    |------------|----------------|  
    |Calendar Year|Year|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|jour|  
  
4.  Dans la table **Date**, répétez les étapes ci-dessus, en créant une hiérarchie **Fiscal**, y compris les colonnes suivantes :  
  
    |Colonne|Renommer en :|  
    |------------|----------------|  
    |Fiscal Year|Year|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Month|  
    |Day Of Month|jour|  
  
5.  Enfin, dans la table **Date**, répétez les étapes ci-dessus, en créant une hiérarchie **Production Calendar**, comprenant les colonnes suivantes :  
  
    |Colonne|Renommer en :|  
    |------------|----------------|  
    |Calendar Year|Year|  
    |Week Number Of Year|Week|  
    |Jour de la semaine|jour|  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour poursuivre l’étude de ce didacticiel, passez à la [Leçon 11 : Créer des partitions](lesson-10-create-partitions.md).  
  
  
