---
title: Créer la base de données de modifications SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f53fe9d295fdd5cd34c6391332af12b9f6788668
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71294761"
---
# <a name="create-the-sql-server-change-database"></a>Créer la base de données de modification SQL Server

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Lorsque vous démarrez l'Assistant Nouvelle instance, la page Créer une base de données CDC s'ouvre. Cette page permet de fournir des informations sur la nouvelle instance de capture de données modifiées et de créer une nouvelle base de données de modification.  
  
 Lorsque vous créez une base de données CDC, elle est activée pour SQL Server CDC et cette activation requiert une connexion membre du rôle serveur fixe `sysadmin` .  
  
 Lorsqu'un utilisateur qui démarre l'Assistant Création d'une instance Oracle CDC n'est pas membre du rôle serveur fixe `sysadmin` , la boîte de dialogue Connexion à SQL Server s'ouvre et vous invite à entrer les informations d'identification pour un membre du rôle sysadmin de façon à effectuer la tâche Activer la base de données pour SQL Server CDC. Lorsque la base de données CDC est créée, la connexion `sysadmin` est ignorée et la tâche reprend avec la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'origine utilisée lorsque la console du concepteur Oracle a été ouverte.  
  
> [!IMPORTANT]  
>  Pour les tâches autres que l’activation de la base de données pour SQL Server CDC, la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée pour exécuter l’Assistant Nouvelle instance doit disposer du rôle serveur fixe `dbcreator` et des autorisations UPDATE sur la base de données MSXDBCDC.  
  
 Pour plus d'informations sur la saisie de données dans la boîte de dialogue Connexion à SQL Server, consultez [SQL Server Connection for Instance Creation](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md).  
  
## <a name="options"></a>Options  
 **Instance Oracle CDC**  
 Entrez les informations suivantes sur l'instance CDC que vous créez.  
  
-   **Nom**: tapez le nom du nouveau service. Ce sera également le nom de la nouvelle base de données modifiée.  
  
-   **Description**: tapez une description de la nouvelle instance pour vous aider à l'identifier. Ce paramètre est facultatif.  
  
 **Base de données modifiée SQL Server**  
 Cette section est utilisée pour créer la base de données.  
  
1.  **Modifier la base de données**: nom de la nouvelle base de données modifiée. Le nom de la base de données est identique au nom donné à l'instance. Ce champ en lecture seule affiche le chemin d'accès complet à la base de données.  
  
2.  **Créer une base de données**: cliquez sur **Créer une base de données** pour créer la base de données.  
  
     Pour créer la base de données, la connexion doit posséder le rôle serveur `sysasmin` . Pour plus d'informations, consultez la remarque sur la sécurité ci-dessus.  
  
     Après avoir créé la base de données, vous pouvez cliquer sur **Suivant** pour [Connect to an Oracle Source Database](../../integration-services/change-data-capture/connect-to-an-oracle-source-database.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : créer l'instance SQL Server de base de données de modifications](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Service de capture de données modifiées Oracle](../../integration-services/change-data-capture/the-oracle-cdc-service.md)  
  
  
