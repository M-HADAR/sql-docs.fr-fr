---
title: Gérer et surveiller la recherche en texte intégral pour une instance de serveur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], about
- full-text search [SQL Server], server management
ms.assetid: 2733ed78-6d33-4bf9-94da-60c3141b87c8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a6ed18416eadf1c2cc664029588bf0201038c261
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011170"
---
# <a name="manage-and-monitor-full-text-search-for-a-server-instance"></a>Gérer et surveiller la recherche en texte intégral pour une instance de serveur
  L'administration de la recherche en texte intégral pour une instance de serveur comprend :  
  
-   Des tâches de gestion du système telles que la gestion du service du lanceur FDHOST (MSSQLFDLauncher), le redémarrage du processus hôte de démon de filtre si vous modifiez les informations d'identification du compte de service, la configuration des propriétés en texte intégral à l'échelle du serveur et la sauvegarde des catalogues de texte intégral. Au niveau du serveur, par exemple, vous pouvez spécifier une langue de texte intégral par défaut qui diffère de la langue par défaut de l'instance de serveur dans son ensemble.  
  
-   Configuration des composants linguistiques de texte intégral (analyseurs lexicaux et générateurs de formes dérivées, fichier de dictionnaire des synonymes, et mots vides et listes de mots vides).  
  
-   Configuration d'une base de données utilisateur pour la recherche en texte intégral. Cela implique de créer un ou plusieurs catalogues de texte intégral pour la base de données et de définir un index de recherche en texte intégral sur chaque table ou vue indexée sur laquelle vous souhaitez exécuter des requêtes de texte intégral.  
  
##  <a name="props"></a> Affichage ou modification des propriétés de serveur pour la recherche en texte intégral  
 Vous pouvez afficher les propriétés de recherche en texte intégral d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-view-and-change-server-properties-for-full-text-search"></a>Pour afficher et modifier les propriétés de serveur pour la recherche en texte intégral  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés du serveur** , cliquez sur la page **Avancé** pour afficher les informations du serveur relatives à la recherche en texte intégral. Les propriétés de recherche en texte intégral sont les suivantes :  
  
    -   **Langue de texte intégral par défaut**  
  
         Spécifie une langue par défaut pour les colonnes de texte intégral indexées. L'analyse linguistique des données de texte intégral indexées dépend de la langue des données. La valeur par défaut de cette option est la langue du serveur. Pour connaître le langue correspondant au paramètre affiché, consultez [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
    -   **Option de mise à niveau des index de recherche en texte intégral**  
  
         Cette propriété de serveur contrôle la manière dont les index de recherche en texte intégral sont migrés lors d'une mise à niveau d'une base de données [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] vers une version ultérieure. Cette propriété s'applique à la mise à niveau par attachement d'une base de données, restauration d'une sauvegarde de la base de données, restauration d'une sauvegarde de fichiers ou copie de la base de données à l'aide de l'Assistant Copie de base de données.  
  
         Les alternatives sont les suivantes :  
  
         **Importer**  
         Les catalogues de texte intégral sont importés. En général, l'importation est considérablement plus rapide que lors d'une reconstruction (rebuild). Par exemple, lorsque vous utilisez un seul processeur, l'importation s'exécute approximativement 10 fois plus vite que lors de la reconstruction. Toutefois, un catalogue de texte intégral importé n'utilise pas les analyseurs lexicaux nouveaux et améliorés introduits dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], ce qui fait que vous pouvez le cas échéant reconstruire vos catalogues de texte intégral au final.  
  
        > [!NOTE]  
        >  Le processus de reconstruction peut s'exécuter en mode multithread, et si plus de 10 processeurs sont disponibles, la reconstruction peut s'effectuer plus vite que l'importation si vous la laissez utiliser tous les processeurs.  
  
         Si aucun catalogue de texte intégral n'est disponible, les index de recherche en texte intégral associés sont reconstruits. Cette option est disponible uniquement pour les bases de données [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] .  
  
         **Recréation**  
         Les catalogues de texte intégral sont reconstruits à l'aide des analyseurs lexicaux nouveaux et améliorés. La reconstruction des index peut prendre du temps, et une quantité importante de ressources en termes d'UC et de mémoire peut être requise après la mise à niveau.  
  
         **Réinitialiser**  
         Les catalogues de texte intégral sont réinitialisés. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Les fichiers de catalogue de texte intégral sont supprimés, mais les métadonnées pour les catalogues de texte intégral et les index de recherche en texte intégral sont conservés. Après leur mise à niveau, tous les index de recherche en texte intégral ont le suivi des modifications désactivé et aucune analyse n'est démarrée automatiquement. Le catalogue reste vide tant que vous n'avez pas procédé manuellement à une alimentation complète, au terme de la mise à niveau.  
  
         Pour plus d’informations sur le choix d’une option de mise à niveau de texte intégral, consultez [mise à niveau de la recherche en texte intégral](upgrade-full-text-search.md).  
  
        > [!NOTE]  
        >  Vous pouvez aussi définir l’option de mise à niveau du catalogue de texte intégral à l’aide de l’action [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)**upgrade_option** .  
  
##  <a name="metadata"></a> Affichage des propriétés de serveur de texte intégral supplémentaires  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] Les fonctions peuvent être utilisées pour obtenir la valeur de différentes propriétés au niveau du serveur pour la recherche en texte intégral. Ces informations sont utiles pour administrer la recherche en texte intégral et résoudre les problèmes qui la concernent.  
  
 Le tableau ci-après recense les propriétés en texte intégral d'une instance de serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ainsi que leurs fonctions [!INCLUDE[tsql](../../../includes/tsql-md.md)] connexes.  
  
|Propriété|Description|Fonction|  
|--------------|-----------------|--------------|  
|`IsFullTextInstalled`|Indique si le composant de texte intégral est installé avec l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[FULLTEXTSERVICEPROPERTY](/sql/t-sql/functions/fulltextserviceproperty-transact-sql)<br /><br /> [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql)|  
|`LoadOSResources`|Indique si les analyseurs lexicaux et les filtres du système d'exploitation sont inscrits et utilisés avec cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|FULLTEXTSERVICEPROPERTY|  
|`VerifySignature`|Indique si seuls les fichiers binaires signés sont chargés par le Moteur d’indexation et de recherche en texte intégral.|FULLTEXTSERVICEPROPERTY|  
  
##  <a name="monitor"></a>Surveillance de l’activité de recherche en texte intégral  
 Plusieurs vues et fonctions de gestion dynamique sont utiles pour la surveillance de l'activité de recherche en texte intégral sur une instance de serveur.  
  
 **Pour afficher des informations sur les catalogues de texte intégral avec une activité d’alimentation en cours**  
  
-   [sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-active-catalogs-transact-sql)  
  
 **Pour afficher l’activité actuelle d’un processus hôte de démon de filtre**  
  
-   [sys.dm_fts_fdhosts &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-fdhosts-transact-sql)  
  
 **Pour afficher des informations sur les remplissages d’index en cours**  
  
-   [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)  
  
 **Pour afficher les tampons de mémoire dans un pool de mémoire qui sont utilisés dans le cadre d’une analyse ou d’une plage d’analyse.**  
  
-   [sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)  
  
 **Pour afficher les pools de mémoire partagée disponibles pour le composant rassembleur de texte intégral pour une analyse de texte intégral ou une plage d’analyse de texte intégral**  
  
-   [sys.dm_fts_memory_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)  
  
 **Pour afficher des informations sur chaque lot d’indexation de texte intégral**  
  
-   [sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-outstanding-batches-transact-sql)  
  
 **Pour afficher des informations sur les plages spécifiques liées à une alimentation en cours**  
  
-   [sys.dm_fts_population_ranges &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-population-ranges-transact-sql)  
  
  
