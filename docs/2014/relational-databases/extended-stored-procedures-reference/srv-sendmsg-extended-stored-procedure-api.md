---
title: srv_sendmsg (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendmsg
ms.assetid: efcb50b9-f8ff-4121-bf67-05830171b928
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 12a7ae2db2d0e1c91e85eeb4a2c2691579c2da70
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62745550"
---
# <a name="srv_sendmsg-extended-stored-procedure-api"></a>srv_sendmsg (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Envoie un message au client.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_sendmsg (  
SRV_PROC *  
srvproc  
,  
int  
msgtype  
,  
DBINT  
msgnum  
,  
DBTINYINT  
class  
,   
DBTINYINT  
state  
,  
DBCHAR *  
rpcname  
,  
int   
rpcnamelen  
,  
DBUSMALLINT  
linenum  
,  
DBCHAR *  
message  
,  
int  
msglen   
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu la demande de langue). La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *msgType*  
 SRV_MSG_INFO ou SRV_MSG_ERROR, selon que le serveur envoie un message d'information ou un message d'erreur.  
  
 *msgnum*  
 Numéro de message à 4 octets.  
  
 *type*  
 Spécifie la gravité de l'erreur. Une gravité inférieure ou égale à 10 est considérée comme un message d'information.  
  
 *Département*  
 Fournit le numéro d'état de l'erreur pour le message actuel. Le numéro d'état de l'erreur fournit des informations sur le contexte de l'erreur. Les numéros d'état valides sont compris entre 0 et 255.  
  
 *rpcname*  
 N’est pas pris en charge.  
  
 *rpcnamelen*  
 N’est pas pris en charge.  
  
 *lineNum*  
 Numéro de ligne dans le lot de commandes du langage auquel le message s'applique. La numérotation des lignes débute à 1. Si *linenum* ne s’applique pas au message, définissez cette valeur sur 0.  
  
 *Message*  
 Pointeur vers la chaîne de caractères à envoyer au client.  
  
 *argument msglen*  
 Spécifie la longueur, en octets, de *message*. Si *message* se termine par le caractère NULL, définissez *msglen* sur SRV_NULLTERM.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL  
  
## <a name="remarks"></a>Notes  
 Cette fonction envoie des messages d'erreur ou d'information au client. Elle est appelée une fois pour chaque message à envoyer.  
  
 Les messages peuvent être envoyés au client avec **srv_sendmsg** dans n’importe quel ordre avant ou après que toutes les lignes (le cas échéant) ont été envoyées avec **srv_sendrow**. Tous les messages, s’il en existe, doivent être envoyés au client avant que l’état d’achèvement soit envoyé avec **srv_senddone**.  
  
 Pour envoyer des messages en Unicode, utilisez **srv_wsendmsg** à la place de **srv_sendmsg**.  
  
 Pour plus d’informations [, consultez données Unicode et pages de codes du serveur](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
