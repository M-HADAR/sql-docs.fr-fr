---
title: Création d’étiquettes de publipostage dans Microsoft Word à l’aide de données Visual FoxPro | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data [ODBC], mailing labels
- Visual FoxPro data [ODBC], Word
- mailing labels [ODBC]
- Visual FoxPro ODBC driver [ODBC], Word
- FoxPro ODBC driver [ODBC], word
ms.assetid: c901b60c-9f84-407a-b3d1-b4d301a71370
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 73880171493555a7d30e5c0c5419d02338961e9b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096531"
---
# <a name="creating-mailing-labels-in-microsoft-word-using-visual-foxpro-data"></a>Création d’étiquettes de publipostage dans Microsoft Word avec des données Visual FoxPro
Vous pouvez utiliser les données Visual FoxPro dans un document Microsoft Word pour Windows 95 ou Windows 98. Par exemple, vous souhaiterez peut-être créer des étiquettes de publipostage à partir des informations client stockées dans une table Visual FoxPro.  
  
### <a name="to-create-mailing-labels"></a>Pour créer des étiquettes de publipostage  
  
1.  Dans Microsoft Word, créez un nouveau document vierge.  
  
2.  Dans le menu Outils, choisissez publipostage.  
  
3.  Dans l’aide à la fusion et publipostage, choisissez créer, puis sélectionnez étiquettes de publipostage.  
  
4.  Sous document principal, choisissez fenêtre active.  
  
5.  Sous source de données, choisissez accéder aux données, puis sélectionnez Ouvrir la source de données.  
  
6.  Dans la boîte de dialogue Ouvrir la source de données, choisissez MS Query.  
  
7.  Dans la boîte de dialogue Sélectionner une source de données, sélectionnez une source de données Visual FoxPro, puis cliquez sur utiliser.  
  
8.  Si la base de données accessible par votre source de données comprend des tables, sélectionnez une table dans la boîte de dialogue Ajouter des tables. Microsoft Query affiche la table ajoutée dans la moitié supérieure du concepteur de requêtes.  
  
9. Sélectionnez les champs de votre requête en les faisant glisser de la table vers la moitié inférieure du concepteur.  
  
10. Dans le menu fichier, choisissez renvoyer les données à Microsoft Word. Microsoft Query se ferme et les données que vous avez sélectionnées peuvent être utilisées dans votre document de fusion et publipostage.  
  
11. Sous document principal, choisissez Setup.  
  
12. Dans la boîte de dialogue Options d’étiquette, sélectionnez les informations d’imprimante et d’étiquette souhaitées, puis cliquez sur OK.  
  
13. Dans la boîte de dialogue créer des étiquettes, sélectionnez les champs que vous souhaitez imprimer sur les étiquettes de publipostage, puis cliquez sur OK.  
  
14. Dans l’aide au publipostage, sous fusionner les données avec le document, cliquez sur fusionner.  
  
15. Dans la boîte de dialogue Fusionner, sélectionnez les options souhaitées, puis cliquez sur fusionner.
