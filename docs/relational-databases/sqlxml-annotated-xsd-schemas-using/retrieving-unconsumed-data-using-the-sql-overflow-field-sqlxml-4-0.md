---
title: 'Obtient des données non consommées avec SQL : overflow-field (SQLXML)'
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 35abd64e0c7e492f114164447ec3e258242d3765
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75257404"
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a>Extraction de données non consommées à l'aide de sql:overflow-field (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Lorsque les enregistrements sont insérés dans une base de données à partir d'un document XML à l'aide de la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML, toutes les données non consommées du document XML source peuvent être stockées dans une colonne. Lorsque vous récupérez des données à partir d’une base de données à l’aide de schémas annotés, vous pouvez spécifier l’attribut **SQL : overflow-field** pour identifier la colonne dans la table dans laquelle les données de dépassement de capacité sont stockées. L’attribut **SQL : overflow-field** peut être spécifié sur ** \<l’élément>**.  
  
 Ces données sont alors récupérées selon les méthodes suivantes :  
  
-   Les attributs stockés dans la colonne de dépassement sont ajoutés à l’élément qui contient l’annotation **SQL : overflow-field** .  
  
-   Les éléments enfants et leurs descendants, stockés dans la colonne de dépassement de capacité de la base de données, sont ajoutés comme éléments enfants après le contenu spécifié explicitement dans le schéma. (Aucun ordre n'est conservé.)  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a>R. Spécification de sql:overflow-field pour un élément  
 Cet exemple suppose que le script suivant a été exécuté afin qu'une table nommée Customers2 existe dans la base de données tempdb :  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 En outre, vous devez créer un répertoire virtuel pour la base de données tempdb et un nom virtuel de modèle de type de **modèle** nommé « template ».  
  
 Dans l'exemple suivant, le schéma de mappage extrait les données non consommées stockées dans la colonne AddressOverflow de la table Customers2 :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom Overflow.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom OverflowT.xml dans le répertoire où vous avez enregistré Overflow.xml. La requête du modèle sélectionne les enregistrements de la table Customers2.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (Overflow.xml) est relatif au répertoire dans lequel le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  

     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
