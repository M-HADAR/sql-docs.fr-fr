---
title: Créer une planification
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ac1b19e7eb04003efe9002f4b7046838355a4f42
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245886"
---
# <a name="create-a-schedule"></a>Créer une planification
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Vous pouvez créer une planification pour les travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de SQL Server Management Objects.  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour créer une planification, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-schedule"></a>Pour créer une planification  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **SQL Server Agent**, cliquez avec le bouton droit sur **Travaux**, puis sélectionnez **Gérer les planifications**.  
  
3.  Dans la boîte de dialogue **Gérer les planifications** , cliquez sur **Nouvelle**.  
  
4.  Dans la zone **Nom** , attribuez-lui un nom.  
  
5.  Si vous ne souhaitez pas que la planification entre en vigueur immédiatement après sa création, désactivez la case à cocher **Activé** .  
  
6.  Pour **Type de planification**, sélectionnez l'une des valeurs suivantes :  
  
    -   Pour lancer le travail lorsque les processeurs atteignent une condition d'inactivité, cliquez sur **Démarrer dès que les processeurs sont inactifs**.  
  
    -   Si vous voulez qu'une planification s'exécute de façon répétée, cliquez sur **Périodique**. Pour définir la planification périodique, renseignez les groupes **Fréquence**, **Fréquence quotidienne**et **Durée** dans la boîte de dialogue.  
  
    -   Si vous souhaitez que la planification ne s'exécute qu'une seule fois, cliquez sur **Une fois**. Pour définir la planification **Une fois** , renseignez le groupe **Une seule occurrence** dans la boîte de dialogue.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-create-a-schedule"></a>Pour créer une planification  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_add_schedule (Transact-SQL)](https://msdn.microsoft.com/9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7).  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour créer une planification**  
  
Utilisez la classe **JobSchedule** à l’aide du langage de programmation de votre choix, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
