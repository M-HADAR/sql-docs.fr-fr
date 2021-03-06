---
title: srv_wsendmsg (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_wsendmsg
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
ms.openlocfilehash: 301674b9acfd822d0049e548011633b68b249682
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68035991"
---
# <a name="srv_wsendmsg-extended-stored-procedure-api"></a>srv_wsendmsg (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Envoie un message Unicode au client.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui est le handle pour une connexion cliente particulière. La structure contient des informations que la bibliothèque d'API de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *Msgnum*  
 Numéro de message à 4 octets.  
  
 *severity*  
 Spécifie la gravité de l'erreur. Une gravité inférieure ou égale à 10 est considérée comme un message d'information ; sinon, il s'agit d'une erreur.  
  
 *Message*  
 Pointeur vers une chaîne Unicode à envoyer au client.  
  
 *argument msglen*  
 Spécifie la longueur, en caractères, de *message*.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Utilisez cette fonction pour envoyer des messages en Unicode. Cette fonction est semblable à **srv_sendmsg**, mais le message qu'elle envoie est une chaîne WCHAR et non une chaîne de type DBCHAR. Notez que la longueur de message est exprimée en caractères et non en octets, et que *msglen* ne sera jamais égal à SRV_NULLTERM.  
  
 Cette fonction retourne FAIL dans les conditions suivantes :  
  
-   L'argument *msglen* spécifié n'est pas compris dans la plage 0-32242.  
  
-   L'argument *msglen* spécifié est 0 mais le pointeur de message est NULL.  
  
-   Une erreur se produit lors de l'envoi du message d'erreur par le biais du réseau.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_sendmsg &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/srv-sendmsg-extended-stored-procedure-api.md)  
  
  
