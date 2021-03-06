---
title: SqlTypes et le DataSet
description: Décrit la prise en charge de type pour SqlTypes dans le DataSet.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: a7ef43ca6afa243e313e8e38bdd05d929161e71f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75233789"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes et le DataSet

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

ADO.NET 2.0 inclut une prise en charge améliorée de type pour le `DataSet` via l’espace de noms <xref:System.Data.SqlTypes>. Les types dans <xref:System.Data.SqlTypes> sont conçus pour fournir des types de données avec les mêmes sémantique et précision que les types de données dans une base de données SQL Server. Chaque type de données dans <xref:System.Data.SqlTypes> a un type de données équivalent dans SQL Server, avec la même représentation de données sous-jacentes.  
  
L’utilisation de <xref:System.Data.SqlTypes> directement dans un <xref:System.Data.DataSet> confère plusieurs avantages lors de l’utilisation de types de données SQL Server. <xref:System.Data.SqlTypes> prend en charge la même sémantique que les types de données natifs SQL Server. La spécification de l’un des <xref:System.Data.SqlTypes> dans la définition d’une <xref:System.Data.DataColumn> élimine la perte de précision qui peut se produire lors de la conversion de types de données décimales ou numériques en l’un des types de données Common Language Runtime (CLR).  

L’exemple suivant crée un objet <xref:System.Data.DataTable>, définissant de façon explicite les types de données <xref:System.Data.DataColumn> en utilisant <xref:System.Data.SqlTypes> au lieu de types CLR. Le code remplit l’objet <xref:System.Data.DataTable> de données de la table Sales.SalesOrderDetail dans la base de données AdventureWorks dans SQL Server. La sortie affichée dans la fenêtre de console affiche le type de données de chaque colonne et les valeurs récupérées à partir de SQL Server.  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
