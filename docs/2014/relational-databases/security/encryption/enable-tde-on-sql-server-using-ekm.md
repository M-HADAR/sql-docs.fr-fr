---
title: Activer TDE à l’aide de EKM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], TDE using an EKM
- TDE, EKM how to
- EKM, TDE how to
- Transparent Data Encryption, using EKM
ms.assetid: b892e7a7-95bd-4903-bf54-55ce08e225af
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.openlocfilehash: 8b3f046017aa54f5db96878f8bfb6c435409d839
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74957229"
---
# <a name="enable-tde-using-ekm"></a>Activer le chiffrement transparent des données à l'aide de la gestion de clés extensible (EKM)
  Cette rubrique explique comment activer le chiffrement transparent des données (TDE) dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] afin de protéger une clé de chiffrement de base de données à l'aide d'une clé asymétrique stockée dans un module de gestion de clés extensible (EKM) avec [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Le chiffrement transparent des données chiffre le stockage d’une base de données entière à l’aide d’une clé symétrique appelée clé de chiffrement de base de données. La clé de chiffrement de base de données peut également être protégée à l'aide d'un certificat qui est lui-même protégé par la clé principale de base de données de la base de données MASTER Pour plus d’informations sur la protection de la clé de chiffrement de base de données à l’aide de la clé principale de base de données, consultez [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md). Pour plus d’informations sur la configuration de TDE lorsque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est exécuté sur une machine virtuelle Azure, consultez [Gestion de clés extensible à l’aide d’Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Pour activer le chiffrement TDE à l'aide de la gestion de clés extensible, avec Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous devez être un utilisateur doté de privilèges élevés (comme un administrateur système) pour créer une clé de chiffrement de base de données et chiffrer une base de données. Cet utilisateur doit pouvoir être authentifié par le module EKM.  
  
-   Au démarrage, le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] doit ouvrir la base de données. Pour ce faire, vous devez créer des informations d'identification qui seront authentifiées par la gestion de clés extensible et les ajouter à un nom de connexion reposant sur une clé asymétrique. Les utilisateurs ne peuvent pas se connecter à l'aide de ce nom de connexion, mais le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] sera en mesure de s'authentifier auprès du périphérique EKM.  
  
-   En cas de perte de la clé asymétrique stockée dans le module EKM, la base de données ne peut pas être ouverte par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si le fournisseur EKM vous permet de sauvegarder la clé asymétrique, vous devez créer une sauvegarde et la stocker dans un endroit sûr.  
  
-   Les options et les paramètres requis par votre fournisseur EKM peuvent différer de ce qui est indiqué dans l'exemple de code ci-dessous. Pour plus d'informations, consultez votre fournisseur EKM.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Cette rubrique utilise les autorisations suivantes :  
  
-   Pour modifier une option de configuration et exécuter l'instruction RECONFIGURE, vous devez disposer de l'autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
-   Requiert l'autorisation ALTER ANY CREDENTIAL.  
  
-   Nécessite l'autorisation ALTER ANY LOGIN.  
  
-   Requiert l'autorisation CREATE ASYMMETRIC KEY.  
  
-   Requiert l'autorisation CONTROL sur la base de données pour chiffrer la base de données.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-enable-tde-using-ekm"></a>Pour activer le chiffrement transparent des données (TDE) à l'aide de la gestion de clés extensible (EKM)  
  
1.  Copiez les fichiers fournis par le fournisseur EKM à un emplacement approprié sur l'ordinateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Dans cet exemple, le dossier **C:\EKM** est utilisé.  
  
2.  Installez les certificats requis par votre fournisseur EKM sur votre ordinateur.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne propose pas de fournisseur EKM. Chaque fournisseur EKM peut utiliser des procédures différentes pour l'installation, la configuration et l'autorisation des utilisateurs.  Consultez la documentation de votre fournisseur EKM pour effectuer cette étape.  
  
3.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
4.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
5.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Enable advanced options.  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Create a cryptographic provider, which we have chosen to call "EKM_Prov," based on an EKM provider  
  
    CREATE CRYPTOGRAPHIC PROVIDER EKM_Prov   
    FROM FILE = 'C:\EKM_Files\KeyProvFile.dll' ;  
    GO  
  
    -- Create a credential that will be used by system administrators.  
    CREATE CREDENTIAL sa_ekm_tde_cred   
    WITH IDENTITY = 'Identity1',   
    SECRET = 'q*gtev$0u#D1v'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
    GO  
  
    -- Add the credential to a high privileged user such as your   
    -- own domain login in the format [DOMAIN\login].  
    ALTER LOGIN Contoso\Mary  
    ADD CREDENTIAL sa_ekm_tde_cred ;  
    GO  
    -- create an asymmetric key stored inside the EKM provider  
    USE master ;  
    GO  
    CREATE ASYMMETRIC KEY ekm_login_key   
    FROM PROVIDER [EKM_Prov]  
    WITH ALGORITHM = RSA_512,  
    PROVIDER_KEY_NAME = 'SQL_Server_Key' ;  
    GO  
  
    -- Create a credential that will be used by the Database Engine.  
    CREATE CREDENTIAL ekm_tde_cred   
    WITH IDENTITY = 'Identity2'   
    , SECRET = 'jeksi84&sLksi01@s'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
  
    -- Add a login used by TDE, and add the new credential to the login.  
    CREATE LOGIN EKM_Login   
    FROM ASYMMETRIC KEY ekm_login_key ;  
    GO  
    ALTER LOGIN EKM_Login   
    ADD CREDENTIAL ekm_tde_cred ;  
    GO  
  
    -- Create the database encryption key that will be used for TDE.  
    USE AdventureWorks2012 ;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM  = AES_128  
    ENCRYPTION BY SERVER ASYMMETRIC KEY ekm_login_key ;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE AdventureWorks2012   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)  
  
-   [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)  
  
-   [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)  
  
-   [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [Gestion de clés extensible à l’aide d’Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
-   [Transparent Data Encryption avec Azure SQL Database](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)  
  
  
