---
title: STLineFromText (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STLineFromText (geometry Data Type)
- STLineFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLineFromText (geometry Data Type)
ms.assetid: 430508ad-207b-4dee-a4d1-4ddf25e6b4a9
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a0a912e4ab228617537e9c28e9a5cecc4a0278fe
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "72278130"
---
# <a name="stlinefromtext-geometry-data-type"></a>STLineFromText (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une instance **geometry** à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text), à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STLineFromText ( 'linestring_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *linestring_tagged_text*  
 Représentation WKT de l’instance **geometryLineString** à retourner. *linestring_tagged_text* est une expression **nvarchar(max)** .  
  
 *SRID*  
 Expression **int** qui représente le SRID (spatial reference identifier ) de l’instance **geometryLineString** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type OGC : **LineString**  
  
## <a name="remarks"></a>Notes  
Cette méthode lève **FormatException** si l’entrée n’est pas au format approprié. La notation de géométrie WKT à trois dimensions et mesurée à partir de la fonctionnalité simple Open Geospatial Consortium (OGC) pour la version de spécification SQL version 1.2.1 n’est pas prise en charge. Consultez les exemples pour la représentation prise en charge des valeurs Z (élévation) et M (mesure).
  
## <a name="examples"></a>Exemples  
 Les exemples suivants utilisent la méthode `STLineFromText()` pour créer une instance `geometry`.

### <a name="example-1-two-dimension-geometry-wkt"></a>Exemple 1 : géométrie WKT à deux dimensions
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100, 200 200)', 0);  
SELECT @g.ToString();  
```  
  
### <a name="example-2-three-dimension-geometry-wkt"></a>Exemple 2 : géométrie WKT à trois dimensions
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100 100, 200 200 200)', 0);  
SELECT @g.ToString();  
``` 

### <a name="example-3-two-dimension-measured-geometry-wkt"></a>Exemple 3 : géométrie mesurée WKT à deux dimensions
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100 NULL 100, 200 200 NULL 200)', 0);  
SELECT @g.ToString();  
``` 

### <a name="example-4-three-dimension-measured-geometry-wkt"></a>Exemple 4 : géométrie mesurée WKT à trois dimensions
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100 100 100, 200 200 200 200)', 0);  
SELECT @g.ToString();  
``` 
## <a name="see-also"></a>Voir aussi  
 [Méthodes geometry statiques de l’OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

