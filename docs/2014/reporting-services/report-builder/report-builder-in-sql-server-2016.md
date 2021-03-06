---
title: Générateur de rapports SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10428"
helpviewer_keywords:
- overview of Report Builder
- getting started
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f03f0f4c210408324ee4a2cae255ba805e0377a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107712"
---
# <a name="report-builder-in-sql-server-2014"></a>Générateur de rapports dans SQL Server 2014
  Le Générateur de rapports est un environnement de création de rapports destiné aux utilisateurs professionnels qui préfèrent travailler dans l'environnement [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office. Lorsque vous concevez un rapport, vous spécifiez l'emplacement des données à obtenir, leur nature et leur mode d'affichage. Au moment de l'exécution du rapport, le processeur de rapports assimile l'ensemble des informations que vous avez spécifiées, puis il récupère les données et les combine à la mise en page du rapport pour générer le rapport. Vous pouvez soit afficher un aperçu de vos rapports dans le Générateur de rapports, soit les publier sur un serveur de rapports ou un serveur de rapports en mode intégré SharePoint, pour permettre à d'autres utilisateurs de les exécuter.  
  
 Le rapport de cette illustration comprend une matrice avec des groupes de lignes et de colonnes, des graphiques sparkline, des indicateurs et un graphique à secteurs de synthèse dans la cellule d'angle, ainsi qu'une carte avec deux ensembles de données géographiques représentées par couleur et par taille de cercle.  
  
 ![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")  
  
##  <a name="JumpStartReptCreation"></a>Création de rapports Jump-Start  
  
-   **Démarrez votre rapport withreport composants** créés par une autre personne de votre équipe. Les parties de rapports sont des éléments de rapport qui ont été publiés séparément sur un serveur de rapports ou sur un site SharePoint intégré à un serveur de rapports. Elles peuvent être réutilisées dans d'autres rapports. Les éléments de rapport tels que les tableaux, matrices, graphiques et images peuvent être publiés en tant que parties de rapports.  
  
-   **Démarrez avec un dataset partagé** créé par une autre personne de votre équipe. Les datasets partagés sont des requêtes basées sur une source de données partagée, qui sont enregistrées sur un serveur de rapports ou un site SharePoint intégré à un serveur de rapports.  
  
-   **Démarrez avec l’Assistant tableau, matrice ou graphique**. Sélectionnez une connexion à une source de données, effectuez un glisser-déplacer de champs pour créer une requête de dataset, sélectionnez une disposition et un style, puis personnalisez votre rapport.  
  
-   **Démarrez avec l’Assistant carte** pour créer des rapports qui affichent des données agrégées sur un arrière-plan géographique ou géométrique. Les données cartographiques peuvent être des données spatiales provenant d'une requête [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'un fichier de forme ESRI (Environmental Systems Research Institute, Inc.). Vous pouvez également ajouter un arrière-plan de mosaïque [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bing.  
  

  
##  <a name="DesignRept"></a>Concevoir votre rapport  
  
-   **Créez des rapports à l'aide de mises en page de rapports de tableau, de matrice, de graphique et au format libre.** Créez des rapports de tableau pour des données en colonnes, des rapports de matrice (tels que des rapports d'analyse croisée ou de tableau croisé dynamique) pour des données synthétisées, des rapports de graphique pour des données graphiques et enfin, des rapports au format libre pour tout autre type de données. Les rapports peuvent incorporer d'autres rapports et graphiques, avec des listes, des graphiques et des contrôles pour les applications web dynamiques.  
  
-   **Rapport à partir de diverses sources de données.** Générez des rapports à l’aide de données de n’importe [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]quel type de source de données qui a un fournisseur de données managé, OLE DB fournisseur ou une source de données ODBC. Vous pouvez créer des rapports qui utilisent des données relationnelles et multidimensionnelles provenant de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Oracle, Hypérion, entre autres. Utilisez une extension pour le traitement des données XML et récupérez des données de n'importe quelle source XML. Vous pouvez utiliser des fonctions table pour concevoir des sources de données personnalisées.  
  
-   **Modifiez des rapports existants.** À l’aide de Générateur de rapports, vous pouvez personnaliser et mettre à jour des [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]rapports qui ont été créés dans Concepteur de rapports.  
  
-   **Modifiez vos données** en filtrant, en regroupant et en triant les données, ou en ajoutant des formules ou des expressions.  
  
-   **Ajoutez des graphiques, des jauges, des graphiques sparkline et des indicateurs** pour synthétiser les données dans un format visuel, et présentez d’un coup d’œil d’importants volumes d’informations agrégées.  
  
-   **Ajoutez des fonctionnalités interactives** telles que des explorateurs de documents, des boutons d’affichage/de masquage et des liens d’extraction vers des sous-rapports et des rapports d’extraction. Utilisez des paramètres et des filtres pour filtrer les données pour des vues personnalisées.  
  
-   **Incorporez ou référencez des images** et d’autres ressources, y compris du contenu externe.  
  

  
##  <a name="ManageRpt"></a>Gérer votre rapport  
  
-   **Enregistrez la définition du rapport** sur votre ordinateur ou sur le serveur de rapports, où vous pouvez le gérer et le partager avec d’autres utilisateurs.  
  
-   **Choisissez un format de présentation** lorsque vous ouvrez le rapport, ou après avoir ouvert le rapport. Vous pouvez sélectionner un format adapté au Web, à l'impression ou à une application bureautique. Les formats disponibles sont les suivants : HTML, MHTML, PDF, XML, CSV, TIFF, Word et Excel.  
  
-   **Configurez des abonnements.** Après avoir publié le rapport sur le serveur de rapports ou un serveur de rapports en mode intégré SharePoint, vous pouvez configurer votre rapport pour une exécution à un moment spécifique, créer un historique de rapport et configurer des abonnements par messagerie électronique.  
  
-   **Générez des flux de données** à partir de votre rapport à l’aide de l’extension de rendu Atom Reporting Services.  
  
> [!NOTE]  
>  Les rapports publiés sont gérés sur un serveur de rapports ou un serveur de rapports en mode intégré SharePoint par un administrateur de serveur de rapports. Les administrateurs de serveur de rapports peuvent choisir le mode de sécurité, définir des propriétés et planifier des opérations, telles que l'historique de rapport et la remise des rapports par courrier électronique. Ils peuvent créer des planifications partagées et des sources de données partagées afin d'en permettre une utilisation générale. Les administrateurs peuvent également gérer tous les dossiers du serveur de rapports. La possibilité de réaliser des tâches de gestion dépend des autorisations délivrées aux utilisateurs.  
  

  
##  <a name="InThisSection"></a> Dans cette section  
 [Nouveautés du Générateur de rapports pour SQL Server 2014](../what-s-new-in-report-builder-for-sql-server-2014.md)  
 Décrit les nouvelles fonctionnalités de cette version du Générateur de rapports, notamment les cartes.  
  
 [Didacticiel : création d’un rapport de graphique rapide en mode hors connexion](tutorial-create-a-quick-chart-report-offline-report-builder.md)  
 Ce didacticiel présente le Générateur de rapports et les Assistants disponibles pour vous aider à créer des rapports. Il fournit un ensemble de données que vous pouvez utiliser pour vous éviter d'avoir à vous connecter à une source de données pour la mise en route.  
  
 [Planification d’un rapport &#40;Générateur de rapports&#41;](../report-design/planning-a-report-report-builder.md)  
 Fournit des informations sur les éléments à prendre en considération avant de commencer à créer un rapport.  
  
 [Concepts de création de rapports &#40;Générateur de rapports et SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
 Définit les concepts clés utilisés dans la documentation du Générateur de rapports.  
  
 [Mode Conception de rapport &#40;Générateur de rapports&#41;](report-design-view-report-builder.md)  
 Explique les différents volets et régions du mode création de rapport.  
  
 [Mode création de dataset partagé &#40;Générateur de rapports&#41;](shared-dataset-design-view-report-builder.md)  
 Explique les différents volets et régions du mode création de dataset partagé.  
  
 [Raccourcis clavier &#40;Générateur de rapports&#41;](keyboard-shortcuts-report-builder.md)  
 Présente les touches de raccourci disponibles pour la navigation et la conception de rapports dans le Générateur de rapports.  
  
 [Démarrer Générateur de rapports &#40;Générateur de rapports&#41;](start-report-builder.md)  
 Explique comment démarrer les deux versions différentes du Générateur de rapports : autonome et [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)].  
  
  
