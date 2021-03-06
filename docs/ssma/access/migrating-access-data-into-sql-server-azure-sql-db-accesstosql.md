---
title: Migration de données Access vers SQL Server-Azure SQL DB (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- bulk loading data
- data, loading into SQL Azure
- data, loading into SQL Server
- migrating databases, loading data
- migrating databases, options
- options, migrating data
- SQL Azure, migrating data into
- SQL Server, migrating data into
ms.assetid: f3b18af7-1af0-499d-a00d-a0af94895625
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8f0e93efee0c57c904c32ec52fbb560f973f21b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907146"
---
# <a name="migrating-access-data-into-sql-server---azure-sql-db-accesstosql"></a>Migration de données Access vers SQL Server-Azure SQL DB (AccessToSQL)
Une fois que vous avez créé avec succès les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]objets de base de données dans, vous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pouvez migrer des données d’accès à ou SQL Azure.  
  
## <a name="setting-migration-options"></a>Définition des options de migration  
Avant de migrer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données vers ou SQL Azure, passez en revue les options de migration de projet dans la boîte de dialogue **paramètres du projet** . Dans cette boîte de dialogue, vous pouvez définir la taille de lot de migration, le verrouillage de table, la vérification des contraintes, le déclenchement du déclencheur d’insertion, l’identité et la gestion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des valeurs NULL, et comment gérer les dates qui se trouvent en dehors de la plage. Pour plus d’informations, consultez [paramètres du projet (migration)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
## <a name="migrating-data"></a>Migration des données  
La migration des données est une opération de chargement en bloc qui déplace des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lignes de données vers ou SQL Azure dans des transactions. Le nombre de lignes à charger dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure dans chaque transaction est configuré dans les paramètres du projet.  
  
Pour afficher les messages de migration, assurez-vous que le volet de sortie est visible. Si ce n’est pas le cas, dans le menu **affichage** , sélectionnez **sortie**.  
  
**Pour migrer des données**  
  
1.  Assurez-vous que vous avez chargé les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base de données Access dans ou SQL Azure.  
  
2.  Dans l’Explorateur de métadonnées Access, sélectionnez les objets qui contiennent les données que vous souhaitez migrer :  
  
    -   Pour migrer des données pour une base de données entière, activez la case à cocher en regard du nom de la base de données.  
  
    -   Pour migrer des données à partir de tables individuelles, développez la base de données, développez **tables**, puis activez la case à cocher en regard de la table. Pour omettre les données de tables individuelles, désactivez la case à cocher.  
  
3.  Cliquez avec le bouton droit sur **bases de données** , puis sélectionnez **migrer des données**.  
  
Vous pouvez également migrer des données en dehors de SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’utilitaire [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]de ligne de commande **BCP** ou. Pour plus d’informations sur ces outils, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consultez la documentation en ligne de.  
  
## <a name="next-step"></a>étape suivante  
Si vous avez accès à des applications de base de données que vous souhaitez continuer à utiliser après la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] migration, liez les tables de base de données Access aux tables ou SQL Azure. Pour plus d’informations, consultez [liaison d’applications d’accès aux SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Définition des options de conversion et de migration](setting-conversion-and-migration-options-accesstosql.md)  
  
