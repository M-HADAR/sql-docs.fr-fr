---
title: Connexion à SQL Server (DB2eToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b59803cb-3cc6-41cc-8553-faf90851410e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7ab4c1f691820fb19dde7a3e3166abc2ff065b18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68126637"
---
# <a name="connecting-to-sql-server-db2etosql"></a>Connexion à SQL Server (DB2eToSQL)
Pour migrer des bases de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vers 2012, 2014 ou Azure SQL dB, vous devez vous connecter à l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]une de ces instances cibles de. Quand vous vous connectez, SSMA obtient les métadonnées relatives à toutes les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’instance de et affiche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les métadonnées de la base de données dans l’Explorateur de métadonnées. SSMA stocke des informations sur l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de à laquelle vous êtes connecté, mais ne stocke pas les mots de passe.  
  
Votre connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reste active jusqu’à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu’à ce que vous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chargeant des objets de base de données dans et migriez les données.  
  
Les métadonnées relatives à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’instance de ne sont pas synchronisées automatiquement. Au lieu de cela, pour mettre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à jour les métadonnées dans l’Explorateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de métadonnées, vous devez mettre à jour manuellement les métadonnées. Pour plus d’informations, consultez la section [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « synchronisation des métadonnées » plus loin dans cette rubrique.  
  
## <a name="required-sql-server-permissions"></a>Autorisations de SQL Server requises  
Le compte utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert des autorisations différentes en fonction des actions effectuées par le compte :  
  
-   Pour convertir des objets DB2 [!INCLUDE[tsql](../../includes/tsql-md.md)] en syntaxe, pour mettre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]jour des métadonnées à partir de ou pour enregistrer la syntaxe convertie dans des scripts, le compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]doit avoir l’autorisation de se connecter à l’instance de.  
  
-   Pour charger des objets de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]base de données dans, le compte doit être membre du rôle de serveur **sysadmin** . Cela est nécessaire pour installer les assemblys CLR.  
  
-   Pour migrer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]données vers, le compte doit être membre du rôle de serveur **sysadmin** . Cela est nécessaire pour exécuter les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] packages de migration de données de l’agent.  
  
-   Pour exécuter le code généré par SSMA, le compte doit disposer des autorisations d' **exécution** pour toutes les fonctions définies par l’utilisateur dans le schéma **ssma_DB2** de la base de données cible. Ces fonctions fournissent des fonctionnalités équivalentes des fonctions système DB2 et sont utilisées par les objets convertis.  
  
Si le compte utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consiste à effectuer toutes les tâches de migration, le compte doit être membre du rôle de serveur **sysadmin** .  
  
## <a name="establishing-a-sql-server-connection"></a>Établissement d’une connexion SQL Server  
Avant de convertir des objets de base [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données DB2 en syntaxe, vous devez établir une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’instance de dans laquelle vous souhaitez migrer la ou les bases de données DB2.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données dans laquelle les objets et les données seront migrés. Vous pouvez personnaliser ce mappage au niveau du schéma DB2 après vous être connecté [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]à. Pour plus d’informations, consultez [mappage de schémas DB2 à des schémas de SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
> [!IMPORTANT]  
> Avant d’essayer de vous connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]à, assurez-vous que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’instance de est en cours d’exécution et peut accepter des connexions.  
  
**Pour se connecter à SQL Server**  
  
1.  Dans le menu **fichier** , sélectionnez **se connecter à SQL Server**.  
  
    Si vous vous êtes connecté [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]précédemment à, le nom de la commande sera **reconnecté à SQL Server**.  
  
2.  Dans la boîte de dialogue connexion, entrez ou sélectionnez le nom de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de.  
  
    -   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer **localhost** ou un point (**.**).  
  
    -   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
    -   Si vous vous connectez à une instance nommée sur un autre ordinateur, entrez le nom de l’ordinateur suivi d’une barre oblique inverse, puis du nom de l’instance, par exemple MyServer\MyInstance.  
  
3.  Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configurée pour accepter les connexions sur un port autre que celui par défaut, entrez le numéro de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] port utilisé pour les connexions dans la zone **port du serveur** . Pour l’instance par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de, le numéro de port par défaut est 1433. Pour les instances nommées, SSMA essaiera d’obtenir le numéro de port [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auprès du service Browser.  
  
4.  Dans la zone **base de données** , entrez le nom de la base de données cible.  
  
    Cette option n’est pas disponible lorsque vous vous reconnectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Dans la zone **authentification** , sélectionnez le type d’authentification à utiliser pour la connexion. Pour utiliser le compte Windows actuel, sélectionnez **authentification Windows**. Pour utiliser une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion, sélectionnez **SQL Server l’authentification**, puis indiquez le nom de connexion et le mot de passe.  
  
6.  Pour une connexion sécurisée, deux contrôles sont ajoutés, les cases à cocher **chiffrer la connexion** et **TrustServerCertificate** . La case à cocher **TrustServerCertificate** est visible uniquement lorsque l’option **chiffrer la connexion** est activée. Lorsque l’option **chiffrer la connexion** est activée (true) et la valeur **TrustServerCertificate** est désactivée (false), elle valide le certificat SQL Server SSL. La validation du certificat de serveur est une partie de la négociation SSL qui garantit qu'il s'agit du serveur correct avec lequel établir une connexion. Pour ce faire, un certificat doit être installé côté client et du côté serveur.  
  
7.  Cliquez sur **Connecter**.  
  
**Compatibilité des versions plus élevée**  
  
-   Vous serez en mesure de vous connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et 2014 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et 2016 quand le projet de migration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créé est 2005.  
  
-   Vous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pouvez vous connecter aux 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet de migration créé est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, mais que vous ne pouvez pas vous connecter à des versions inférieures, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par exemple, 2005.  
  
-   Vous pouvez vous connecter aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 lorsque le projet créé est SQL Server 2012.  
  
||||||  
|-|-|-|-|-|  
|**TYPE de projet et VERSION du serveur cible**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012 <br />(Version : 11. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 <br />(Version : 12. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version : 13. x)|Azure SQL DB|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012|Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014|||Oui||  
|Azure SQL DB||||Oui|  
  
> [!IMPORTANT]  
> La conversion des objets de base de données est effectuée en fonction du type de projet, mais pas de celui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la version de à laquelle vous êtes connecté. Dans le cas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , 2014 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , 2016 ou Azure SQL db.  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisation des métadonnées de SQL Server  
Les métadonnées relatives aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données ne sont pas automatiquement mises à jour. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’Explorateur de métadonnées, les métadonnées sont un instantané des métadonnées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]lors de la première connexion à, ou la dernière fois que vous avez mis à jour manuellement les métadonnées. Vous pouvez mettre à jour manuellement les métadonnées de toutes les bases de données ou d’une base de données ou d’un objet de base de données unique.  
  
**Pour synchroniser les métadonnées**  
  
1.  Assurez-vous que vous êtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]connecté à.  
  
2.  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’Explorateur de métadonnées, activez la case à cocher en regard de la base de données ou du schéma de base de données que vous souhaitez mettre à jour.  
  
    Par exemple, pour mettre à jour les métadonnées de toutes les bases de données, activez la case à cocher en regard de **bases de données**.  
  
3.  Cliquez avec le bouton droit sur **bases**de données, ou sur la base de données individuelle ou le schéma de base de données, puis sélectionnez **synchroniser avec la base de**données.  
  
## <a name="next-step"></a>étape suivante  
L’étape suivante de la migration dépend des besoins de votre projet :  
  
-   Pour personnaliser le mappage entre les schémas et les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données et schémas DB2, consultez [mappage de schémas DB2 à des schémas de SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
-   Pour personnaliser les options de configuration des projets, consultez [paramètres du projet &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md) et les sections associées.  
  
-   Pour personnaliser le mappage des types de données sources et cibles, consultez [mappage des types de données DB2 et SQL Server &#40;les&#41;DB2ToSQL ](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   Si vous n’avez pas besoin d’effectuer ces tâches, vous pouvez convertir les définitions d’objet de base de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données DB2 en définitions d’objets. Pour plus d’informations, consultez [conversion de schémas DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Migration de bases de données DB2 vers SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
