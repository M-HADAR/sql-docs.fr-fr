---
title: Méthode SetDefaults (ServerSettings)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: 76e4cfab-4b15-4da4-bb2f-8aac6f927f79
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86e15376bd56a439e0763e79a5c166d7023125ea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660272"
---
# <a name="setdefaults-method-serversettings-class"></a>Méthode SetDefaults (classe ServerSettings)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Définit toutes les valeurs par défaut de l’instance [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de avec l’option permettant de remplacer les données existantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Éléments  
 *dessin*  
 Objet de [classe ServerSettings](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md) qui représente une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance de client.  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*OverwriteAll*|Valeur booléenne qui spécifie s’il faut remplacer les valeurs existantes sur l’instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]de : **true** pour remplacer les données existantes, ou **false** si les données existantes ne doivent pas être remplacées.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur u**Int32** qui correspond à 0 si le service a été correctement modifié, égale à 1 si la demande n’est pas prise en charge, et à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
