---
title: Format de persistance XML | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML persistence [ADO], persistence format
ms.assetid: 6e146738-ac4d-47bb-b6cd-d87b2260aead
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e2d1c30546a8466ba9950f31cffdfb9447bd89ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923387"
---
# <a name="xml-persistence-format"></a>Format de persistance XML
ADO utilise l’encodage UTF-8 pour le flux XML qu’il conserve.  
  
 Le format XML ADO est divisé en deux sections : une section de schéma suivie de la section de données. Voici un exemple de fichier XML pour la table Shippers de la base de données Northwind. Les différentes parties du code XML sont présentées dans l’exemple ci-dessous.  
  
## <a name="remarks"></a>Notes  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"   
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"   
xmlns:rs="urn:schemas-microsoft-com:rowset"   
xmlns:z="#RowsetSchema">   
  <s:Schema id="RowsetSchema">   
    <s:ElementType name="row" content="eltOnly" rs:updatable="true">   
      <s:AttributeType name="ShipperID" rs:number="1"   
        rs:basetable="shippers" rs:basecolumn="ShipperID"  
        rs:keycolumn="true">   
        <s:datatype dt:type="int" dt:maxLength="4" rs:precision="10"   
          rs:fixedlength="true" rs:maybenull="false"/>   
      </s:AttributeType>   
      <s:AttributeType name="CompanyName" rs:number="2"   
        rs:nullable="true" rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="CompanyName">   
        <s:datatype dt:type="string" dt:maxLength="40" />   
      </s:AttributeType>   
      <s:AttributeType name="Phone" rs:number="3" rs:nullable="true"   
        rs:write="true" rs:basetable="shippers"   
        rs:basecolumn="Phone">   
        <s:datatype dt:type="string" dt:maxLength="24"/>   
      </s:AttributeType>   
      <s:extends type="rs:rowbase"/>   
    </s:ElementType>   
  </s:Schema>   
  
  <rs:data>   
    <z:row ShipperID="1" CompanyName="Speedy Express"   
      Phone="(503) 555-9831"/>   
    <z:row ShipperID="2" CompanyName="United Package"   
      Phone="(503) 555-3199"/>   
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>   
  </rs:data>   
</xml>  
```  
  
 Le schéma montre les déclarations des espaces de noms, de la section de schéma et de la section de données. La section schéma contient des définitions pour Row, ShipperID, CompanyName et Phone.  
  
 Les définitions de schéma sont conformes à la [spécification de données XML W3C](http://www.w3.org/TR/1998/NOTE-XML-data/) et peuvent être entièrement validées (même si la validation ne se produit pas dans Internet Explorer 5). XML-Data est actuellement le seul format de schéma pris en charge pour la persistance du Recordset.  
  
 La section des données comporte trois lignes contenant des informations sur les expéditeurs. Pour un ensemble de lignes vide, la section des données peut être vide \<, mais les balises RS : Data> doivent être présentes. Sans données, vous pouvez écrire la balise sténographique comme simple \<RS : data/>. Toute balise précédée de « RS » indique qu’elle se trouve dans l’espace de noms défini par urn : schemas-microsoft-com : rowset.  
  
## <a name="see-also"></a>Voir aussi  
 [Persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md)
