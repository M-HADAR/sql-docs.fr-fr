---
title: Traitement des résultats | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9fdc66899f7d863cbfb3ae04ad0796614717a734
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63209662"
---
# <a name="processing-results"></a>Traitement des résultats
  Si un objet d'ensemble de ligne est produit par l'exécution d'une commande ou la génération d'un objet d'ensemble de ligne directement à partir du fournisseur, le consommateur doit extraire et accéder aux données dans l'ensemble de lignes.  
  
 Les ensembles de lignes sont les objets centraux qui permettent au fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client d'exposer des données au format tabulaire. Conceptuellement, un ensemble de lignes est un jeu de lignes dans lequel chaque ligne possède des données de colonne. Un objet d’ensemble de ligne expose des interfaces comme **IRowset** (contient des méthodes pour extraire des lignes de l’ensemble de lignes de manière séquentielle), **IAccessor** (autorise la définition d’un groupe de liaisons de colonnes qui décrivent la manière dont les données tabulaires sont liées aux variables du programme de consommateur), **IColumnsInfo** (fournit des informations sur les colonnes de l’ensemble de lignes) et **IRowsetInfo** (fournit des informations sur l’ensemble de lignes).  
  
 Un consommateur peut appeler la méthode **IRowset::GetData** pour extraire une ligne de données de l’ensemble de lignes dans une mémoire tampon. Avant que **GetData** ne soit appelé, le consommateur décrit la mémoire tampon à l’aide d’un jeu de structures DBBINDING. Chaque liaison décrit la manière dont une colonne dans un ensemble de lignes est stockée dans une mémoire tampon de consommateur et contient les éléments suivants :  
  
-   ordinal de la colonne (ou paramètre) auquel la liaison s'applique ;  
  
-   informations concernant ce qui est lié (par exemple, valeur des données, longueur des données et leur état de liaison) ;  
  
-   informations concernant ce qui est décalé dans la mémoire tampon à chacune de ces parties ;  
  
-   longueur et type des valeurs de données telles qu'elles existent dans la mémoire tampon du consommateur.  
  
 Lors de l'obtention des données, le fournisseur utilise les informations dans chaque liaison afin de déterminer où et comment extraire des données de la mémoire tampon du consommateur. Lors de la définition des données dans la mémoire tampon du consommateur, le fournisseur utilise les informations dans chaque liaison afin de déterminer où et comment retourner des données dans la mémoire tampon du consommateur.  
  
 Une fois les structures DBBINDING spécifiées, un accesseur est créé (**IAccessor::CreateAccessor**). Un accesseur est une collection de liaisons utilisée pour obtenir ou définir les données dans la mémoire tampon du consommateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application SQL Server Native Client OLE DB Provider](creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Rubriques de procédures OLE DB](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
