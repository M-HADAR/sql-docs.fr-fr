---
title: RPC:Completed, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- RPC:Completed event class
ms.assetid: 0d526201-94c9-4e4c-afb1-4213df1815ba
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c4b427047aeba970ad65a6bd2ac31a219978ea71
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046764"
---
# <a name="rpccompleted-event-class"></a>RPC:Completed (classe d'événements)
  La classe d'événements RPC:Completed indique qu'un appel de procédure distante a été réglé.  
  
## <a name="rpccompleted-event-class-data-columns"></a>Colonnes de données de la classe d'événements RPC:Completed  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|BinaryData|`image`|Valeur binaire dépendante de la classe d'événements capturés dans la trace.|2|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|UC|`int`|Temps processeur utilisé par l'événement. En microsecondes à partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. En millisecondes dans les versions antérieures.|18|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l’instruction USE *Database* ou la base de données par défaut si aucune instruction USE *Database* n’a été émise pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|nom_base_de_données|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|Duration|`bigint`|Temps pris par l'événement. En microsecondes à partir de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. En millisecondes dans les versions antérieures.|13|Oui|  
|EndTime|`datetime`|Heure de fin de l'appel de procédure distante.|15|Oui|  
|Error|`int`|Numéro d'erreur d'un événement donné.<br /><br /> 0=OK<br /><br /> 1=Erreur<br /><br /> 2=Abandon<br /><br /> 3=Ignoré|31|Oui|  
|EventClass|`int`|Type d'événement = 10.|27|Non|  
|EventSequence|`int`|Séquence d'un événement donné au sein de la demande.|51|Non|  
|GroupID|`int`|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|LoginName|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|LoginSid|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom d'utilisateur Windows.|6|Oui|  
|ObjectName|`nvarchar`|Nom de l'objet référencé.|34|Oui|  
|Lectures|`bigint`|Nombre de lectures de page émises par l'appel de procédure distante.|16|Oui|  
|RequestID|`int`|ID de la demande contenant l'instruction.|49|Oui|  
|RowCounts|`bigint`|Nombre de lignes dans le traitement RPC.|48|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26||  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`ntext`|Texte de l’appel de procédure distante|1|Oui|  
|TransactionID|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
|Écritures|`bigint`|Nombre d'écritures de page émises par l'appel de procédure distante.|17|Oui|  
|XactSequence|`bigint`|Jeton qui décrit la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
