---
title: Configurer la base de données et le site Web pour Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 478dea9095fe22a437aecf138c22374b5a70885b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054103"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>Configurer la base de données et le site web de Master Data Services
  Utilisez le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] pour configurer la base de données et le site web pour [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)  
  
 Pour configurer la base de données et le site web, effectuez les tâches suivantes :  
  
1.  Créez une base de données à l’aide de [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]la page **configuration de la base de données** dans.  
  
     Pour plus d’informations, consultez [page Configuration de la base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) et [Assistant Création de base de données &#40;gestionnaire de configuration Master Data Services&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  Créez un site Web, sélectionnez le site Web par défaut ou sélectionnez un autre site Web existant, à l’aide [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]de la page **configuration Web** dans. Associez ensuite la base de données MDS à l'application web sélectionnée ou créée.  
  
     Pour plus d’informations, consultez [page Configuration Web &#40;Gestionnaire de configuration Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) et [boîte de dialogue créer un site web &#40;gestionnaire de configuration Master Data Services&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  Facultatif Activez l’intégration avec Data Quality Services à l’aide de la [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]page de **configuration Web** dans.  
  
     Pour plus d’informations, consultez [page de configuration Web &#40;Gestionnaire de configuration Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) et [activer l’intégration de Data Quality Services avec Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 Vous pouvez utiliser [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] pour spécifier des paramètres pour les applications et services web associés à la base de données MDS. Par exemple, vous pouvez spécifier la fréquence à laquelle les données sont chargées ou des e-mails de validation envoyés. Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données Master Data Services](../../2014/master-data-services/master-data-services-database.md)   
 [Application Web Master Data Manager](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
