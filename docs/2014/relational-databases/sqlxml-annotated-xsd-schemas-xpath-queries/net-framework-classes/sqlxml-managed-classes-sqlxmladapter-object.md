---
title: Objet SqlXmlAdapter (classes managées SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b339e67b07ddb4168f9922c22e620eb2fa10d85e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014931"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>Objet SqlXmlAdapter (classes managées SQLXML)
  Cet objet fournit des méthodes qui facilitent l'interaction avec le dataset dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Pour obtenir un exemple fonctionnel, consultez [accès à la fonctionnalité SQLXML dans l’environnement .net](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 L’objet SqlXmlAdapter prend en charge les méthodes suivantes :  
  
 void Fill (DataSet DS)  
 Remplit le dataset dans le .NET Framework avec les données XML extraites de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 annuler la mise à jour (DataSet DS)  
 Applique des mises à jour aux enregistrements dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir des données dans le dataset.  
  
 L’objet SqlXmlAdapter prend en charge les constructeurs suivants :  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet SqlXmlCommand &#40;les classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [Objet SqlXmlParameter &#40;les classes managées SQLXML&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
