---
title: Restaurer la base de données (page Options) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.options.f1
ms.assetid: 9a75d48b-c25f-40f3-8ea1-32cfa8211754
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 266c127a8ef38a1a5701de24f9442861e604d84d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62875634"
---
# <a name="restore-database-options-page"></a>Restaurer la base de données (page Options)
  Utilisez la page **Options** de la boîte de dialogue **Restaurer la base de données** pour modifier le comportement et le résultat de l’opération de restauration.  
  
 **Pour utiliser SQL Server Management Studio pour restaurer une sauvegarde de base de données**  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  Lorsque vous spécifiez une tâche de restauration à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous pouvez générer un script [!INCLUDE[tsql](../../includes/tsql-md.md)] correspondant contenant les instructions RESTORE pour cette opération de restauration. Pour générer le script, cliquez sur **Script** et sélectionnez une destination pour le script. Pour plus d’informations sur la syntaxe de RESTORE, consultez [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).  
  
## <a name="options"></a>Options  
  
### <a name="restore-options"></a>Options de restauration  
 Pour modifier des aspects du comportement de l’opération de restauration, utilisez les options du volet **Options de restauration** .  
  
 **Remplacer la base de données existante [WITH REPLACE]**  
 L’opération de restauration remplacera les fichiers de toute base de données qui utilise actuellement le nom de base de données que vous spécifiez dans le champ **Restaurer sur**de la page [Général](../../integration-services/general-page-of-integration-services-designers-options.md) de la boîte de dialogue **Restaurer la base de données** . Les fichiers de la base de données existante seront remplacés même si vous restaurez des sauvegardes à partir d'une base de données différente vers le nom de base de données existant. L’activation de cette option revient à utiliser l’option REPLACE dans une instruction [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) ([!INCLUDE[tsql](../../includes/tsql-md.md)]).  
  
> [!CAUTION]  
>  Utilisez cette option uniquement après un examen attentif. Pour plus d’informations, consultez [Arguments RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
 **Conserver les paramètres de la réplication [WITH KEEP_REPLICATION]**  
 Conserve les paramètres de réplication lors de la restauration d'une base de données publiée sur un serveur autre que celui sur lequel la base de données a été créée. Cette option est utile seulement si la base de données a été répliquée lors de la création de la sauvegarde.  
  
 Cette option est disponible uniquement avec l’option **Laisser la base de données opérationnelle en restaurant les transactions non validées** (décrite plus bas dans ce tableau) qui équivaut à restaurer une sauvegarde avec l’option RECOVERY.  
  
 L’activation de cette option revient à utiliser l’option KEEP_REPLICATION dans une instruction [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) .  
  
 Pour plus d’informations, consultez [Sauvegarder et restaurer des bases de données répliquées](../replication/administration/back-up-and-restore-replicated-databases.md).  
  
 **Restreindre l'accès à la base de données restaurée [WITH RESTRICTED_USER]**  
 Limite l’accès à la base de données restaurée aux membres de **db_owner**, **dbcreator**ou **sysadmin**.  
  
 La sélection de cette option équivaut à utiliser l'option RESTRICTED_USER dans une instruction RESTORE.  
  
### <a name="recovery-state"></a>État de récupération  
 Pour déterminer l’état de la base de données après l’opération de restauration, vous devez sélectionner l’une des options du volet **État de récupération** .  
  
 **RESTORE WITH RECOVERY**  
 Récupère la base de données après avoir restauré la base de données finale sélectionnée dans la grille **Jeux de sauvegarde à restaurer**de la [page Général](../../integration-services/general-page-of-integration-services-designers-options.md). Il s’agit de l’option par défaut. Elle revient à spécifier WITH RECOVERY dans une instruction [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) ([!INCLUDE[tsql](../../includes/tsql-md.md)]).  
  
> [!NOTE]  
>  Avec le mode de restauration complète ou le mode de récupération utilisant les journaux de transactions, choisissez cette option si vous restaurez tous les fichiers journaux maintenant.  
  
 **RESTORE WITH NORECOVERY**  
 Laisse la base de données en état de restauration. Cela vous permet de restaurer des sauvegardes supplémentaires dans le chemin d'accès de récupération actuel. Pour récupérer la base de données, vous devez effectuer une opération de restauration en utilisant l'option RESTORE WITH RECOVERY (voir l'option précédente).  
  
 Cette option revient à spécifier WITH NORECOVERY dans une instruction RESTORE.  
  
 Si vous sélectionnez cette option, l'option **Conserver les paramètres de réplication** n'est pas disponible.  
  
 **RESTORE WITH STANDBY**  
 Maintient la base de données dans un état d'attente, dans lequel elle est disponible pour un accès limité en lecture seule. Cette option revient à spécifier WITH STANDBY dans une instruction RESTORE.  
  
 Si vous sélectionnez cette option, vous devez spécifier un fichier d’annulation dans la zone de texte **Fichiers d’annulation** . Ce fichier d'annulation permet d'annuler les effets de la récupération.  
  
 **Fichiers d’annulation**  
 Spécifie un fichier d'annulation. Vous pouvez rechercher le fichier d'annulation ou entrer son chemin d'accès directement dans la zone de texte.  
  
### <a name="tail-log-backup"></a>Sauvegarde de la fin du journal  
 Permet d'indiquer qu'une sauvegarde de la fin du journal doit être effectuée avec la restauration de la base de données.  
  
 **Sauvegarder la fin du journal avant la restauration**  
 Activez cette case à cocher pour indiquer qu'une sauvegarde de la fin du journal doit être effectuée.  
  
> [!NOTE]  
>  Si la limite que vous avez sélectionnée dans la boîte de dialogue [Chronologie de sauvegarde](backup-timeline.md) requiert une sauvegarde de la fin du journal, cette case est activée et vous ne pouvez pas la modifier.  
  
 **Fichier de sauvegarde**  
 Spécifie un fichier de sauvegarde de la fin du journal. Vous pouvez rechercher le fichier de sauvegarde ou entrer son nom directement dans la zone de texte.  
  
### <a name="server-connections"></a>Connexions serveur  
 Vous permet de fermer les connexions de base de données existantes.  
  
 **Fermer les connexions existantes**  
 Les opérations de restauration peuvent échouer s'il existe des connexions actives à la base de données. Activez l'option **Fermer les connexions existantes** pour garantir que toutes les connexions actives entre [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et la base de données sont fermées. Cette case à cocher définit la base de données en mode mono-utilisateur avant d'effectuer les opérations de restauration, et définit la base de données en mode multi-utilisateur une fois l'opération terminée.  
  
### <a name="prompt"></a>Prompt  
 **Demander confirmation avant chaque restauration de sauvegarde**  
 Indique que, une fois chaque sauvegarde restaurée, la boîte de dialogue **Continuer la restauration** s’affichera pour vous inviter à confirmer la poursuite de la séquence de restauration. Cette boîte de dialogue affiche le nom du support de sauvegarde suivant (s'il est connu), ainsi que le nom et la description du jeu de sauvegarde suivant.  
  
 Cette option vous permet d'interrompre momentanément une séquence de restauration après avoir restauré un nombre quelconque de sauvegardes. Elle est particulièrement utile lorsque vous devez échanger des bandes pour différents supports de sauvegarde, par exemple quand le serveur dispose d'un seul périphérique à bandes. Lorsque vous êtes prêt à continuer, cliquez sur **OK**.  
  
 Vous pouvez interrompre une séquence de restauration en cliquant sur **Non**. La base de données est conservée dans l'état de restauration. Vous pouvez quand vous le souhaitez poursuivre la séquence de restauration en continuant avec la sauvegarde suivante décrite dans la boîte de dialogue **Continuer la restauration** . La procédure de restauration de la sauvegarde suivante varie selon qu'elle contient des données ou des journaux de transaction, comme suit :  
  
-   Si la sauvegarde suivante est une sauvegarde complète ou différentielle, utilisez à nouveau la tâche **Restaurer la base de données** .  
  
-   Si la sauvegarde suivante est une sauvegarde de fichiers, utilisez la tâche **Restaurer les fichiers et les groupes de fichiers**. Pour plus d’informations, consultez [Restaurer des fichiers et des groupes de fichiers &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md).  
  
-   S'il s'agit d'une sauvegarde de journal, utilisez la tâche **Restaurer le journal des transactions** . Pour plus d’informations sur la reprise d’une séquence de restauration en restaurant un journal de transactions, consultez [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Restaurer une sauvegarde à partir d’une unité &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)   
 [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)   
 [Appliquer les sauvegardes du journal des transactions &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Restaurer la base de données &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
