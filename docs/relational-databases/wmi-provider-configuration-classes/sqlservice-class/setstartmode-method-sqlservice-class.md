---
title: Méthode setStartMode, (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetStartMode Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: edd3b4a5fa4d787292f1978da80c5f7803242010
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660910"
---
# <a name="setstartmode-method-sqlservice-class"></a>Méthode SetStartMode (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Modifie le mode de démarrage de l'instance de service.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.SetStartMode(StartMode)  
```  
  
## <a name="parts"></a>Éléments  
 *dessin*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
#### <a name="parameters"></a>Paramètres  
 *StartMode*  
 Valeur **uint32** qui spécifie le mode de démarrage de l'instance de service.  
  
 Les valeurs valides sont les suivantes :  
  
 Valeur = 0. Boot - Le pilote de périphérique est démarré par le chargeur du système d'exploitation. Cette valeur est uniquement valide pour les services de pilote.  
  
 Valeur = 1. System - Le pilote de périphérique est démarré par la méthode **IoInitSystem** . Cette valeur est uniquement valide pour les services de pilote.  
  
 Valeur = 2 Automatic - Le service doit être démarré automatiquement par le Gestionnaire de contrôle des services lors du démarrage du système.  
  
 Valeur = 3. Manual - Le service doit être démarré par Computer Manager lorsqu'un processus appelle la méthode **StartService** .  
  
 Valeur = 4 Disabled - Le service ne peut pas être démarré.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** égale à 0 si le service a été correctement modifié ou égale à 1 si la demande n'est pas prise en charge. Tout autre nombre indique une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
