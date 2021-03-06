---
title: MSSQL_ENG018752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018752 error
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0558ded6ed10284df39270ddeca9d92434daf40e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63057536"
---
# <a name="mssql_eng018752"></a>MSSQL_ENG018752
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|18752|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Un seul Agent de lecture du journal ou une seule procédure liée au journal (sp_repldone, sp_replcmds et sp_replshowcmds) peut se connecter à une base de données à la fois. Si vous avez exécuté une procédure liée au journal, supprimez la connexion à travers laquelle fut exécutée la procédure ou exécutez sp_replflush sur cette connexion avant de démarrer l'Agent de lecture du journal ou d'exécuter toute autre procédure liée au journal.|  
  
## <a name="explanation"></a>Explication  
 Plusieurs connexions tentent actuellement d'exécuter l'une des procédures suivantes : **sp_repldone**, **sp_replcmds**ou **sp_replshowcmds**. Les procédures stockées [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) et [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) sont utilisées par l’Agent de lecture du journal pour détecter et mettre à jour les informations relatives aux transactions répliquées dans une base de données publiée. La procédure stockée [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) est utilisée pour résoudre certains problèmes rencontrés en réplication transactionnelle.  
  
 Cette erreur se produit dans les circonstances suivantes :  
  
-   Si l'Agent de lecture du journal d'une base de données publiée est en cours d'exécution et si un deuxième Agent de lecture de journal tente de s'exécuter sur la même base de données, cette erreur est émise pour le second agent et apparaît dans l'historique de l'agent.  
  
     Dans les situations où plusieurs agents sont impliqués, il est possible que l'un d'entre eux résulte d'un processus orphelin.  
  
-   Si l'Agent de lecture du journal d'une base de données publiée est démarré et qu'un utilisateur exécute **sp_repldone**, **sp_replcmds**ou **sp_replshowcmds** sur la même base de données, cette erreur est émise dans l'application où la procédure stockée a été exécutée (par exemple **sqlcmd**).  
  
-   Si aucun Agent de lecture de journal n'est en cours d'exécution sur une base de données publiée et si un utilisateur exécute **sp_repldone**, **sp_replcmds**ou **sp_replshowcmds** , puis omet de fermer la connexion sur laquelle la procédure a été exécutée, cette erreur est générée lorsque l'Agent de lecture de journal tente de se connecter à la base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante peut vous aider à résoudre ce problème. Si l'une des étapes permet à l'Agent de lecture de journal de démarrer sans erreur, il n'est pas nécessaire d'exécuter le reste de la procédure.  
  
-   Vérifiez dans l'historique de l'Agent de lecture de journal s'il y a d'autres erreurs qui pourraient être cause de cette erreur. Pour plus d’informations sur l’affichage de l’État et des détails des erreurs des agents dans le moniteur de réplication, consultez [afficher des informations et effectuer des tâches à l’aide du moniteur](monitor/view-information-and-perform-tasks-replication-monitor.md)  
  
-   Recherchez dans le résultat de [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) s’il existe des numéros spécifiques d’identification de processus (SPID) relatifs à la base de données publiée. Fermez toute connexion susceptible d'avoir exécuté **sp_repldone**, **sp_replcmds**ou **sp_replshowcmds**.  
  
-   Redémarrez l'Agent de lecture du journal. Pour plus d’informations, consultez [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
-   Redémarrez le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (mettez-le hors ligne ou en ligne dans un cluster) sur le serveur de distribution. S'il est possible qu'une tâche planifiée ait exécuté **sp_repldone**, **sp_replcmds**ou **sp_replshowcmds** à partir d'autres instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , redémarrez également l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour ces instances. Pour plus d’informations, consultez [Démarrer, arrêter ou suspendre le service SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).  
  
-   Exécutez [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) sur le serveur de publication sur la base de données de publication, puis redémarrez l’Agent de lecture du journal.  
  
-   Si l'erreur continue de se produire, augmentez le facteur de journalisation de l'agent et spécifiez un fichier de sortie pour le journal. En fonction du contexte de l'erreur, cette action peut fournir des pistes conduisant à l'erreur et/ou à d'autres messages d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)   
 [Agent de lecture du journal des réplications](agents/replication-log-reader-agent.md)  
  
  
