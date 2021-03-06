---
title: sp_replmonitorhelpmergesession (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesession_TSQL
- sp_replmonitorhelpmergesession
helpviewer_keywords:
- sp_replmonitorhelpmergesession
ms.assetid: a0400ba8-9609-4901-917e-925e119103a1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1781e22e97870e7b9c26e7de397d77600ecbe1ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771237"
---
# <a name="sp_replmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Retourne des informations sur les sessions passées d'un Agent de fusion de réplication, à raison d'une ligne par session correspondant au critère de filtrage. Cette procédure stockée, qui est utilisée pour surveiller la réplication de fusion, est exécutée sur la base de données de distribution du serveur de distribution ou sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replmonitorhelpmergesession [ [ @agent_name = ] 'agent_name' ]  
    [ , [ @hours = ] hours ]  
    [ , [ @session_type = ] session_type ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @agent_name = ] 'agent_name'`Nom de l’agent. *agent_name* est de type **nvarchar (100)** et n’a pas de valeur par défaut.  
  
`[ @hours = ] hours`Plage de temps, en heures, pendant laquelle les informations de session de l’agent historique sont retournées. *hours* est de **type int**, qui peut être l’une des plages suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|< **entre**|Retourne des informations sur les exécutions passées de l'Agent, dans la limite de 100 exécutions.|  
|**0** (par défaut)|Retourne des informations sur toutes les exécutions passées de l'Agent.|  
|> **entre**|Retourne des informations sur les exécutions de l’agent qui se sont produites au cours des dernières *heures* .|  
  
`[ @session_type = ] session_type`Filtre le jeu de résultats en fonction du résultat final de la session. *session_type* est de **type int**et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1** (par défaut)|Sessions de l'Agent se soldant par une nouvelle tentative ou par un succès.|  
|**0**|Sessions de l'Agent se soldant par un échec.|  
  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut. Ce paramètre est utilisé lors de l’exécution de **sp_replmonitorhelpmergesession** sur l’abonné.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données de publication. *publisher_db* est de **type sysname**, avec NULL comme valeur par défaut. Ce paramètre est utilisé lors de l’exécution de **sp_replmonitorhelpmergesession** sur l’abonné.  
  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, avec NULL comme valeur par défaut. Ce paramètre est utilisé lors de l’exécution de **sp_replmonitorhelpmergesession** sur l’abonné.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**Session_id**|**int**|ID de la session de travail d'Agent.|  
|**État**|**int**|État de l'exécution de l'Agent :<br /><br /> **1** = début<br /><br /> **2** = opération réussie<br /><br /> **3** = en cours<br /><br /> **4** = inactif<br /><br /> **5** = nouvelle tentative<br /><br /> **6** = échec|  
|**StartTime**|**DATETIME**|Heure de début de la session de travail de l’agent.|  
|**EndTime**|**DATETIME**|Heure de fin de la session du travail de l’agent.|  
|**Durée**|**int**|Durée cumulée de cette session de travail (en secondes)|  
|**UploadedCommands**|**int**|Nombre de commandes téléchargées (upload) pendant la session d'Agent.|  
|**DownloadedCommands**|**int**|Nombre de commandes téléchargées (download) pendant la session d'Agent.|  
|**ErrorMessages**|**int**|Nombre de messages d'erreur générés pendant la session d'Agent.|  
|**ErrorID**|**int**|ID de l'erreur qui s'est produite|  
|**PercentageDone**|**sépar**|Pourcentage estimé des modifications déjà remises dans une session active.|  
|**TimeRemaining**|**int**|Nombre estimé de secondes restantes dans une session active.|  
|**CurrentPhase**|**int**|Phase actuelle d'une session active ; ce paramètre peut prendre l'une des valeurs suivantes.<br /><br /> **1** = téléchargement<br /><br /> **2** = téléchargement|  
|**LastMessage**|**nvarchar (500)**|Dernier message journalisé par l'Agent de fusion pendant la session.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replmonitorhelpmergesession** est utilisé pour surveiller la réplication de fusion.  
  
 Lorsqu’il est exécuté sur l’abonné, **sp_replmonitorhelpmergesession** renvoie uniquement des informations sur les cinq dernières sessions agent de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle de base de données fixe **db_owner** ou **replmonitor** sur la base de données de distribution sur le serveur de distribution ou sur la base de données d’abonnement sur l’abonné peuvent exécuter **sp_replmonitorhelpmergesession**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller la réplication par programmation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
