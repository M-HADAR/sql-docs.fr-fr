---
title: Supprimer le témoin d’une session de mise en miroir de bases de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], turning off
- witness [SQL Server], removing
- database mirroring [SQL Server], witness
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0fee60fa1a78c2d6d0becb63b2319105016adf1c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754676"
---
# <a name="remove-the-witness-from-a-database-mirroring-session-sql-server"></a>Supprimer le témoin d'une session de mise en miroir de bases de données (SQL Server)
  Cette rubrique explique comment supprimer un témoin depuis une session de mise en miroir de bases de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. À tout moment au cours d'une session de mise en miroir d'une base de données, le propriétaire de cette dernière peut désactiver le témoin pour cette session.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour remplacer supprimer le témoin, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [après avoir supprimé le témoin](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation ALTER sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-remove-the-witness"></a>Pour supprimer le témoin  
  
1.  Connectez-vous à l'instance du serveur principal puis, dans le volet **Explorateur d'objets** , cliquez sur le nom du serveur pour développer l'arborescence.  
  
2.  Développez **Bases de données**, puis sélectionnez la base de données dont vous souhaitez supprimer le témoin.  
  
3.  Cliquez avec le bouton droit sur la base de données, sélectionnez **Tâches**, puis cliquez sur **Miroir**. La page **Mise en miroir** de la boîte de dialogue **Propriétés de la base de données** s'affiche.  
  
4.  Pour supprimer le témoin, supprimez son adresse réseau de serveur du champ **Témoin** .  
  
    > [!NOTE]  
    >  Si vous passez du mode de sécurité élevée avec basculement automatique au mode haute performance, le champ **Témoin** est automatiquement supprimé.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-remove-the-witness"></a>Pour supprimer le témoin  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur l'une des instances de serveur partenaire.  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Émettez l'instruction suivante :  
  
     [ALTER database](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET WITNESS désactivé  
  
     où *nom_base_de_données* est le nom de la base de données en miroir.  
  
     L'exemple suivant supprime le témoin de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="FollowUp"></a>Suivi : après avoir supprimé le témoin  
 La désactivation du témoin modifie le [mode d’opération](database-mirroring-operating-modes.md)conformément au paramètre de sécurité des transactions :  
  
-   Si la sécurité des transactions a la valeur FULL (valeur par défaut), la session utilise le mode synchrone haute sécurité sans basculement automatique.  
  
-   Si la sécurité des transactions a la valeur OFF (désactivée), la session agit de manière asynchrone (en mode hautes performances) sans nécessiter de quorum. Lorsque la sécurité des transactions est désactivée, il est vivement recommandé de désactiver également le témoin.  
  
> [!TIP]  
>  Le paramètre de sécurité des transactions de la base de données est enregistré pour chaque serveur partenaire dans la vue de catalogue [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) des colonnes **mirroring_safety_level** et **mirroring_safety_level_desc**.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Ajouter un témoin de mise en miroir de bases de données à l’aide de l’authentification Windows &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [Ajouter ou remplacer un témoin de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Modifier la sécurité des transactions dans une session de mise en miroir de bases de données &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)   
 [Ajouter un témoin de mise en miroir de bases de données à l’aide de l’authentification Windows &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)   
 [Témoin de mise en miroir de base de données](database-mirroring-witness.md)  
  
  
