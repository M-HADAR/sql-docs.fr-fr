---
title: Migration des données Oracle vers SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Data Migration, Client-Side Migration
- Oracle Data Migration,Server-Side Migration
ms.assetid: e23c5268-41ed-4e55-9fe7-a11376202a13
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: c37f9c8e39a8a9dd87eabecba445b5ce7cef9028
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264676"
---
# <a name="migrating-oracle-data-into-sql-server-oracletosql"></a>Migration de données Oracle dans SQL Server (OracleToSQL)
Une fois que vous avez correctement synchronisé les objets convertis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]avec, vous pouvez migrer des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]d’Oracle vers.  
  
> [!IMPORTANT]  
> Si le moteur utilisé est le moteur de migration des données côté serveur, avant de pouvoir migrer des données, vous devez installer le pack d’extension SSMA pour Oracle et les fournisseurs Oracle sur l’ordinateur qui exécute SSMA. Le service SQL Server Agent doit également être en cours d’exécution. Pour plus d’informations sur l’installation du pack d’extension, voir [installation de composants serveur (OracleToSQL)](https://msdn.microsoft.com/33070e5f-4e39-4b70-ae81-b8af6e4983c5) .  
  
## <a name="setting-migration-options"></a>Définition des options de migration  
Avant de migrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des données vers, passez en revue les options de migration de projet dans la boîte de dialogue **paramètres du projet** .  
  
-   À l’aide de cette boîte de dialogue, vous pouvez définir des options telles que la taille de lot de migration, le verrouillage de table, la vérification des contraintes, la gestion des valeurs NULL et la gestion des valeurs d’identité. Pour plus d’informations sur les paramètres de migration de projet, consultez [paramètres du projet (migration) (OracleToSQL)](https://msdn.microsoft.com/fcd6b988-633b-4b2b-9f36-6368b5e86b60).  
  
-   Le **moteur de migration** de la boîte de dialogue **paramètres du projet** permet à l’utilisateur d’effectuer le processus de migration à l’aide de deux types de moteurs de migration de données :  
  
    1.  Moteur de migration de données côté client  
  
    2.  Moteur de migration de données côté serveur  
  
**Migration des données côté client :**  
  
-   Pour lancer la migration des données côté client, sélectionnez l’option **moteur de migration de données côté client** dans la boîte de dialogue **paramètres du projet** .  
  
-   Dans les **paramètres du projet**, l’option moteur de migration de **données côté client** est définie.  
  
    > [!NOTE]  
    > Le **moteur de migration de données côté client** se trouve dans l’application SSMA et n’est donc pas dépendant de la disponibilité du pack d’extension.  
  
**Migration des données côté serveur :**  
  
-   Pendant la migration des données côté serveur, le moteur réside sur la base de données cible. Il est installé par le biais du pack d’extension. Pour plus d’informations sur la façon d’installer le pack d’extension, consultez [installation de composants serveur sur SQL Server](installing-ssma-components-on-sql-server-oracletosql.md)  
  
-   Pour lancer la migration côté serveur, sélectionnez l’option **moteur de migration de données côté serveur** dans la boîte de dialogue **paramètres du projet** .  
  
## <a name="migrating-data-to-sql-server"></a>Migration des données vers SQL Server  
La migration des données est une opération de chargement en masse qui déplace des lignes de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de tables Oracle dans des tables de transactions. Le nombre de lignes chargées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans dans chaque transaction est configuré dans les paramètres du projet.  
  
Pour afficher les messages de migration, assurez-vous que le volet de sortie est visible. Dans le cas contraire, dans le menu **affichage** , sélectionnez **sortie**.  
  
**Pour migrer des données**  
  
1.  Vérifiez les points suivants :  
  
    -   Les fournisseurs Oracle sont installés sur l’ordinateur qui exécute SSMA.  
  
    -   Vous avez synchronisé les objets convertis avec la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  
  
2.  Dans l’Explorateur de métadonnées Oracle, sélectionnez les objets qui contiennent les données que vous souhaitez migrer :  
  
    -   Pour migrer des données pour tous les schémas, activez la case à cocher en regard de **schémas**.  
  
    -   Pour migrer des données ou omettre des tables individuelles, commencez par développer le schéma, développez **tables**, puis activez ou désactivez la case à cocher en regard de la table.  
  
3.  Pour migrer des données, deux cas se produisent :  
  
    **Migration des données côté client :**  
  
    -   Pour effectuer la **migration des données côté client**, sélectionnez l’option **moteur de migration de données côté client** dans la boîte de dialogue **paramètres du projet** .  
  
    **Migration des données côté serveur :**  
  
    -   Avant d’effectuer la migration des données côté serveur, vérifiez les éléments suivants :  
  
        1.  Le pack d’extension SSMA pour Oracle est installé sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de.  
  
        2.  Le service SQL Server Agent s’exécute sur l’instance de SQL Server.  
  
    -   Pour effectuer la **migration des données côté serveur**, sélectionnez l’option **moteur de migration de données côté serveur** dans la boîte de dialogue **paramètres du projet** .  
  
4.  Cliquez avec le bouton droit sur **schémas** dans l’Explorateur de métadonnées Oracle, puis cliquez sur **migrer les données**. Vous pouvez également migrer des données pour des objets individuels ou des catégories d’objets : cliquez avec le bouton droit sur l’objet ou son dossier parent. Sélectionnez l’option **migrer les données** .  
  
    > [!NOTE]  
    > Si le pack d’extension SSMA pour Oracle n’est pas installé sur l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]instance de et si le **moteur de migration de données côté serveur** est sélectionné, lors de la migration des données vers la base de données cible, l’erreur suivante s’est produite : «les composants de migration de données SSMA n’ont pas été trouvés sur SQL Server, la migration des données côté serveur n’est pas possible. Vérifiez si le pack d’extension est correctement installé. Cliquez sur **Annuler** pour mettre fin à la migration des données.  
  
5.  Dans la boîte de dialogue **se connecter à Oracle** , entrez les informations d’identification de connexion, puis cliquez sur **se connecter**. Pour plus d’informations sur la connexion à Oracle, consultez [se connecter à oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md)  
  
    Pour vous connecter à la base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de données cible, entrez les informations d’identification de connexion dans la boîte de dialogue **se connecter à SQL Server** , puis cliquez sur **se connecter**. Pour plus d’informations sur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]connexion à, consultez [se connecter à SQL Server](https://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Les messages s’affichent dans le volet de **sortie** . Une fois la migration terminée, le **rapport de migration des données** s’affiche. Si des données n’ont pas été migrées, cliquez sur la ligne qui contient les erreurs, puis cliquez sur **Détails**. Lorsque vous avez terminé avec le rapport, cliquez sur **Fermer**. Pour plus d’informations sur le rapport de migration de données, consultez [rapport de migration des données (SSMA commun)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Lorsque SQL Express Edition est utilisé comme base de données cible, seule la migration des données côté client est autorisée et la migration des données côté serveur n’est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
