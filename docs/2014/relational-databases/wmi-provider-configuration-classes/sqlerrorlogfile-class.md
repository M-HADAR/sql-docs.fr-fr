---
title: SqlErrorLogFile, classe | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 8c5c6f1998cffc268a57318e0124f74d3411a3b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63249315"
---
# <a name="sqlerrorlogfile-class"></a>Classe SqlErrorLogFile
  Fournit des propriétés pour l'affichage des informations relatives à un fichier journal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a>Propriétés  
 La classe SQLErrorLogFile définit les propriétés suivantes.  
  
|||  
|-|-|  
|ArchiveNumber|Type de données : `uint32`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Numéro d'archive pour le fichier journal.|  
|InstanceName|Type de données : `string`<br /><br /> Type d'accès : Lecture seule<br /><br /> Qualificateurs : Clé<br /><br /> <br /><br /> Nom de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où le fichier journal réside.|  
|LastModified|Type de données : `datetime`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Date de la dernière modification du fichier journal.|  
|LogFileSize|Type de données : `uint32`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Taille du fichier journal, en octets.|  
|Name|Type de données : `string`<br /><br /> Type d'accès : Lecture seule<br /><br /> Qualificateurs : Clé<br /><br /> <br /><br /> Nom du fichier journal.|  
  
## <a name="remarks"></a>Notes  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Espace de noms|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant extrait les informations relatives à tous les fichiers journaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur une instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour exécuter l’exemple, remplacez \< *Instance_Name*> par le nom de l’instance, par exemple, « Instance1 ».  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a>Commentaires  
 Lorsque *InstanceName* n’est pas fourni dans l’instruction WQL, la requête retourne des informations pour l’instance par défaut. Par exemple, l'instruction WQL suivante retournera les informations relatives à tous les fichiers journaux de l'instance par défaut (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>Sécurité  
 Pour vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un fichier journal via WMI, vous devez disposer des autorisations suivantes sur les ordinateurs locaux et distants :  
  
-   Accès en lecture à l’espace de noms WMI **Root\Microsoft\SqlServer\ComputerManagement10** . Par défaut, tout le monde dispose de l'accès en lecture via l'autorisation Activer le compte.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur la vérification des autorisations WMI, consultez la section sécurité de la rubrique [afficher les fichiers journaux hors connexion](../logs/view-offline-log-files.md).  
  
-   Autorisation en lecture sur le dossier qui contient les journaux des erreurs. Par défaut, les journaux des erreurs se trouvent dans le chemin d’accès suivant (où \< *lecteur>* représente le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lecteur \<sur lequel vous avez installé et *InstanceName*> est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]le nom de l’instance de) :  
  
     **> de lecteur : \Program Files\Microsoft SQL Server\MSSQL11. \<** **\< Nom_instance> \MSSQL\Log**  
  
 Si vous vous connectez via un pare-feu, vérifiez qu'une exception est définie dans le pare-feu pour WMI sur les ordinateurs cibles distants. Pour plus d’informations, consultez [connexion à WMI à distance à partir de Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Voir aussi  
 [SqlErrorLogEvent, classe](sqlerrorlogevent-class.md)   
 [Afficher les fichiers journaux hors connexion](../logs/view-offline-log-files.md)  
  
  
