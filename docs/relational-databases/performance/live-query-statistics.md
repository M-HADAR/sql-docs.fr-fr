---
title: Statistiques des requêtes actives | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- query statistics [SQL Server] live query stats
- live query statistics
- debugging [SQL Server], live query stats
- statistics [SQL Server], live query statistics
- query profiling
- lightweight query profiling
- lightweight profiling
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 724eb513c3a48916e1083e3ce5bb50251896d381
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "73983250"
---
# <a name="live-query-statistics"></a>Statistiques des requêtes dynamiques
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] offre la possibilité de visualiser le plan d’exécution dynamique d’une requête active. Ce plan de requête active fournit des insights en temps réel sur le processus d’exécution des requêtes à mesure que les contrôles passent d’un [opérateur de plan de requête](../../relational-databases/showplan-logical-and-physical-operators-reference.md) à un autre. Le plan de requête active affiche la progression globale de la requête ainsi que des statistiques d’exécution de niveau opérateur telles que le nombre de lignes produites, le temps écoulé, la progression de l’opérateur, etc. Vous pouvez accéder à ces données en temps réel sans avoir à attendre l’exécution de la requête ; ces statistiques d’exécution se révèlent donc extrêmement utiles pour résoudre les problèmes de performances de requêtes. Cette fonctionnalité est disponible à partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], mais elle peut fonctionner avec [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  

> [!NOTE]
> En interne, les statistiques des requêtes actives utilisent la vue de gestion dynamique [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md).
  
**S’applique à** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et versions ultérieures).  
  
> [!WARNING]  
> Cette fonctionnalité est principalement utilisée à des fins de dépannage. Son utilisation peut légèrement ralentir les performances globales des requêtes, en particulier dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Pour plus d’informations, consultez [Infrastructure du profilage de requête](../../relational-databases/performance/query-profiling-infrastructure.md).  
> Cette fonctionnalité peut être utilisée avec le [débogueur Transact-SQL](../../relational-databases/scripting/configure-firewall-rules-before-running-the-tsql-debugger.md).  
  
## <a name="to-view-live-query-statistics-for-one-query"></a>Pour afficher les statistiques des requêtes actives pour une requête 
  
1.  Pour afficher le plan d’exécution des requêtes actives, accédez au menu Outils et cliquez sur l’icône **Inclure les statistiques des requêtes actives**.  
  
     ![Bouton Statistiques des requêtes actives de la barre d’outils](../../relational-databases/performance/media/livequerystatstoolbar.png "Bouton Statistiques des requêtes actives de la barre d’outils")  
  
     Vous pouvez également accéder au plan d’exécution des requêtes actives en cliquant avec le bouton droit sur une requête sélectionnée dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et en cliquant sur **Inclure les statistiques des requêtes actives**.  
  
     ![Bouton Statistiques des requêtes actives du menu contextuel](../../relational-databases/performance/media/livequerystatsmenu.png "Bouton Statistiques des requêtes actives du menu contextuel")  
  
2.  Exécutez maintenant la requête. Le plan de requête active affiche la progression globale de la requête et les statistiques d’exécution (par exemple, temps écoulé, progression, etc.) pour les opérateurs du plan de requête. Les informations relatives à la progression de la requête et les statistiques d’exécution sont régulièrement mises à jour tout au long de l’exécution de la requête. Vous pouvez utiliser ces informations pour comprendre le processus global d’exécution de la requête, déboguer les longues requêtes, les requêtes qui s’exécutent indéfiniment et les requêtes qui entraînent un dépassement tempdb, ou encore résoudre les problèmes de délai d’attente.  
  
     ![Bouton Statistiques des requêtes actives du plan d’exécution de requêtes](../../relational-databases/performance/media/livequerystatsplan.png "Bouton Statistiques des requêtes actives du plan d’exécution de requêtes")  
  
## <a name="to-view-live-query-statistics-for-any-query"></a>Pour afficher les statistiques des requêtes actives pour n’importe quelle requête 

Vous pouvez également cliquer avec le bouton droit sur n’importe quelle requête dans la table **Processus** ou **Requêtes coûteuses actives** du **[Moniteur d’activité](../../relational-databases/performance-monitor/activity-monitor.md)** pour accéder au plan d’exécution actif.  
  
 ![Bouton Statistiques des requêtes actives du Moniteur d’activité](../../relational-databases/performance/media/livequerystatsactmon.png "Bouton Statistiques des requêtes actives du Moniteur d’activité")  
  
## <a name="remarks"></a>Notes  
 L’infrastructure de profil de statistiques doit être activée pour que les statistiques de requêtes actives puissent capturer des informations sur la progression des requêtes. En fonction de la version, la surcharge peut être significative. Pour plus d’informations sur cette surcharge, consultez [Infrastructure du profilage de requête](../../relational-databases/performance/query-profiling-infrastructure.md).
  
## <a name="permissions"></a>Autorisations  
 Nécessite une autorisation `SHOWPLAN` au niveau de la base de données pour l’écriture de données dans la page de résultats **Statistiques des requêtes actives**, une autorisation `VIEW SERVER STATE` au niveau du serveur pour l’affichage des statistiques actives, ainsi que toutes les autorisations nécessaires pour l’exécution de la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Outils de surveillance et d’optimisation des performances](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Ouvrir le Moniteur d’activité &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)     
 [Moniteur d’activité](../../relational-databases/performance-monitor/activity-monitor.md)     
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
 [Indicateurs de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
 [Guide de référence des opérateurs Showplan logiques et physiques](../../relational-databases/showplan-logical-and-physical-operators-reference.md)     
 [Infrastructure du profilage de requête](../../relational-databases/performance/query-profiling-infrastructure.md)   
