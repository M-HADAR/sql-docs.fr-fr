---
title: srv_paramdata (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramdata
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramdata
ms.assetid: 3104514d-b404-47c9-b6d7-928106384874
author: rothja
ms.author: jroth
ms.openlocfilehash: 9f8a7f5ebb1b85740735c6070a784423b3258012
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064027"
---
# <a name="srv_paramdata-extended-stored-procedure-api"></a>srv_paramdata (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Retourne la valeur d'un paramètre d'appel de procédure stockée distante. Cette fonction a été remplacée par la fonction **srv_paraminfo**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void * srv_paramdata (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Arguments  
 *srvproc*  
 Pointeur vers la structure SRV_PROC qui correspond au handle d'une connexion cliente particulière (dans ce cas, le handle qui a reçu l'appel de procédure stockée distante). La structure contient des informations que la bibliothèque de procédure stockée étendue utilise pour gérer les communications et les données entre l'application et le client.  
  
 *n*  
 Numéro du paramètre. Le premier paramètre est le numéro 1.  
  
## <a name="returns"></a>Retours  
 Pointeur vers la valeur de paramètre. Si le *n*ième paramètre est NULL, qu’il n’y a pas de *n*ième paramètre ou qu’il n’y a aucune procédure stockée distante, la valeur NULL est retournée. Si la valeur de paramètre est une chaîne, elle peut ne pas se terminer par le caractère NULL. Utilisez **srv_paramlen** pour déterminer la longueur de la chaîne.  
  
 Cette fonction retourne les valeurs suivantes, si le paramètre est l’un des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données. Les données du pointeur indiquent si le pointeur pour le type de données est valide (VP), NULL ou non applicable (N/A), et le contenu des données désignées par le pointeur.  
  
|Nouveaux types de données|Longueur de données d'entrée|  
|--------------------|-----------------------|  
|BITN|**Null :** VP, NULL<br /><br /> **Zéro :** VP, NULL<br /><br /> **>= 255 :** NON APPLICABLE<br /><br /> **<255 :** NON APPLICABLE|  
|BIGVARCHAR|**Null :** NULL, N/A<br /><br /> **Zéro :** VP, NULL<br /><br /> **>= 255 :** VP, 255 caractères<br /><br /> **<255 :** VP, données réelles|  
|BIGCHAR|**Null :** NULL, N/A<br /><br /> **Zéro :** VP, 255 espaces<br /><br /> **>= 255 :** VP, 255 caractères<br /><br /> **<255 :** VP, données réelles + remplissage (jusqu’à 255)|  
|BIGBINARY|**Null :** NULL, N/A<br /><br /> **Zéro :** VP, 255 0x00<br /><br /> **>= 255 :** VP, 255 octets<br /><br /> **<255 :** VP, données réelles + remplissage (jusqu’à 255)|  
|BIGVARBINARY|**Null :** NULL, N/A<br /><br /> **Zéro :** VP, 0x00<br /><br /> **>= 255 :** VP, 255 octets<br /><br /> **<255 :** VP, données réelles|  
|NCHAR|**Null :** NULL, N/A<br /><br /> **Zéro :** VP, 255 espaces<br /><br /> **>= 255 :** VP, 255 caractères<br /><br /> **<255 :** VP, données réelles + remplissage (jusqu’à 255)|  
|NVARCHAR|**Null :** NULL, N/A<br /><br /> **Zéro :** VP, NULL<br /><br /> **>= 255 :** VP, 255 caractères<br /><br /> **<255 :** VP, données réelles|  
|NTEXT|**Null :** NON APPLICABLE<br /><br /> **Zéro :** NON APPLICABLE<br /><br /> **>= 255 :** NON APPLICABLE<br /><br /> ** \<255 :** NON APPLICABLE|  
  
 
  \*   Les données ne se terminent pas par le caractère NULL ; aucun avertissement n’est émis en cas de troncation de données >255 caractères.  
  
## <a name="remarks"></a>Notes  
 Si vous connaissez le nom du paramètre, vous pouvez utiliser **srv_paramnumber** pour obtenir le numéro du paramètre. Pour déterminer si un paramètre est NULL, utilisez **srv_paramlen**.  
  
 Lorsqu'un appel de procédure stockée distante est effectué avec des paramètres, ceux-ci peuvent être passés par nom ou par position (sans nom). Si l'appel de procédure stockée distante est effectué avec certains paramètres passés par nom et certains passés par position, une erreur se produit. Si une erreur se produit, le gestionnaire de SRV_RPC est toujours appelé, mais il apparaît comme s’il n’y avait aucun paramètre et **srv_rpcparams** retourne 0.  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Voir aussi  
 [srv_rpcparams &#40;API de procédure stockée étendue&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
