---
title: Destination ADO NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.f1
helpviewer_keywords:
- destinations [Integration Services], ADO.NET
- ADO.NET destination
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c6126a352377e988c08a11211d12bb8bc77e93f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70153971"
---
# <a name="ado-net-destination"></a>Destination ADO NET
  La destination ADO NET charge des données dans différentes bases de données compatibles [!INCLUDE[vstecado](../../includes/vstecado-md.md)]qui utilisent une table ou une vue de base de données. Vous pouvez charger ces données dans une table ou une vue existante ou créer une table et y charger les données.  
  
 Vous pouvez utiliser la destination ADO NET pour vous connecter [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]à. La connexion à [!INCLUDE[ssSDS](../../includes/sssds-md.md)] via OLE DB n'est pas prise en charge. Pour plus d’informations sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)], consultez [Recommandations générales et limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).  
  
## <a name="troubleshooting-the-ado-net-destination"></a>Résolution des problèmes liés à la destination ADO NET  
 Vous pouvez consigner les appels que la destination ADO NET effectue auprès de fournisseurs de données externes. Cette fonctionnalité de journalisation permet de résoudre des problèmes liés à l'enregistrement de données vers des sources de données externes que réalise la destination ADO NET. Pour consigner les appels aux fournisseurs de données externes effectués par la destination ADO.NET, activez la journalisation du package et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="configuring-the-ado-net-destination"></a>Configuration de la destination ADO NET  
 Cette destination utilise un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] pour se connecter à une source de données. Il indique quel fournisseur [!INCLUDE[vstecado](../../includes/vstecado-md.md)] utiliser. Pour plus d’informations, consultez [Gestionnaire de connexions ADO.NET](../connection-manager/ado-net-connection-manager.md).  
  
 Une destination ADO NET inclut des mappages entre les colonnes d'entrée et les colonnes de la source de données de destination. Vous n'avez pas besoin de mapper les colonnes d'entrée à toutes les colonnes de destination. Toutefois, les propriétés de certaines colonnes de destination peuvent requérir le mappage de colonnes d'entrée. Sinon, des erreurs peuvent se produire. Par exemple, si une colonne de destination n'autorise pas les valeurs Null, vous devez mapper une colonne d'entrée à cette colonne. Par ailleurs, les types de données des colonnes mappées doivent être compatibles. Par exemple, vous ne pouvez pas mapper une colonne d’entrée avec un type de données chaîne à une colonne de destination avec un type de données numérique si le fournisseur [!INCLUDE[vstecado](../../includes/vstecado-md.md)] ne prend pas en charge ce mappage.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge l’insertion de texte dans les colonnes dont le type de données est défini sur image. Pour plus d’informations sur les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
> [!NOTE]  
>  La destination ADO NET ne prend pas en charge le mappage d'une colonne d'entrée dont le type a la valeur DT_DBTIME avec une colonne de base de données dont le type a la valeur datetime. Pour plus d’informations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur les types de données, consultez [Integration Services types de données](integration-services-data-types.md).  
  
 La destination ADO NET comporte une entrée standard et une sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de destination ADO.NET** , cliquez sur une des rubriques suivantes :  
  
-   [Éditeur de destination ADO NET &#40;page Gestionnaire de connexions&#41;](../ado-net-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination ADO NET &#40;page Mappages&#41;](../ado-net-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination ADO NET &#40;page sortie d’erreur&#41;](../ado-net-destination-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées ADO NET](ado-net-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir les propriétés, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
  
