---
title: sysmail_add_profile_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_profile_sp_TSQL
- sysmail_add_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profile_sp
ms.assetid: a828e55c-633a-41cf-9769-a0698b446e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4bd7f90688d61f9ecee487d553393e38bed82e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70211278"
---
# <a name="sysmail_add_profile_sp-transact-sql"></a>sysmail_add_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Crée un nouveau profil de messagerie de base de données.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_add_profile_sp [ @profile_name = ] 'profile_name'  
    [ , [ @description = ] 'description' ]  
    [ , [ @profile_id = ] new_profile_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_name = ] 'profile\_name'`Nom du nouveau profil. *profile_name* est de **type sysname**, sans valeur par défaut.  
 
   > [!NOTE]
   > Le nom de profil qui utilise l’agent SQL Azure SQL Managed Instance doit être appelé **AzureManagedInstance_dbmail_profile**
  
`[ @description = ] 'description'`Description facultative du nouveau profil. *Description* est de type **nvarchar (256)**, sans valeur par défaut.  
  
`[ @profile_id = ] _new\_profile\_id OUTPUT`Retourne l’ID du nouveau profil. *new_profile_id* est de **type int**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 Un profil de messagerie de base de données contient un nombre quelconque de comptes de messagerie de base de données. Les procédures stockées de la messagerie de base de données peuvent faire référence à un profil par son nom ou par l'ID généré par cette procédure. Pour plus d’informations sur l’ajout d’un compte à un profil, consultez [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md).  
  
 Le nom et la description du profil peuvent être modifiés à l’aide de la procédure stockée **sysmail_update_profile_sp**, tandis que l’ID de profil reste constant pendant toute la durée de vie du profil.  
  
 Le nom du profil doit être unique pour Microsoft [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ou la procédure stockée retourne une erreur.  
  
 La procédure stockée **sysmail_add_profile_sp** se trouve dans la base de données **msdb** et appartient au schéma **dbo** . La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution pour cette procédure sont octroyées par défaut aux membres du rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 **A. Création d'un profil**  
  
 L'exemple ci-dessous crée un profil de messagerie de base de données nommé `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.' ;  
```  
  
 **B. Création d'un profil et enregistrement de son ID dans une variable**  
  
 L'exemple ci-dessous crée un profil de messagerie de base de données nommé `AdventureWorks Administrator`. L'exemple stocke l'ID du profil dans la variable `@profileId` et retourne un jeu de résultats contenant l'ID du nouveau profil.  
  
```  
DECLARE @profileId INT ;  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.',  
       @profile_id = @profileId OUTPUT ;  
  
SELECT @profileId ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Créer un compte Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Objets de configuration Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
