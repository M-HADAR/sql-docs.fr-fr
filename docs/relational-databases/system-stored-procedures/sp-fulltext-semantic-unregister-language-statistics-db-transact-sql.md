---
title: sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db_TSQL
- sp_fulltext_semantic_unregister_language_statistics_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db
ms.assetid: 1426ca4a-9a76-489e-98da-8f6d13ff9732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d6952d245dfc9083c7cfa6e6d36ad991ffd24654
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72909141"
---
# <a name="sp_fulltext_semantic_unregister_language_statistics_db-transact-sql"></a>sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Annule l'inscription d'une base de données de statistiques linguistiques de sémantique existante de l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et supprime toutes les métadonnées associées.  
  
 Cette instruction ne détache pas la base de données ni ne supprime le fichier de base de données physique du système de fichiers. Après avoir annulé l'inscription de la base de données, vous pouvez la détacher et supprimer le fichier de base de données physique.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
##  <a name="Arguments"></a> Arguments  
 Cette procédure ne requiert pas d'arguments. Étant donné qu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne dispose que d'une base de données de statistiques linguistiques de sémantique, il n'est pas nécessaire d'identifier la base de données.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucun.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Lorsque l'inscription d'une base de données de statistiques linguistiques de sémantique est annulée, toutes les métadonnées associées sont également supprimées.  
  
 **sp_fulltext_semantic_unregister_language_statistics_db** effectue les étapes suivantes :  
  
1.  Vérifie qu'aucun remplissage sémantique n'est en cours pour l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Supprime toutes les métadonnées associées à la base de données de statistiques linguistiques de sémantique spécifiée.  

 Pour plus d’informations, consultez [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur la base de données Base de langages statistiques pour la recherche sémantique installée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sur une instance de, interrogez l’affichage catalogue [sys. Fulltext_semantic_language_statistics_database &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment annuler l’inscription de la base de données Base de langages statistiques pour la recherche sémantique en appelant **sp_fulltext_semantic_unregister_language_statistics_db**.  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
