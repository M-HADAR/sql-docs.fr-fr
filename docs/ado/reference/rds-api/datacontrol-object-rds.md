---
title: DataControl, objet (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl
- RDS.DataControl
helpviewer_keywords:
- DataControl object [ADO]
ms.assetid: d85ea4fc-451c-436e-97b8-58f92b149dd0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a571e93a070c3ce07fbaf40a86b762c749042ec1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964406"
---
# <a name="datacontrol-object-rds"></a>DataControl, objet (RDS)
Lie un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) de requêtes de données à un ou plusieurs contrôles (par exemple, une zone de texte, un contrôle de grille ou une zone de liste déroulante) pour afficher les données du **Recordset** sur une page Web.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="https://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
</OBJECT>  
```  
  
## <a name="remarks"></a>Notes  
 ID de classe pour le **RDS. **L’objet DataControl est BD96C556-65A3-11D0-983A-00C04FC29E33.  
  
> [!NOTE]
>  Si vous recevez une erreur indiquant qu’un [objet RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) ou **RDS. **L’objet DataControl ne se charge pas, assurez-vous que vous utilisez l’ID de classe correct. Les ID de classe de ces objets ont été modifiés par rapport à la version 1,0 et 1,1. Sachez également que même les colonnes Nullable doivent être définies lorsque vous utilisez l’objet **RDS DataControl** .  
  
 Pour un scénario de base, vous devez définir uniquement les propriétés **SQL**, **Connect**et **Server** de l' **objet RDS. DataControl** , qui appellera automatiquement l’objet métier par défaut, [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md).  
  
 Toutes les propriétés de l' **objet RDS. DataControl** est facultatif, car les objets métier personnalisés peuvent remplacer leurs fonctionnalités.  
  
> [!NOTE]
>  Si vous interrogez plusieurs résultats, seul le premier [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est retourné. Si plusieurs jeux de résultats sont nécessaires, assignez-les à son propre **DataControl**. Voici un exemple de requête pour plusieurs résultats :`"Select * from Authors, Select * from Topics"`  
  
 Ajout de « DFMode = 20 ; » à votre chaîne de connexion lorsque vous utilisez les **services Bureau à distance. DataControl** peut améliorer les performances de votre serveur lorsque vous mettez à jour des données. Avec ce paramètre, l’objet **RDSServer. DataFactory** sur le serveur utilise un mode moins gourmand en ressources. Toutefois, les fonctionnalités suivantes ne sont pas disponibles dans cette configuration :  
  
-   Utilisation de requêtes paramétrables.  
  
-   Obtention des informations sur les paramètres ou les colonnes avant d’appeler la méthode **Execute** .  
  
-   Affectation de la **valeur true**à l' **instruction Transact updates** .  
  
-   Obtention de l’état de la ligne.  
  
-   Appel de la méthode [Resync](../../../ado/reference/ado-api/resync-method.md) .  
  
-   Actualisation (explicitement ou automatiquement) via la propriété [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) .  
  
-   Définition des propriétés de la **commande** ou du [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) .  
  
-   Utilisation de **adCmdTableDirect**.  
  
 **RDS. **L’objet DataControl s’exécute en mode asynchrone par défaut. Si vous avez besoin d’une exécution synchrone pour votre application, affectez au paramètre [ExecuteOptions](../../../ado/reference/rds-api/executeoptions-property-rds.md) la valeur **adcExecSync** et au paramètre [FetchOptions](../../../ado/reference/rds-api/fetchoptions-property-rds.md) la valeur **adcFetchUpFront**, comme indiqué dans l’exemple suivant.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"   
    ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="https://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
   <PARAM NAME="ExecuteOptions" VALUE="1">   <PARAM NAME="FetchOptions" VALUE="1">  
</OBJECT>  
```  
  
 Utilisez un **RDS. DataControl** pour lier les résultats d’une requête unique à un ou plusieurs contrôles visuels. Par exemple, supposons que vous codez une requête demandant des données client, telles que le nom, le séjour, le lieu de naissance, l’âge et la priorité du client. Vous pouvez utiliser un seul **objet RDS. DataControl** pour afficher le nom, l’âge et la région d’un client dans trois zones de texte distinctes ; État du client prioritaire dans une case à cocher ; et toutes les données dans un contrôle de grille.  
  
 Utilisez des **RDS différents. DataControl** pour lier les résultats de plusieurs requêtes à différents contrôles visuels. Supposons, par exemple, que vous utilisez une requête pour obtenir des informations sur un client, et une deuxième requête pour obtenir des informations sur les articles achetés par le client. Vous souhaitez afficher les résultats de la première requête dans trois zones de texte et une case à cocher, ainsi que les résultats de la deuxième requête dans un contrôle Grid. Si vous utilisez l’objet métier par défaut (**RDSServer. DataFactory**), vous devez effectuer les opérations suivantes :  
  
-   Ajoutez deux **RDS. DataControl** à votre page Web.  
  
-   Écrivez deux requêtes, une pour chaque propriété **SQL** des deux **RDS. Objets DataControl** . Un **RDS. DataControl** contient une requête SQL qui demande des informations sur le client ; le deuxième contient une requête qui demande une liste de marchandises achetées par le client.  
  
-   Dans les balises d’objet de chaque contrôle lié, spécifiez la valeur DATAFLD pour définir les valeurs des données que vous souhaitez afficher dans chaque contrôle visuel.  
  
 Il n’existe aucune restriction de nombre sur le nombre de **RDS. **Les objets DataControl que vous pouvez incorporer à l’aide de balises d’objet sur une page Web unique.  
  
 Lorsque vous définissez le **RDS. DataControl** sur une page Web, utilisez des valeurs de **hauteur** et de **largeur** non nulles telles que 1 (pour éviter l’inclusion d’espace supplémentaire).  
  
 Les composants du client Remote Data Service sont déjà inclus dans le cadre d’Internet Explorer 4,0 ; par conséquent, vous n’avez pas besoin d’inclure un paramètre CODEBASE dans votre **objet RDS. **Balise d’objet DataControl.  
  
 Avec Internet Explorer 4,0 ou une version ultérieure, vous pouvez lier des données à l’aide de contrôles HTML et de contrôles® ActiveX uniquement s’ils sont marqués comme des contrôles de modèle Apartment.  
  
> [!NOTE]
>  **Utilisateurs Microsoft Visual Basic** **RDS. DataControl** est sécurisé pour l’écriture de scripts et est utilisé uniquement dans les applications Web. Une application cliente Visual Basic n’a pas besoin de cette application.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DataControl, exemple d’objet (VBScript)](../../../ado/reference/rds-api/datacontrol-object-example-vbscript.md)






















