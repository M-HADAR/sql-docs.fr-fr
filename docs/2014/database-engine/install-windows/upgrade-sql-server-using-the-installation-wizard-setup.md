---
title: Mettre à niveau vers SQL Server 2014 à l’aide de l’Assistant Installation (programme d’installation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- upgrading Database Engine
- Database Engine [SQL Server], upgrading
ms.assetid: cef118a5-a7ce-4bfa-8b9d-c81996284cfc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8330702d8c886cc9197dcd944878c3f794780205
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62775396"
---
# <a name="upgrade-to-sql-server-2014-using-the-installation-wizard-setup"></a>Effectuer une mise à niveau vers SQL Server 2014 à l'aide de l'Assistant Installation (programme d'installation)
  L'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit une arborescence de fonctionnalités unique pour mettre à niveau les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez également installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] côte à côte avec une version antérieure ou migrer les bases de données et les paramètres de configuration existants à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les appliquer à une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Mises à niveau de la version et de l'édition prises en charge](supported-version-and-edition-upgrades.md)  
  
-   [Utiliser plusieurs versions et instances de SQL Server](../../sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)  
  
-   [Mettre à niveau une instance de cluster de basculement SQL Server &#40;de l’installation&#41;](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)  
  
-   [Installer SQL Server 2014 à partir de l'invite de commandes](install-sql-server-from-the-command-prompt.md)  
  
-   [Utiliser l'Assistant Copie de base de données](../../relational-databases/databases/use-the-copy-database-wizard.md)  
  
> [!NOTE]  
>  La mise à niveau d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] n'est pas prise en charge sur un ordinateur qui exécute [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1. Pour plus d’informations sur les installations Server Core, consultez [installer SQL Server 2014 sur Server Core](install-sql-server-on-server-core.md).  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine doté des autorisations de lecture et d'exécution sur le partage distant, et qui représente un administrateur local.  
  
 Avant de mettre à niveau le [!INCLUDE[ssDE](../../includes/ssde-md.md)], consultez les rubriques suivantes :  
  
-   [Mettre à niveau vers SQL Server 2014](upgrade-sql-server.md)  
  
-   [Configurations matérielle et logicielle requises pour l'installation de SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Paramètres de l'outil d'analyse de configuration système](check-parameters-for-the-system-configuration-checker.md)  
  
-   [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Compatibilité descendante du moteur de base de données SQL Server](../sql-server-database-engine-backward-compatibility.md)  
  
> [!WARNING]  
>  N'oubliez pas que vous ne pouvez pas modifier les fonctionnalités à mettre à niveau, de même que vous ne pouvez pas ajouter de fonctionnalités pendant l'opération de mise à niveau. Pour plus d’informations sur la façon d’ajouter des fonctionnalités à une instance mise [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à niveau de une fois l’opération de mise à niveau terminée, consultez [Ajouter des fonctionnalités à une instance de SQL Server 2014 &#40;&#41;d’installation ](add-features-to-an-instance-of-sql-server-setup.md).  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-upgrade-to-includesscurrentincludessscurrent-mdmd"></a>Pour effectuer une mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
1.  Insérez le support d'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et, dans le dossier racine, double-cliquez sur Setup.exe. Pour effectuer l'installation à partir d'un partage réseau, accédez au dossier racine sur le partage, puis double-cliquez sur Setup.exe.  
  
2.  L'Assistant d'installation démarre le Centre d'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour mettre à niveau une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]existante de, cliquez sur **installation** dans la zone de navigation de gauche, puis cliquez sur **mettre [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]à niveau [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]partir de, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], ou **.  
  
3.  Dans la page Clé de produit, cliquez sur une option pour indiquer si vous effectuez une mise à niveau vers une édition gratuite de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou si vous disposez d'une clé PID pour une version de production du produit. Pour plus d’informations, consultez [éditions et composants de SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) et [mises à niveau de version et d’édition prises en charge](supported-version-and-edition-upgrades.md).  
  
4.  Dans la page Termes du contrat de licence, prenez connaissance du contrat de licence et, si vous en acceptez les termes, activez la case à cocher **J'accepte les termes du contrat de licence.** , puis cliquez sur **Suivant**. Pour aider à améliorer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez également activer l'option d'utilisation des fonctionnalités et envoyer des rapports à [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
5.  Dans la fenêtre Règles globales, la procédure d'installation passera automatiquement à la fenêtre Mises à jour du produit s'il n'existe aucune erreur de règle.  
  
6.  La page [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update s'affiche si la case à cocher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update n'est pas activée dans Panneau de configuration\Tous les éléments du Panneau de configuration\Windows Update\Modifier les paramètres. Une coche sur la page [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update permet de modifier les paramètres de l'ordinateur de façon à inclure les dernières mises à jour lorsque vous recherchez les mises à jour de Windows.  
  
7.  Dans la page Mises à jour du produit, les dernières mises à jour disponibles de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'affichent. Si vous ne souhaitez pas inclure les mises à jour, décochez la case **Inclure les mises à jour du produit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**. Si aucune mise à jour du produit n'est découverte, le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'affiche pas cette page et passe automatiquement à la page **Installer les fichiers d'installation** .  
  
8.  Sur la page Installer les fichiers d'installation, le programme d'installation fournit la progression du téléchargement, de l'extraction et de l'installation des fichiers d'installation. Si une mise à jour de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est trouvée, et est spécifiée pour être incluse, cette mise à jour est également installée.  
  
9. Dans la fenêtre Règles de mise à niveau, la procédure d'installation passera automatiquement à la fenêtre Sélectionner une instance s'il n'existe aucune erreur de règle.  
  
10. Dans la page Sélectionner une instance, spécifiez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à mettre à niveau. Pour mettre à niveau les outils d'administration et les fonctionnalités partagées, sélectionnez **Mettre à niveau les fonctionnalités partagées uniquement**.  
  
11. Dans la page Sélectionner les composants, les fonctionnalités à mettre à niveau seront présélectionnées. Une description de chaque groupe de composants apparaît dans le volet droit après que vous avez sélectionné le nom de la fonctionnalité.  
  
     Les composants requis pour les fonctionnalités sélectionnées sont affichés dans le volet droit. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe les composants requis qui n'ont pas déjà été installés lors de l'étape d'installation décrite plus loin dans cette procédure.  
  
    > [!NOTE]  
    >  Si vous avez choisi de mettre à niveau les fonctionnalités partagées en sélectionnant ** \<mettre à niveau les fonctionnalités partagées uniquement>** dans la page **Sélectionner une instance** , toutes les fonctionnalités partagées sont présélectionnées dans la page sélection de fonctionnalités. Tous les composants partagés sont mis à niveau à la fois.  
  
12. Dans la page Configuration de l'instance, spécifiez l'ID d'instance pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     **ID d’instance** : par défaut, le nom de l’instance est utilisé comme ID d’instance. Il permet d'identifier les répertoires d'installation et les clés de Registre de votre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tel est le cas pour les instances par défaut et les instances nommées. Pour une instance par défaut, le nom de l'instance et l'ID d'instance sont MSSQLSERVER. Pour utiliser un ID d’instance non défini par défaut, indiquez une valeur dans la zone de texte **ID d’instance** .  
  
     Tous les Service Packs et mises à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'appliqueront à chaque composant d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     **Instances installées** : la grille affiche les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de qui se trouvent sur l’ordinateur où le programme d’installation s’exécute. Si une instance par défaut est déjà installée sur l'ordinateur, vous devez installer une instance nommée de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
13. Le flux de travail du reste de cette rubrique dépend des fonctionnalités que vous avez spécifiées pour votre installation. Il est possible que les pages ne soient pas toutes visibles, en fonction de vos sélections.  
  
14. Dans la page Configuration du serveur - Comptes de service, les comptes de service par défaut s’affichent pour les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les services réels configurés dans cette page dépendent des fonctionnalités que vous mettez à niveau.  
  
     Les informations d'authentification et de connexion sont transférées à partir de l'instance antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez attribuer le même compte de connexion à tous les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou configurer chaque compte de service individuellement. Vous pouvez également spécifier si les services démarrent automatiquement, sont démarrés manuellement ou sont désactivés. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] vous recommande de configurer les comptes de service individuellement afin de fournir des privilèges moindres pour chaque service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer leurs tâches. Pour plus d’informations, consultez [configurer les comptes de service Windows et les autorisations](../configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
     Pour spécifier le même compte de connexion pour tous les comptes de service dans cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], fournissez les informations d'identification dans les champs en bas de page.  
  
     **Note de sécurité**[!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
     Lorsque vous avez terminé de spécifier les informations de connexion pour les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur **Suivant**.  
  
15. Dans la page des options de mise à niveau de recherche en texte intégral, spécifiez les options de mise à niveau pour les bases de données mises à niveau. Pour plus d’informations, consultez [Options de mise à niveau de recherche en texte intégral](../../sql-server/install/full-text-search-upgrade-options.md).  
  
16. La fenêtre Règles de fonctionnalité avancera automatiquement si toutes les règles passent.  
  
17. La page Prêt pour la mise à niveau affiche une arborescence des options d'installation spécifiées durant l'exécution du programme d'installation. Pour continuer, cliquez sur **Installer**. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe d'abord les composants requis pour les fonctionnalités sélectionnées, puis installe les fonctionnalités.  
  
18. Au cours de l'installation, la page de progression fournit des informations d'état de sorte que vous puissiez contrôler la progression de l'installation au fil de l'exécution du programme d'installation.  
  
19. Après l'installation, la page Terminé fournit un lien vers le fichier journal résumé pour l'installation et d'autres remarques importantes. Pour terminer le processus d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur **Fermer**.  
  
20. Redémarrez l'ordinateur si vous êtes invité à le faire. Il est important de lire le message affiché par l'Assistant Installation à la fin de l'installation. Pour plus d’informations sur les fichiers journaux d’installation, consultez [Afficher et lire les fichiers journaux d’installation de SQL Server](view-and-read-sql-server-setup-log-files.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir effectué la mise à niveau vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], effectuez les tâches suivantes :  
  
-   **Inscrire vos serveurs-la** mise à niveau supprime les paramètres du Registre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]pour l’instance précédente de. Après la mise à niveau, vous devez réinscrire vos serveurs.  
  
-   **Mettre à jour les statistiques** : pour optimiser les performances des requêtes, nous vous recommandons de mettre à jour les statistiques sur toutes les bases de données après la mise à niveau. Utilisez la procédure stockée `sp_updatestats` pour mettre à jour les statistiques des tables définies par l'utilisateur dans les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Configurer votre nouvelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation** : pour réduire la surface d’exposition attaquable d’un système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , installe et active de manière sélective les services et fonctionnalités clés. Pour plus d'informations sur la configuration de la surface d'exposition, consultez le fichier Lisezmoi de cette version.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à niveau vers SQL Server 2014](upgrade-sql-server.md)   
 [Compatibilité descendante](../../getting-started/backward-compatibility.md)  
  
  
