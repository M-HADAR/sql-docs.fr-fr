---
title: 'Leçon 2 : génération d’un scénario de prévision (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ee814dc0891e70dfeccf2b96383d1d7b5c324aa8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62931531"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>Leçon 2 : génération d'un scénario de prévision (Didacticiel intermédiaire sur l'exploration de données)
  Vous êtes analyste des ventes pour [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]et il vous a été demandé de fournir une estimation des ventes des produits pour l'année à venir. Plus précisément, vous devez comparer les estimations entre les différentes régions et les différentes gammes de produits. Vous devez, de plus, déterminer si les ventes des différents produits varient en fonction de la période de l'année.  
  
 Afin de rechercher les informations demandées, vous allez, au cours de cette leçon, faire un récapitulatif des ventes de l'entreprise au niveau mensuel et synthétiser les chiffres des ventes en fonction de trois régions : Europe, Amérique du Nord et Pacifique.  
  
 Une fois les tâches de cette leçon terminées, vous serez en mesure de répondre aux questions suivantes :  
  
-   Comment les ventes de différents modèles de vélos varient-elles au fil du temps ?  
  
-   Existe-t-il des différences entre les modèles des ventes dans les trois régions ?  
  
-   Est-il possible de prédire des pics dans les ventes ?  
  
 La leçon peut être effectuée en deux parties :  
  
-   La première partie présente la création et l'utilisation de base d'un modèle de série chronologique.  
  
-   La deuxième partie vous guide tout au long de la création d'un modèle de série chronologique, basé sur toutes les régions. Utilisez ce modèle général pour une *prédiction croisée*.  
  
 Pour effectuer les tâches de cette leçon, répertoriées ci-dessous, vous allez utiliser [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] la source de données que vous avez créée au cours de la [leçon 1 : création de la solution intermédiaire d’exploration de données &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).  
  
> [!WARNING]  
>  Les dates dans l'exemple de base de données de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ont été mises à jour pour cette version. Si vous utilisez une version antérieure de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], vous pouvez générer le modèle en suivant ces étapes, mais les résultats peuvent être différents.  
  
 **Création d'un modèle de prévision simple**  
  
-   [Ajout d’une vue de source de données pour les prévisions &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [Création d’une structure et d’un modèle de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Modification de la structure de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [Personnalisation et traitement du modèle de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Exploration du modèle de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Création de prédictions de série chronologique &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 **Création d'un modèle de prévision général pour la prédiction croisée**  
  
-   [Prédictions de série chronologique avancées &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [Prédictions de série chronologique utilisant des données mises à jour &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [Prédictions de série chronologique utilisant des données de remplacement &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [Comparaison des prédictions pour les modèles de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Ajout d’une vue de source de données pour les prévisions &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [Comprendre la configuration requise pour un modèle de série chronologique &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Toutes les leçons  
 [Leçon 1 : création de la solution intermédiaire d’exploration de données &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 Leçon 2 : Scénario de prévision (didacticiel sur l’exploration de données intermédiaire)  
  
 [Leçon 3 : création d’un scénario de panier de marché &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Leçon 4 : génération d’un scénario Sequence Clustering &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Leçon 5 : génération de modèles de réseau neuronal et de régression logistique &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Didacticiel sur l’exploration de données intermédiaire &#40;Analysis Services d’exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
