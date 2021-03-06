---
title: Ajouter des colonnes à une table (moteur de base de données)| Microsoft Docs
ms.custom: ''
ms.date: 10/27/2016
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8081b4b4b4c8a9d19af0c558d162974d98e16878
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68094742"
---
# <a name="add-columns-to-a-table-database-engine"></a>Ajouter des colonnes à une table (moteur de base de données)

[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

Cet article explique comment ajouter des colonnes à une table dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="BeforeYouBegin"></a> Avant de commencer

### <a name="Restrictions"></a> Limitations et restrictions

 L'instruction ALTER TABLE permettant d'ajouter des colonnes à une table, ajoute automatiquement ces colonnes à la fin de la table. Si vous souhaitez classer les colonnes dans la table dans un ordre spécifique, utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Cependant, notez que cette méthode n'est pas recommandée pour concevoir une base de données. La recommandation est de spécifier l'ordre dans lequel les colonnes sont renvoyées au niveau de l'application et de la requête. Vous ne pouvez pas compter sur l'utilisation de SELECT * pour retourner toutes les colonnes dans une commande prévue d'après l'ordre dans lequel elles sont définies dans la table. Spécifiez toujours le nom des colonnes dans vos requêtes et applications dans l'ordre dans lequel vous souhaitez qu'elles apparaissent.

### <a name="Security"></a> Sécurité

#### <a name="Permissions"></a> Autorisations

Requiert une autorisation ALTER sur la table.

## <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio

### <a name="to-insert-columns-into-a-table-with-table-designer"></a>Pour insérer des colonnes dans une table à l'aide du Concepteur de tables

1. Dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur la table dans laquelle vous souhaitez ajouter des colonnes et choisissez **Conception**.
2. Cliquez sur la première cellule vide dans la colonne **Nom de la colonne** .
3. Tapez le nom de la colonne dans la cellule. Le nom de la colonne est une valeur requise.
4. Appuyez sur la touche TAB pour passer à la cellule **Type de données** et sélectionnez le type de données dans la liste déroulante.

   Il s’agit d’une valeur obligatoire, qui est utilisée comme valeur par défaut si vous n’en choisissez pas.

   > [!NOTE]
   > Vous pouvez modifier la valeur par défaut dans la boîte de dialogue **Options** située sous **Outils de base de données**.

5. Continuez à définir éventuellement d'autres propriétés des colonnes dans l'onglet **Propriétés des Colonnes** .

    > [!NOTE]
    > Les valeurs par défaut des propriétés des colonnes sont ajoutées lorsque vous créez une nouvelle colonne, mais vous pouvez les modifier sous l’onglet **Propriétés de la colonne** .

6. Quand vous avez fini d’ajouter des colonnes, dans le menu **Fichier**, choisissez **Enregistrer** _nom de la table_.
  
## <a name="TsqlProcedure"></a> Utilisation de Transact-SQL
  
### <a name="to-insert-columns-into-a-table"></a>Pour insérer des colonnes dans une table  
  
L'exemple suivant ajoute deux colonnes à la table `dbo.doc_exa`.

```sql
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;
```

#### <a name="FollowUp"></a> Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)
