---
title: SQL Server - Objet Access Methods | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Access Methods object
- SQLServer:Access Methods
ms.assetid: 27558585-e780-48bb-a042-30d664662ebc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 96229c151957cd0b0bf91c248b4d96a294864181
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63251109"
---
# <a name="sql-server-access-methods-object"></a>SQL Server - Objet Access Methods
  L'objet **Access Methods** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs permettant de surveiller l'accès aux données logiques de la base de données. Les compteurs **Gestionnaire de tampons** permettent de surveiller l'accès physique aux pages de bases de données sur le disque. La surveillance des méthodes d'accès aux données de la base de données permet de déterminer s'il est possible d'améliorer les performances des requêtes en ajoutant ou en modifiant des index, en ajoutant ou en déplaçant des partitions, en ajoutant des fichiers ou des groupes de fichiers, en défragmentant des index ou en réécrivant des requêtes. Il est également possible d'utiliser les compteurs **Méthodes d'accès** pour surveiller le volume des données, les index ou l'espace libre dans la base de données. Ils indiquent ainsi le volume des données et leur fragmentation pour chaque instance du serveur. Une fragmentation excessive des index peut nuire aux performances.  
  
 Pour des informations détaillées sur le volume, la fragmentation et l'utilisation des données, utilisez les vues de gestion dynamique suivantes :  
  
-   [sys. dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql)  
  
-   [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)  
  
-   [sys. dm_db_partition_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql)  
  
-   [sys. dm_db_index_usage_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql)  
  
 Pour l'utilisation de l'espace dans la base de données **tempdb** au niveau fichier, tâche et session, utilisez les vues de gestion dynamique suivantes :  
  
-   [sys. dm_db_file_space_usage &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql)  
  
-   [sys. dm_db_task_space_usage &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql)  
  
-   [sys. dm_db_session_space_usage &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql)  
  
 Ce tableau décrit les compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Access Methods** permettent de surveiller l'accès physique aux pages de bases de données sur le disque.  
  
|Compteurs méthodes d'accès de SQL Server|Description|  
|----------------------------------------|-----------------|  
|**Lots de nettoyages par seconde**|Nombre de traitements par secondes effectués par la tâche en arrière-plan qui nettoie les unités d'allocation supprimées et différées.|  
|**Nettoyages au/s**|Nombre d'unités d'allocation par secondes supprimées par la tâche en arrière-plan qui nettoie les unités d'allocation supprimées et différées. Chaque suppression d'unité d'allocation nécessite plusieurs traitements.|  
|**Nombre de créations LOB par référence**|Nombre de valeurs des objets de grande taille (lob) passées par référence. Les objets de grande taille passés par référence sont utilisés dans certaines opérations en bloc pour éviter le coût de passage par valeur.|  
|**Nombre d’utilisations LOB par référence**|Nombre de valeurs LOB par référence ayant été utilisées. Les objets de grande taille passés par référence sont utilisés dans certaines opérations en bloc pour éviter le coût de passage par valeur.|  
|**Nombre d’LOB avec lecture anticipée**|Nombre de pages d'objets de grande taille sur lesquelles une lecture par anticipation a eu lieu.|  
|**Nombre d’extractions de ligne**|Nombre de valeurs des colonnes ayant été extraites dans la ligne alors qu'elles étaient hors ligne.|  
|**Nombre de notifications push hors ligne**|Nombre de valeurs des colonnes ayant été envoyées hors ligne alors qu'elles étaient dans la ligne.|  
|**Unités Analytics supprimés différés**|Nombre d'unités d'allocation en attente de suppression par la tâche en arrière-plan qui nettoie les unités d'allocation supprimées et différées.|  
|**Ensembles de lignes supprimés différés**|Nombre d'ensembles de lignes créés suite à des opérations abandonnées de construction d'index en ligne en attente de suppression par la tâche en arrière-plan qui nettoie les ensembles de lignes supprimés et différés.|  
|**Nettoyages d’ensembles de lignes supprimés/s**|Nombre d'ensembles de lignes par seconde créés suite à des opérations abandonnées de construction d'index en ligne supprimés par la tâche en arrière-plan qui nettoie les ensembles de lignes supprimés et différés.|  
|**Ensembles de lignes supprimés ignorés/s**|Nombre d'ensembles de lignes par seconde créés suite à des opérations abandonnées de construction d'index en ligne ignorés par la tâche en arrière-plan qui nettoie les ensembles de lignes créés, supprimés et différés.|  
|**Désallocations d’extensions/s**|Nombre d'extensions libérées par seconde dans toutes les bases de données de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Étendues allouées/s**|Nombre d'extensions allouées par seconde dans toutes les bases de données de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Lots de nettoyages ayant échoué/s**|Nombre de traitements par secondes qui ont échoué et qui ont demandé une autre tentative, effectuée par la tâche en arrière-plan qui nettoie les unités d'allocation supprimées et différées. L'échec peut être dû à un manque de mémoire ou d'espace disque, à une panne matérielle ou à d'autres raisons.|  
|**Échec du cookie de page feuille**|Nombre de fois où il n'a pas été possible d'utiliser un cookie de page feuille pendant une recherche d'index depuis que des modifications sont intervenues sur la page feuille. Le cookie accélère la recherche d'index.|  
|**Échec du cookie de page d’arborescence**|Nombre de fois où il n'a pas été possible d'utiliser un cookie de page d'arborescence pendant une recherche d'index depuis que des modifications sont intervenues sur les pages parentes de ces pages d'arborescences. Le cookie accélère la recherche d'index.|  
|**Enregistrements transmis/s**|Nombre d'enregistrements extraits par seconde via des pointeurs d'enregistrements transmis.|  
|**Extractions de pages d’espace libre/s**|Nombre de pages extraites par seconde par les analyses de l'espace libre. Ces analyses recherchent l'espace libre dans les pages déjà allouées à une unité d'allocation pour satisfaire les demandes d'insertion ou de modification des fragments d'enregistrements.|  
|**Analyses d’espace libre/s**|Nombre d'analyses par seconde lancées pour rechercher l'espace libre dans les pages déjà allouées à une unité d'allocation pour insérer ou modifier un fragment d'enregistrement. Chaque analyse peut trouver plusieurs pages.|  
|**Analyses complètes/s**|Nombre d'analyses complètes illimitées par seconde. Il peut s'agir d'analyses sur la table de base ou sur l'index complet.|  
|**Recherches d’index/s**|Nombre de recherches d'index par seconde. Ces recherches sont utilisées pour démarrer une analyse ou un repositionnement d'étendue, revalider un point d'analyse, extraire un enregistrement d'index unique et rechercher l'index pour localiser où une nouvelle ligne doit être insérée.|  
|**LobHandle créer un nombre**|Nombre d'objets de grande taille (lob) temporaires créés.|  
|**Nombre de destructions de LobHandle**|Nombre d'objets de grande taille (lob) temporaires détruits.|  
|**Nombre de création du fournisseur nombre fournisseurs**|Nombre de fournisseurs de services de stockage d'objets de grande taille (LobSSP) créés. Une table de travail créée par LobSSP.|  
|**Nombre de suppressions du fournisseur nombre fournisseurs**|Nombre de LobSSP détruits.|  
|**Nombre de troncations du fournisseur nombre fournisseurs**|Nombre de LobSSP tronqués.|  
|**Allocations de pages mixtes/s**|Nombre de pages allouées par seconde à partir d'extensions mixtes. Ces pages peuvent s'utiliser pour stocker les pages IAM et les huit premières pages allouées à une unité d'allocation.|  
|**Tentatives de compression de page/s**|Nombre de pages évaluées pour la compression de niveau page. Inclut les pages qui n'ont pas été compressées car des économies significatives n'ont pas pu être obtenues. Inclut tous les objets dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur les objets spécifiques, consultez [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).|  
|**Désallocations de pages/s**|Nombre de pages désallouées par seconde dans toutes les bases de données de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Elles comprennent les pages d'extensions mixtes et uniformes.|  
|**Fractionnements de pages/s**|Nombre de fractionnements de pages par seconde qui surviennent à la suite d'un débordement des pages d'index.|  
|**Pages allouées/s**|Nombre de pages allouées par seconde dans toutes les bases de données de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Elles comprennent les allocations des pages d'extensions mixtes et uniformes.|  
|**Pages compressées/s**|Nombre de pages de données compressées à l'aide de la compression PAGE. Inclut tous les objets dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur les objets spécifiques, consultez [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).|  
|**Analyses par sondage/s**|Nombre d'analyses par sondage par seconde utilisées pour trouver directement au plus une seule ligne qualifiée dans un index ou dans une table de base.|  
|**Analyses de plage/s**|Nombre d'analyses d'étendue qualifiées dans les index par seconde.|  
|**Revalidations du point d’analyse/s**|Nombre de revalidations du point d'analyse par seconde nécessaires à la poursuite de l'analyse.|  
|**Enregistrements fantômes ignorés/s**|Nombre d'enregistrements fantômes ignorés par seconde pendant des analyses.|  
|**Escalades de verrous de table/s**|Nombre de fois où les verrous sur une table ont été remontés à la granularité TABLE ou HoBT.|  
|**Utilisation du cookie de page feuille**|Nombre de fois où un cookie de page feuille a été utilisé pendant une recherche d'index depuis qu'aucune modification n'est intervenue sur la page feuille. Le cookie accélère la recherche d'index.|  
|**Cookie de page d’arborescence utilisé**|Nombre de fois où un cookie de page d'arborescence a été utilisé pendant une recherche d'index depuis qu'aucune modification n'est intervenue sur la page d'arborescence. Le cookie accélère la recherche d'index.|  
|**Fichiers créées/s**|Nombre de fichiers de travail créés par seconde. Par exemple, il est possible d'utiliser des fichiers de travail pour enregistrer des résultats temporaires de jointures et d'agrégats de hachage.|  
|**Tables de récréations créées/s**|Nombre de tables de travail créées par seconde. Par exemple, il est possible d'utiliser des tables de travail pour enregistrer des résultats temporaires de mise en attente de requêtes, de variables XML et de curseurs.|  
|**Ratio de tables de tables à partir du cache**|Pourcentage de tables de travail créées lorsque les deux premières pages de la table de travail n'étaient pas allouées mais étaient immédiatement disponibles dans la mémoire cache de la table de travail. (Lorsqu'une table de travail est supprimée, deux pages peuvent rester allouées : elles sont placées dans la mémoire cache de la table de travail pour augmenter les performances).|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
