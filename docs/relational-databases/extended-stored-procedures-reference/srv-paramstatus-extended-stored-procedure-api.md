---
title: srv_paramstatus (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramstatus
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
author: rothja
ms.author: jroth
ms.openlocfilehash: 9898dbde804b0c4615a5dc4ad6b8fefa79000ccb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005575"
---
# <a name="srv_paramstatus-extended-stored-procedure-api"></a>srv_paramstatus (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Retourne l'état d'un paramètre d'appel d'une procédure stockée distante particulière.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui correspond au handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu l'appel de procédure stockée distante). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *n*  
 Indique le numéro du paramètre. Le premier paramètre est le numéro 1.  
  
## <a name="returns"></a>Retours  
 Un **int** qui contient les indicateurs d’état du paramètre. Actuellement, il existe un seul indicateur: Si le bit 0 est défini sur 1, le paramètre est un paramètre de retour. En l’absence du *n*ième paramètre ou d’une procédure stockée distante, la valeur -1 est retournée.  
  
## <a name="remarks"></a>Notes  
 Cette routine retourne les indicateurs d'état pour un paramètre d'appel d'une procédure stockée distante.  
  
 Les paramètres contiennent les données passées entre les clients et l'application avec des procédures stockées distantes. Le client peut spécifier certains paramètres en tant que paramètres de retour. Ces paramètres de retour peuvent contenir des valeurs que l'application transmet au client.  
  
 Actuellement, le seul indicateur d'état est celui qui indique si le paramètre est un paramètre de retour.  
  
 Quand un appel de procédure stockée distante est effectué avec des paramètres, ceux-ci peuvent être passés par nom ou par position (sans nom). Si l'appel de procédure stockée distante est effectué avec certains paramètres passés par nom et certains passés par position, une erreur se produit. Si une erreur se produit, le gestionnaire SRV_RPC est tout de même appelé, mais il apparaît comme s’il n’y avait aucun paramètre, et **srv_rpcparams** retourne 0.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_rpcparams &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
