---
title: sp_revokelogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 95598885a80b1f697f5e1287e22c1048e737ba6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67944722"
---
# <a name="sp_revokelogin-transact-sql"></a>sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime les entrées de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de pour un utilisateur ou un groupe Windows créé à l’aide de Create login, **sp_grantlogin**ou **sp_denylogin**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez à la place [Drop login](../../t-sql/statements/drop-login-transact-sql.md) .  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @loginame = ] 'login'`Nom de l’utilisateur ou du groupe Windows. *login* est de **type sysname**, sans valeur par défaut. la *connexion* peut être n’importe quel nom d’utilisateur ou groupe Windows existant sous la forme *nom*\\de l’ordinateur*utilisateur ou domaine*\\*utilisateur*.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_revokelogin** désactive les connexions à l’aide du compte spécifié par le paramètre de *connexion* . Cependant, les utilisateurs Windows qui ont l'autorisation d'accéder à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par l'intermédiaire de leur appartenance à un groupe Windows peuvent néanmoins se connecter par le groupe une fois leur accès individuel supprimé. De même, si le paramètre de *connexion* spécifie le nom d’un groupe Windows, les membres de ce groupe qui ont été disposant d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accès distinct à l’instance de pourront toujours se connecter.  
  
 Par exemple, si l’utilisateur Windows **ADVWORKS\john** est membre du groupe Windows **ADVWORKS\Admins**, et **sp_revokelogin** révoque l’accès de `ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 L’utilisateur **ADVWORKS\john** peut toujours se connecter si **ADVWORKS\Admins** a reçu l’autorisation d’accéder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]à une instance de. De même, si l’accès a été révoqué à **ADVWORKS\Admins** du groupe Windows et que **ADVWORKS\john** est autorisé, **ADVWORKS\john** peut toujours se connecter.  
  
 Utilisez **sp_denylogin** pour empêcher explicitement les utilisateurs de se connecter à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]instance de, quelle que soit leur appartenance à un groupe Windows.  
  
 **sp_revokelogin** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER ANY LOGIN sur le serveur.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime les entrées de connexion de l’utilisateur `Corporate\MollyA`Windows.  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 ou  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
