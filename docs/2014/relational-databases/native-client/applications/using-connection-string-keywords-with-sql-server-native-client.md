---
title: Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6135c1d2cbf1291465e1346f71010b8befe6f7b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046393"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client
  Certaines API [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilisent des chaînes de connexion pour spécifier des attributs de connexion. Les chaînes de connexion sont des listes de mots clés et de valeurs associées ; chaque mot clé identifie un attribut de connexion particulier.  
  
 **Veuillez noter !** 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client autorise l'ambiguïté dans les chaînes de connexion afin de maintenir la compatibilité descendante (par exemple, certains mots clés peuvent être spécifiés plusieurs fois et des mots clés en conflit peuvent être autorisés avec la résolution en fonction de la position ou de la précédence). Les versions ultérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client n'autoriseront peut-être pas l'ambiguïté dans les chaînes de connexion. Lors de la modification d'applications, il est conseillé d'utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour éliminer toute dépendance vis-à-vis de l'ambiguïté de chaîne de connexion.  
  
 Les sections suivantes décrivent les mots clés qui peuvent être utilisés avec le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et ActiveX Data Objects (ADO) lors de l'utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client comme fournisseur de données.  
  
## <a name="odbc-driver-connection-string-keywords"></a>Mots clés de chaîne de connexion du pilote ODBC  
 Les applications ODBC utilisent des chaînes de connexion comme paramètres pour les fonctions [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) et [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md) .  
  
 Les chaînes de connexion utilisées par ODBC ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre accolades, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs d'attributs contiennent des signes non alphanumériques. Il est supposé que la première accolade fermante dans la valeur termine la valeur ; par conséquent, les valeurs ne peuvent pas contenir de caractères d'accolade fermante.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec une chaîne de connexion ODBC.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|`Addr`|Synonyme de « Address ».|  
|`Address`|Adresse réseau du serveur exécutant une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. 
  `Address` est généralement le nom réseau du serveur, mais il peut s'agir d'autres noms tels qu'un canal, une adresse IP ou un port TCP/IP et une adresse de socket.<br /><br /> Si vous spécifiez une adresse IP, assurez-vous que les protocoles TCP/IP ou de canaux nommés sont activés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La valeur de `Address` est prioritaire par rapport à la valeur passée à `Server` dans les chaînes de connexion ODBC lors de l'utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Notez également que `Address=;` se connecte au serveur spécifié dans le mot clé `Server`, tandis que `Address= ;, Address=.;`, `Address=localhost;` et `Address=(local);` provoquent tous l'établissement d'une connexion au serveur local.<br /><br /> La syntaxe complète du mot clé `Address` est la suivante :<br /><br /> [*protocole*`:`] *Adresse*[`,`*port &#124; \pipe\pipename*]<br /><br /> le *protocole* peut `tcp` être (TCP/IP) `lpc` , (mémoire partagée) ou `np` (canaux nommés). Pour plus d’informations sur les protocoles, consultez [configurer des protocoles clients](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Si ni le *protocole* ni `Network` le mot clé n' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est spécifié, Native Client utilise l’ordre des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] protocoles spécifié dans Configuration Manager.<br /><br /> *port* est le port auquel se connecter, sur le serveur spécifié. Par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le port 1433.|  
|`AnsiNPW`|Lorsque la valeur « yes » est spécifiée, le pilote utilise les comportements ANSI pour gérer les comparaisons NULL, le remplissage des données caractères, les avertissements et la concaténation de NULL. Lorsque la valeur « no » est spécifiée, les comportements ANSI ne sont pas exposés. Pour plus d’informations sur les comportements ANSI NPW, consultez [effets des options ISO](../../native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|`APP`|Nom de l’application appelant [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) (facultatif). Si elle est spécifiée, cette valeur est stockée dans la colonne **Master. dbo. sysprocesses** **program_name** et est retournée par [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) et les fonctions [APP_NAME](/sql/t-sql/functions/app-name-transact-sql) .|  
|`ApplicationIntent`|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont `ReadOnly` et `ReadWrite`. Par exemple : ApplicationIntent = ReadOnly<br /><br /> Par défaut, il s’agit de `ReadWrite`. Pour plus d’informations [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur la prise en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]de Native Client pour, consultez [SQL Server Native Client la prise en charge de la haute disponibilité et de la récupération d’urgence](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`AttachDBFileName`|Nom du fichier primaire d'une base de données qui peut être attachée. Incluez le chemin d'accès complet et échappez tout caractère \ lors de l'utilisation d'une variable de chaîne de caractères C :<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Cette base de données est attachée et devient la base de données par défaut de la connexion. Pour utiliser `AttachDBFileName` , vous devez également spécifier le nom de la base de données dans le paramètre de base de données [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) ou l’attribut de connexion SQL_COPT_CURRENT_CATALOG. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas ; il utilise la base de données attachée comme valeur par défaut pour la connexion.|  
|`AutoTranslate`|Lorsque la valeur « yes » est spécifiée, les chaînes de caractères ANSI transmises entre le client et le serveur sont converties au format Unicode afin de réduire les problèmes lors de la correspondance des caractères étendus entre les pages de codes sur le client et le serveur.<br /><br /> Les données client SQL_C_CHAR envoyées à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] une variable, un paramètre ou une variable de **type char**, **varchar**ou **Text** sont converties du format caractère au format Unicode à l’aide de la page de codes ANSI du client (ACP), puis converties du format Unicode au format caractère à l’aide de l’ACP du serveur.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]les données de **type char**, **varchar**ou **Text** envoyées à une variable client SQL_C_CHAR sont converties du format caractère au format Unicode à l’aide du serveur ACP, puis converties du format Unicode au format caractère à l’aide du client ACP.<br /><br /> Ces conversions sont effectuées sur le client par le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Cela requiert que la page de codes ANSI utilisée sur le serveur soit disponible sur le client.<br /><br /> Ces paramètres n'ont aucun effet sur les conversions effectuées pour les transferts suivants :<br /><br /> -Unicode SQL_C_WCHAR données client envoyées à **char**, **varchar**ou **Text** sur le serveur.<br />-   données de serveur de **type char**, **varchar**ou **Text** envoyées à une variable de SQL_C_WCHAR Unicode sur le client.<br />-ANSI SQL_C_CHAR données client envoyées à Unicode **nchar**, **nvarchar**ou **ntext** sur le serveur.<br />-Les données de serveur **nchar**, **nvarchar**ou **ntext** Unicode envoyées à une variable SQL_C_CHAR ANSI sur le client.<br /><br /> Lorsque la valeur « no » est spécifiée, la conversion de caractère n'est pas effectuée.<br /><br /> Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client ne traduit pas le caractère ANSI du client SQL_C_CHAR les données envoyées aux variables, paramètres ou colonnes **char**, **varchar**ou **Text** sur le serveur. Aucune traduction n’est effectuée sur les données de **type char**, **varchar**ou **Text** envoyées à partir du serveur vers SQL_C_CHAR variables sur le client.<br /><br /> Si le client et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisent des pages de codes ANSI différentes, les caractères étendus peuvent être mal interprétés.|  
|`Database`|Nom de la base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par défaut utilisée pour la connexion. Si `Database` n'est pas spécifié, la base de données par défaut définie pour la connexion est utilisée. La base de données par défaut de la source de données ODBC remplace la base de données par défaut définie pour la connexion. La base de données doit être une base de données existante à moins que `AttachDBFileName` ne soit également spécifié. Si `AttachDBFileName` est également spécifié, le fichier primaire vers lequel il pointe est attaché et le nom de la base de données spécifié par `Database` lui est assigné.|  
|`Driver`|Nom du pilote tel qu’il est retourné par [SQLDrivers](../../native-client-odbc-api/sqldrivers.md). La valeur de mot clé pour le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est « {SQL Server Native Client 11.0} ». Le mot clé `Server` est requis si `Driver` est spécifié et que `DriverCompletion` a la valeur SQL_DRIVER_NOPROMPT.<br /><br /> Pour plus d’informations sur les noms des pilotes, consultez [utilisation des fichiers de bibliothèque et d’en-tête SQL Server Native Client](using-the-sql-server-native-client-header-and-library-files.md).|  
|`DSN`|Nom d'une source de données utilisateur ou système ODBC existante. Ce mot clé remplace toutes les valeurs qui peuvent être spécifiées dans les mots clés `Server`, `Network` et `Address`.|  
|`Encrypt`|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|`Fallback`|Ce mot clé est déconseillé et sa valeur est ignorée par le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`Failover_Partner`|Nom du partenaire de basculement à utiliser s'il est impossible d'établir une connexion au serveur principal.|  
|`FailoverPartnerSPN`|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le pilote.|  
|`FileDSN`|Nom d'une source de données de fichier ODBC existante.|  
|`Language`|Nom de la langue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (facultatif). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]peut stocker des messages pour plusieurs langues dans **sysmessages**. Lors de la connexion à un ordinateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec plusieurs langues, `Language` spécifie le jeu de messages utilisé pour la connexion.|  
|`MARS_Connection`|Active ou désactive MARS (Multiple Active Result Set) sur la connexion. Les valeurs reconnues sont « yes » et « no ». La valeur par défaut est « no ».|  
|`MultiSubnetFailover`|Spécifiez toujours `multiSubnetFailover=Yes` lors de la connexion à l'écouteur de groupe de disponibilité d'un groupe de disponibilité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d'une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. 
  `multiSubnetFailover=Yes` configure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour fournir une détection plus rapide du serveur actif et une connexion à celui-ci. Les valeurs possibles sont `Yes` et `No`. Par exemple :<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Par défaut, il s’agit de `No`. Pour plus d’informations [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur la prise en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]de Native Client pour, consultez [SQL Server Native Client la prise en charge de la haute disponibilité et de la récupération d’urgence](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Net`|Synonyme de « Network ».|  
|`Network`|Les valeurs valides sont **dbnmpntw** (canaux nommés) et **dbmssocn** (TCP/IP).<br /><br /> Le fait de spécifier à la fois une valeur pour le mot clé `Network` et un préfixe de protocole sur le mot clé `Server` constitue une erreur.|  
|`PWD`|Mot de passe du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] spécifié dans le paramètre UID. Il n'est pas nécessaire de spécifier `PWD` si la connexion a un mot de passe NULL ou lors de l'utilisation de l'authentification Windows (`Trusted_Connection = yes`).|  
|`QueryLog_On`|Lorsque la valeur « yes » est spécifiée, l'enregistrement des données de requêtes longues est activé sur la connexion. Lorsque la valeur « no » est spécifiée, les données de requêtes longues ne sont pas enregistrées dans le journal.|  
|`QueryLogFile`|Chemin d'accès complet et nom de fichier d'un fichier à utiliser pour l'enregistrement des données sur les requêtes longues.|  
|`QueryLogTime`|Chaîne de caractères numérique spécifiant le seuil d'enregistrement (en millisecondes) des requêtes longues. Toute requête qui n'obtient pas de réponse dans les délais spécifiées est écrite dans le fichier journal de requêtes longues.|  
|`QuotedId`|Lorsque la valeur « yes » est spécifiée, QUOTED_IDENTIFIERS est défini à ON pour la connexion, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise les règles ISO concernant l'utilisation de guillemets dans les instructions SQL. Lorsque la valeur « no » est spécifiée, QUOTED_IDENTIFIERS est défini à OFF pour la connexion. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise dans ce cas les règles [!INCLUDE[tsql](../../../includes/tsql-md.md)] héritées concernant l'utilisation de guillemets dans les instructions SQL. Pour plus d’informations, consultez [effets des options ISO](../../native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|`Regional`|Lorsque la valeur « yes » est spécifiée, le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise les paramètres du client pour convertir monnaie, date et heure en données caractères. La conversion est unidirectionnelle uniquement ; le pilote ne reconnaît pas les formats standard non-ODBC pour les chaînes de date ou les valeurs monétaires contenues par exemple dans un paramètre utilisé dans une instruction INSERT ou UPDATE. Lorsque la valeur « no » est spécifiée, le pilote utilise les chaînes standard ODBC pour représenter les données de monnaie, date et heure converties en données caractères.|  
|`SaveFile`|Nom d'un fichier source de données ODBC dans lequel les attributs de la connexion actuelle sont enregistrés si la connexion réussit.|  
|`Server`|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La valeur doit être le nom d'un serveur sur le réseau, une adresse IP ou le nom d'un alias du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Le mot clé `Address` remplace le mot clé `Server`.<br /><br /> Vous pouvez vous connecter à l’instance par défaut sur le serveur local en spécifiant l’un des éléments suivants :<br /><br /> -   `Server=;`<br />-   `Server=.;`<br />-   `Server=(local);`<br />-   `Server=(localhost);`<br />-   **Serveur = (base de\\ ** données locale) _InstanceName_`;`<br /><br /> Pour plus d’informations sur la prise en charge de la base de données locale, consultez [SQL Server Native Client Support pour](../features/sql-server-native-client-support-for-localdb.md)la base de données<br /><br /> Pour spécifier une instance nommée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ajoutez **\\** _InstanceName_.<br /><br /> Si aucun serveur n'est spécifié, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Si vous spécifiez une adresse IP, assurez-vous que les protocoles TCP/IP ou de canaux nommés sont activés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La syntaxe complète du mot clé `Server` est la suivante :<br /><br /> `Server=`[*protocole*`:`] *Serveur*[`,`*port*]<br /><br /> le *protocole* peut `tcp` être (TCP/IP) `lpc` , (mémoire partagée) ou `np` (canaux nommés).<br /><br /> Voici un exemple de spécification d'un canal nommé :<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Cette ligne spécifie le protocole de canal nommé, un canal nommé sur l'ordinateur local (`\\.\pipe`), le nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) et le nom par défaut du canal nommé (`sql/query`).<br /><br /> Si aucun *protocole* ni le `Network` mot clé n’est spécifié [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , Native Client utilise l’ordre des protocoles spécifié [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans Configuration Manager.<br /><br /> *port* est le port auquel se connecter, sur le serveur spécifié. Par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le port 1433.<br /><br /> Les espaces sont ignorés au début de la valeur passée à `Server` dans les chaînes de connexion ODBC lors de l'utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`ServerSPN`|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le pilote.|  
|`StatsLog_On`|Lorsque la valeur « yes » est spécifiée, active la capture de données de performances du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Lorsque la valeur « no » est spécifiée, les données de performances du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ne sont pas disponibles sur la connexion.|  
|`StatsLogFile`|Chemin d'accès complet et nom de fichier d'un fichier utilisé pour enregistrer les statistiques de performances du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`Trusted_Connection`|Lorsque la valeur « yes » est spécifiée, fait en sorte que le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le mode d'authentification Windows pour la validation de connexion. Autrement, fait en sorte que le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise un nom d'utilisateur et un mot de passe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour la validation de connexion, et les mots clés UID et PWD doivent être spécifiés.|  
|`TrustServerCertificate`|En cas d'utilisation avec `Encrypt`, active le chiffrement à l'aide d'un certificat de serveur auto-signé.|  
|`UID`|Compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] valide. Il n'est pas nécessaire de spécifier l'UID lors de l'utilisation de l'authentification Windows.|  
|`UseProcForPrepare`|Ce mot clé est déconseillé et son paramètre est ignoré par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client.|  
|`WSID`|ID de station de travail. En général, il s'agit du nom réseau de l'ordinateur sur lequel l'application réside (facultatif). Si elle est spécifiée, cette valeur est stockée dans le **nom d’hôte** de la colonne **Master. dbo. sysprocesses** et est retournée par [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) et la fonction [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) .|  
  
 **Les paramètres de conversion régionaux s’appliquent aux types de données monétaires, numériques, de date et d’heure. Le paramètre de conversion s’applique uniquement à la conversion de sortie et n’est visible que lorsque des valeurs de devise, numériques, de date ou d’heure sont converties en chaînes de caractères**.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise les paramètres régionaux du Registre pour l'utilisateur actuel. Le pilote n’honore pas les paramètres régionaux du thread actuel si l’application l’a défini après la connexion par, par exemple, en appelant **SetThreadLocale**.  
  
 La modification du comportement régional d'une source de données peut provoquer l'échec de l'application. Une application qui analyse des chaînes de date et s'attend à ce qu'elles apparaissent comme défini par ODBC pourrait être affectée de manière négative par la modification de cette valeur.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Mots clés de chaîne de connexion du fournisseur OLE DB  
 Il existe deux manières pour les applications OLE DB d'initialiser des objets source de données :  
  
-   **IDBInitialize :: Initialize**  
  
-   **IDataInitialize :: GetDataSource**  
  
 Dans le premier cas, une chaîne du fournisseur peut être utilisée pour initialiser des propriétés de connexion en définissant la propriété DBPROP_INIT_PROVIDERSTRING dans le jeu de propriétés DBPROPSET_DBINIT. Dans le deuxième cas, une chaîne d’initialisation peut être passée à la méthode **IDataInitialize::GetDataSource** pour initialiser des propriétés de connexion. Les deux méthodes initialisent les mêmes propriétés de connexion OLE DB, mais des jeux de mots clés différents sont utilisés. L’ensemble de mots clés utilisé par **IDataInitialize::GetDataSource** est au minimum la description des propriétés présentes dans le groupe de propriétés d’initialisation.  
  
 Lorsqu'un paramètre de chaîne du fournisseur qui a une propriété OLE DB correspondante définie à une certaine valeur par défaut ou explicitement définie avec une valeur, la valeur de la propriété OLE DB remplace le paramètre dans la chaîne du fournisseur.  
  
 Les propriétés booléennes définies dans les chaînes du fournisseur via des valeurs DBPROP_INIT_PROVIDERSTRING sont définies à l'aide des valeurs « yes » et « no ». Les propriétés booléennes définies dans les chaînes d’initialisation à l’aide de **IDataInitialize::GetDataSource** sont définies à l’aide des valeurs « true » et « false ».  
  
 Les applications qui utilisent **IDataInitialize::GetDataSource** peuvent également utiliser les mots clés utilisés par **IDBInitialize::Initialize**, mais uniquement pour les propriétés qui n’ont pas de valeur par défaut. Si une application utilise à la fois le mot clé **IDataInitialize::GetDataSource** et le mot clé **IDBInitialize::Initialize** dans la chaîne d’initialisation, le paramètre de mot clé **IDataInitialize::GetDataSource** est utilisé. Il est fortement recommandé que les applications n’utilisent pas de mots clés **IDBInitialize::Initialize** dans les chaînes de connexion **IDataInitialize:GetDataSource**, car ce comportement peut ne pas être conservé dans les versions ultérieures.  
  
 **Remarque :** Une chaîne de connexion passée via **IDataInitialize :: GetDataSource** est convertie en propriétés et appliquée via **IDBProperties :: SetProperties**. Si les services de composants ont trouvé la description de la propriété dans **IDBProperties::GetPropertyInfo**, cette propriété sera appliquée comme une propriété autonome. Sinon, elle sera appliquée par le biais de la propriété DBPROP_PROVIDERSTRING. Par exemple, si vous spécifiez la chaîne de connexion **Data source = server1 ; Server = Server2**, `Data Source` sera défini en tant que propriété, mais `Server` passera dans une chaîne de fournisseur.  
  
 Si vous spécifiez plusieurs instances de la même propriété spécifique au fournisseur, la première valeur de la première propriété est utilisée.  
  
 Les chaînes de connexion utilisées par les applications OLE DB utilisant DBPROP_INIT_PROVIDERSTRING avec **IDBInitialize::Initialize** ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre accolades, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs d'attributs contiennent des signes non alphanumériques. Il est supposé que la première accolade fermante dans la valeur termine la valeur ; par conséquent, les valeurs ne peuvent pas contenir de caractères d'accolade fermante.  
  
 Un espace après le signe égal (=) d’un mot clé de chaîne de connexion sera interprété comme un littéral, même si la valeur est placée entre guillemets.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec DBPROP_INIT_PROVIDERSTRING.  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|`Addr`|SSPROP_INIT_NETWORKADDRESS|Synonyme de « Address ».|  
|`Address`|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d'informations sur la syntaxe d'adresse valide, consultez la description du mot clé ODBC `Address`, plus loin dans cette rubrique.|  
|`APP`|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|`ApplicationIntent`|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont `ReadOnly` et `ReadWrite`.<br /><br /> Par défaut, il s’agit de `ReadWrite`. Pour plus d’informations [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur la prise en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]de Native Client pour, consultez [SQL Server Native Client la prise en charge de la haute disponibilité et de la récupération d’urgence](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`AttachDBFileName`|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser `AttachDBFileName`, vous devez également spécifier le nom de la base de données avec le mot clé Database de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « yes » et « no ».|  
|`Database`|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données à utiliser. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données SQL Server 2000.|  
|`Encrypt`|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|`FailoverPartner`|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|`FailoverPartnerSPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|`Language`|SSPROPT_INIT_CURRENTLANGUAGE|Langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`MarsConn`|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion si le serveur est [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|`Net`|SSPROP_INIT_NETWORKLIBRARY|Synonyme de « Network ».|  
|`Network`|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Synonyme de « Network ».|  
|`PacketSize`|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|`PersistSensitive`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « yes » et « no » comme valeurs. Lorsque « no » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes|  
|`PWD`|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Server`|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d'informations sur la syntaxe d'adresse valide, consultez la description du mot clé ODBC `Server` dans cette rubrique.|  
|`ServerSPN`|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|`Timeout`|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|`Trusted_Connection`|DBPROP_AUTH_INTEGRATED|Lorsque la valeur « yes » est spécifiée, fait en sorte que le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le mode d'authentification Windows pour la validation de connexion. Autrement, fait en sorte que le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise un nom d'utilisateur et un mot de passe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour la validation de connexion, et les mots clés UID et PWD doivent être spécifiés.|  
|`TrustServerCertificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « yes » et « no » comme valeurs. La valeur par défaut est « no », ce qui signifie que le certificat de serveur sera validé.|  
|`UID`|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`UseProcForPrepare`|SSPROP_INIT_USEPROCFORPREP|Ce mot clé est déconseillé et sa valeur est ignorée par le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`WSID`|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 Les chaînes de connexion utilisées par les applications OLE DB utilisant **IDataInitialize::GetDataSource** ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 L'utilisation des propriétés doit être conforme à la syntaxe autorisée dans l'étendue.  Par exemple, `WSID` utilise`{}`des guillemets () `Application Name` et utilise des caractères de guillemets`'`simples () ou`"`doubles (). Seules les propriétés de chaîne peuvent être mises entre guillemets. Si vous tentez de placer entre guillemets un entier ou une propriété énumérée, une erreur indiquant que la chaîne de connexion n'est pas conforme à la spécification OLE DB sera générée.  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre guillemets simples ou doubles, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs contiennent des caractères non alphanumériques. Le caractère de guillemet utilisé peut également apparaître dans des valeurs, à condition d'être doublé.  
  
 Un espace après le signe égal (=) d’un mot clé de chaîne de connexion sera interprété comme un littéral, même si la valeur est placée entre guillemets.  
  
 Si une chaîne de connexion a plusieurs des propriétés répertoriées dans le tableau suivant, la valeur de la dernière propriété sera utilisée.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec **IDataInitialize::GetDataSource** :  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|`Application Name`|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|`Application Intent`|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont `ReadOnly` et `ReadWrite`.<br /><br /> Par défaut, il s’agit de `ReadWrite`. Pour plus d’informations [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur la prise en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]de Native Client pour, consultez [SQL Server Native Client la prise en charge de la haute disponibilité et de la récupération d’urgence](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « true » et « false ».|  
|`Connect Timeout`|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|`Current Language`|SSPROPT_INIT_CURRENTLANGUAGE|Nom de la langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Data Source`|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d'informations sur la syntaxe d'adresse valide, consultez la description du mot clé ODBC `Server`, plus loin dans cette rubrique.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données à utiliser. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|`Failover Partner`|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|`Failover Partner SPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|`Initial Catalog`|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|`Initial File Name`|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser `AttachDBFileName`, vous devez également spécifier le nom de la base de données avec le mot clé DATABASE de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|`Integrated Security`|DBPROP_AUTH_INTEGRATED|Accepte la valeur « SSPI » pour l'authentification Windows.|  
|`MARS Connection`|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion. Les valeurs reconnues sont « true » et « false ». La valeur par défaut est « false ».|  
|`Network Address`|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d'informations sur la syntaxe d'adresse valide, consultez la description du mot clé ODBC `Address`, plus loin dans cette rubrique.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|`Packet Size`|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|`Password`|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Persist Security Info`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « true » et « false » comme valeurs. Lorsque « false » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes|  
|`Provider`||Pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ce doit être « SQLNCLI11 ».|  
|`Server SPN`|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|`Trust Server Certificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « true » et « false » comme valeurs. La valeur par défaut est « false », ce qui signifie que le certificat de serveur sera validé.|  
|`Use Encryption for Data`|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».|  
|`User ID`|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Workstation ID`|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 **Remarque** Dans la chaîne de connexion, la propriété « ancien mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui est le mot de passe actuel (éventuellement arrivé à expiration) qui n’est pas disponible via une propriété de chaîne de fournisseur.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Mots clés de chaîne de connexion ActiveX Data Objects (ADO)  
 Les applications ADO définissent la propriété **ConnectionString** des objets **ADODBConnection** ou fournissent une chaîne de connexion comme paramètre à la méthode **Open** des objets **ADODBConnection**.  
  
 Les applications ADO peuvent également utiliser les mots clés utilisés par la méthode OLE DB **IDBInitialize::Initialize**, mais uniquement pour les propriétés qui n’ont pas de valeur par défaut. Si une application utilise à la fois les mots clés ADO et les mots clés **IDBInitialize::Initialize** dans la chaîne d’initialisation, le paramètre de mot clé ADO est utilisé. Il est vivement recommandé que les applications utilisent uniquement des mots clés de chaîne de connexion ADO.  
  
 Les chaînes de connexion utilisées par ADO ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre guillemets doubles, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs contiennent des caractères non alphanumériques. Les valeurs d'attributs ne peuvent pas contenir de guillemets doubles.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec une chaîne de connexion ADO :  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|`Application Intent`|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont `ReadOnly` et `ReadWrite`.<br /><br /> Par défaut, il s’agit de `ReadWrite`. Pour plus d’informations [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur la prise en charge [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]de Native Client pour, consultez [SQL Server Native Client la prise en charge de la haute disponibilité et de la récupération d’urgence](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Application Name`|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « true » et « false ».|  
|`Connect Timeout`|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|`Current Language`|SSPROPT_INIT_CURRENTLANGUAGE|Nom de la langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Data Source`|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d'informations sur la syntaxe d'adresse valide, consultez la description du mot clé ODBC `Server` dans cette rubrique.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données qui sera utilisé. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données SQL Server 2000.|  
|`Failover Partner`|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|`Failover Partner SPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|`Initial Catalog`|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|`Initial File Name`|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser `AttachDBFileName`, vous devez également spécifier le nom de la base de données avec le mot clé DATABASE de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|`Integrated Security`|DBPROP_AUTH_INTEGRATED|Accepte la valeur « SSPI » pour l'authentification Windows.|  
|`MARS Connection`|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion si le serveur est [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Les valeurs reconnues sont « true » et « false ». La valeur par défaut est « false ».|  
|`Network Address`|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d'informations sur la syntaxe d'adresse valide, consultez la description du mot clé ODBC `Address` dans cette rubrique.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|`Packet Size`|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|`Password`|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Persist Security Info`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « true » et « false » comme valeurs. Lorsque « false » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes.|  
|`Provider`||Pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ce doit être « SQLNCLI11 ».|  
|`Server SPN`|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|`Trust Server Certificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « true » et « false » comme valeurs. La valeur par défaut est « false », ce qui signifie que le certificat de serveur sera validé.|  
|`Use Encryption for Data`|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».|  
|`User ID`|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Workstation ID`|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 **Remarque** Dans la chaîne de connexion, la propriété « ancien mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui est le mot de passe actuel (éventuellement arrivé à expiration) qui n’est pas disponible via une propriété de chaîne de fournisseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
