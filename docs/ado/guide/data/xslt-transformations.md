---
title: Transformations XSLT | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2606733b3efc5a9641f8de0f544b3cff7c7e9a31
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923341"
---
# <a name="xslt-transformations"></a>Transformations XSLT
XSLT peut être appliqué au code XML généré pour le transformer en un autre format. La compréhension du format XML dans ADO vous aide à développer des modèles XSLT qui peuvent le transformer en une forme plus conviviale.  
  
 Par exemple, vous savez que chaque ligne de l’ensemble d’enregistrements est enregistrée en tant qu’élément z :Row à l’intérieur de l’élément RS : Data. De même, chaque champ de l’ensemble d’enregistrements est enregistré en tant que paire attribut-valeur pour cet élément.  
  
## <a name="remarks"></a>Notes  
 Le script XSLT suivant peut être appliqué au code XML présenté dans la section précédente pour le transformer en table HTML à afficher dans le navigateur :  
  
```  
<?xml version="1.0" encoding="ISO-8859-1"?>  
<html xmlns:xsl="http://www.w3.org/TR/WD-xsl">  
<body STYLE="font-family:Arial, helvetica, sans-serif; font-size:12pt; background-color:white">  
<table border="1" style="table-layout:fixed" width="600">  
  <col width="200"></col>  
  <tr bgcolor="teal">  
    <th><font color="white">CustomerId</font></th>  
    <th><font color="white">CompanyName</font></th>  
    <th><font color="white">ContactName</font></th>  
  </tr>  
<xsl:for-each select="xml/rs:data/z:row">  
  <tr bgcolor="navy">  
    <td><font color="white"><xsl:value-of select="@CustomerID"/></font></td>  
    <td><font color="white"><xsl:value-of select="@CompanyName"/></font></td>  
    <td><font color="white"><xsl:value-of select="@ContactName"/></font></td>   
  </tr>  
</xsl:for-each>  
</table>  
</body>  
</html>  
```  
  
 Le XSLT convertit le flux de données XML généré par la méthode ADO Save en une table HTML qui affiche chaque champ de l’ensemble d’enregistrements avec un en-tête de table. Les en-têtes et les lignes de la table se voient également attribuer des polices et des couleurs différentes.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
