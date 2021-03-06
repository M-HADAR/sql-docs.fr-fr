---
title: sp_pdw_remove_network_credentials
titleSuffix: Azure SQL Data Warehouse
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.subservice: design
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: c12696a2-5939-402b-9866-8a837ca4c0a3
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7068beee49260db17e7b8f704e5aba316deb6ea3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73844437"
---
# <a name="sp_pdw_remove_network_credentials-sql-data-warehouse"></a>sp_pdw_remove_network_credentials (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Cela supprime les informations d’identification réseau [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] stockées dans pour accéder à un partage de fichiers réseau. Par exemple, utilisez cette procédure stockée pour supprimer l' [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] autorisation d’effectuer des opérations de sauvegarde et de restauration sur un serveur qui réside dans votre propre réseau.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique")[Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_remove_network_credentials 'target_server_name'  
```  
  
## <a name="arguments"></a>Arguments  
 '*target_server_name*'  
 Spécifie le nom d’hôte ou l’adresse IP du serveur cible. Les informations d’identification permettant d’accéder à ce serveur [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]seront supprimées de. Cela ne modifie pas ou ne supprime pas les autorisations sur le serveur cible réel qui est géré par votre propre équipe.  
  
 *target_server_name* est défini en tant que nvarchar (337).  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation **ALTER Server State** .  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Une erreur se produit si la suppression des informations d’identification échoue sur le nœud de contrôle et sur tous les nœuds de calcul.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Cette procédure stockée supprime les informations d’identification réseau du compte [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]NetworkService pour. Le compte NetworkService exécute chaque instance de SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le nœud de contrôle et les nœuds de calcul. Par exemple, lorsqu’une opération de sauvegarde s’exécute, le nœud de contrôle et chaque nœud de calcul utilisent les informations d’identification du compte NetworkService pour accéder au serveur cible.  
  
## <a name="metadata"></a>Métadonnées  
 Pour répertorier toutes les informations d’identification et vérifier que les informations d’identification ont été supprimées, utilisez [sys. dm_pdw_network_credentials &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
 Pour ajouter des informations d’identification, utilisez [sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-remove-credentials-for-performing-a-database-backup"></a>R. Supprimer les informations d’identification pour effectuer une sauvegarde de base de données  
 L’exemple suivant supprime les informations d’identification du nom d’utilisateur et du mot de passe pour accéder au serveur cible dont l’adresse IP est 10.192.147.63.  
  
```  
EXEC sp_pdw_remove_network_credentials '10.192.147.63';  
```  
  
  

