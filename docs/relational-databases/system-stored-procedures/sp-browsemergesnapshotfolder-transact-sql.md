---
title: sp_browsemergesnapshotfolder (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsemergesnapshotfolder
- sp_browsemergesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsemergesnapshotfolder
ms.assetid: e248642f-5fea-4ed7-be1a-36ff75abcfde
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92df93d1c14b10aa6587d0eaf13f4de81bc4d7f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046010"
---
# <a name="sp_browsemergesnapshotfolder-transact-sql"></a>sp_browsemergesnapshotfolder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le chemin d'accès complet du dernier instantané généré pour une publication de fusion. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_browsemergesnapshotfolder [@publication= ] 'publication'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar (2000)**|Chemin d'accès complet du répertoire de l'instantané.|  
  
## <a name="remarks"></a>Notes  
 **sp_browsemergesnapshotfolder** est utilisé dans la réplication de fusion.  
  
 Si la publication est configurée pour que les fichiers d'instantané soient à la fois générés dans le répertoire de travail du serveur de publication et dans le dossier d'instantanés du serveur de publication, le jeu de résultats contient deux lignes : la première contient le dossier d'instantanés de la publication, la seconde le répertoire de travail du serveur de publication.  
  
 **sp_browsemergesnapshotfolder** est utile pour déterminer le répertoire dans lequel les fichiers d’instantanés de fusion sont générés. Ce dossier/chemin et son contenu peuvent alors être copiés sur un support amovible, et l'instantané peut être utilisé pour synchroniser un abonnement à partir d'un emplacement d'instantané secondaire.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_browsemergesnapshotfolder**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
