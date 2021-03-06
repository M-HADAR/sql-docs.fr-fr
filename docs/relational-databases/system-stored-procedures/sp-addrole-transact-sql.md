---
title: sp_addrole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addrole
- sp_addrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrole
ms.assetid: e8a21642-8440-419a-8585-93d3d9d44f00
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1711ec3941a5fced5ef9e0c32808d6153b673e2b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030923"
---
# <a name="sp_addrole-transact-sql"></a>sp_addrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un rôle de base de données dans la base de données active.  
  
> [!IMPORTANT]
>  **sp_addrole** est inclus pour la compatibilité avec les versions [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures de et peut ne pas être pris en charge dans une version ultérieure. Utilisez à la place [CREATE ROLE](../../t-sql/statements/create-role-transact-sql.md) .  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addrole [ @rolename = ] 'role' [ , [ @ownername = ] 'owner' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @rolename = ] 'role'`Nom du nouveau rôle de base de données. *role* est de **type sysname**et n’a pas de valeur par défaut. le *rôle* doit être un identificateur valide (ID) et ne doit pas déjà exister dans la base de données actuelle.  
  
`[ @ownername = ] 'owner'`Propriétaire du nouveau rôle de base de données. *owner* est de **type sysname**et sa valeur par défaut est l’utilisateur actuel. le *propriétaire* doit être un rôle de base de données ou un utilisateur de base de données dans la base de données actuelle.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Les noms des rôles de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent compter de 1 à 128 caractères, y compris des lettres, des symboles et des chiffres. Les noms des rôles de base de données ne peuvent pas :\\contenir une barre oblique inverse (), avoir la valeur null ou être une chaîne vide (**' '**).  
  
 Après avoir ajouté un rôle de base de données, utilisez [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) pour ajouter des principaux au rôle. Lorsque vous utilisez les instructions GRANT, DENY ou REVOKE pour appliquer des autorisations au rôle de base de données, les membres de ce rôle héritent de ces autorisations comme si elles avaient été appliquées directement à leur compte.  
  
> [!NOTE]  
>  Il n'est pas possible de créer de nouveaux rôles de serveurs. Les rôles ne peuvent être créés qu'au niveau de la base de données.  
  
 **sp_addrole** ne peut pas être utilisé dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation CREATE ROLE sur la base de données. Pour la création d'un schéma, exige l'autorisation CREATE SCHEMA sur la base de données. Si le *propriétaire* est spécifié en tant qu’utilisateur ou groupe, doit emprunter l’identité de cet utilisateur ou groupe. Si *owner* est spécifié en tant que Role, requiert l’autorisation ALTER sur ce rôle ou sur un membre de ce rôle. Si le propriétaire est spécifié en tant que rôle d'application, exige l'autorisation ALTER sur ce rôle d'application.  
  
## <a name="examples"></a>Exemples  
 Le code exemple suivant ajoute le nouveau rôle `Managers` à la base de données active.  
  
```  
EXEC sp_addrole 'Managers';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)  
  
  
