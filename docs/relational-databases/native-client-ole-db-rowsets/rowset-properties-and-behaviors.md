---
title: "Propriétés et comportements | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], properties
- SQL Server Native Client OLE DB provider, rowsets
- properties [OLE DB]
- OLE DB rowsets, properties
ms.assetid: 9baabcb6-0114-42f2-89f8-d8d66b3c8c14
caps.latest.revision: "47"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 68f4ffdbf0408a936d7a2c9b49f18eb8adb32520
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="rowset-properties-and-behaviors"></a>Propriétés et comportements de l'ensemble de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il s’agit du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] propriétés ensemble de lignes du fournisseur OLE DB Native Client.  
  
|ID de propriété| Description|  
|-----------------|-----------------|  
|DBPROP_ABORTPRESERVE|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : le comportement d'un ensemble de lignes après une opération d'abandon est déterminé par cette propriété.<br /><br /> VARIANT_FALSE : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif invalide les ensembles de lignes après une opération d’abandon. Les fonctionnalités de l'objet d'ensemble de lignes sont quasiment perdues. Il prend uniquement en charge **IUnknown** opérations et la version de handles de ligne et d’accesseur en attente.<br /><br /> VARIANT_TRUE : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur gère un ensemble de lignes valide.|  
|DBPROP_ACCESSORDER|R/W : lecture/écriture<br /><br /> Valeur par défaut : DBPROPVAL_AO_RANDOM<br /><br /> Description : ordre d'accès. Ordre dans lequel les colonnes doivent être accessibles dans l'ensemble de lignes.<br /><br /> DBPROPVAL_AO_RANDOM : les colonnes sont accessibles dans n'importe quel ordre.<br /><br /> DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS : les colonnes liées en tant qu'objets de stockage sont accessibles uniquement dans l'ordre séquentiel déterminé par l'ordinal de colonne.<br /><br /> DBPROPVAL_AO_SEQUENTIAL : toutes les colonnes doivent être accessibles dans l'ordre séquentiel déterminé par l'ordinal de colonne.|  
|DBPROP_APPENDONLY|Cette propriété de l’ensemble de lignes n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la valeur de propriété génère une erreur.|  
|DBPROP_BLOCKINGSTORAGEOBJECTS|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bloc d’objets du stockage de fournisseur OLE DB Native Client à l’aide d’autres méthodes de l’ensemble de lignes.|  
|DBPROP_BOOKMARKS DBPROP_LITERALBOOKMARKS|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur prend en charge les signets pour l’identification des lignes de jeu de lignes lorsque DBPROP_BOOKMARKS ou DBPROP_LITERALBOOKMARKS a la valeur VARIANT_TRUE.<br /><br /> L'affectation de la valeur VARIANT_TRUE à l'une ou l'autre des propriétés ne permet pas le positionnement dans l'ensemble de lignes à partir d'un signet. Affectez VARIANT_TRUE à DBPROP_IRowsetLocate ou DBPROP_IRowsetScroll pour créer un ensemble de lignes prenant en charge le positionnement dans l'ensemble de lignes à partir d'un signet.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de fournisseur OLE DB Native Client utilise un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseur pour prendre en charge un ensemble de lignes qui contient des signets. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).<br /><br /> Remarque : Définition de ces propriétés en conflit avec d’autres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définition de curseur des propriétés du fournisseur OLE DB Native Client provoque une erreur. Par exemple, si DBPROP_BOOKMARKS a la valeur VARIANT_TRUE alors que DBPROP_OTHERINSERT a également la valeur VARIANT_TRUE, une erreur est générée lorsque le consommateur essaie d'ouvrir un ensemble de lignes.|  
|DBPROP_BOOKMARKSKIPPED|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne DB_E_BADBOOKMARK si le consommateur indique un signet non valide lors du positionnement ou un ensemble de lignes contenant la recherche.|  
|DBPROP_BOOKMARKTYPE|R/w : lecture seule<br /><br /> Valeur par défaut : DBPROPVAL_BMK_NUMERIC<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client implémente uniquement des signets numériques. A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] signet du fournisseur OLE DB Native Client est entier non signé de 32 bits, de type DBTYPE_UI4.|  
|DBPROP_CACHEDEFERRED|Cette propriété de l’ensemble de lignes n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la valeur de propriété génère une erreur.|  
|DBPROP_CANFETCHBACKWARDS DBPROP_CANSCROLLBACKWARDS|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge l’extraction vers l’arrière et le défilement dans les ensembles de lignes non séquentielles. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif crée un ensemble de lignes pris en charge de curseur lorsque DBPROP_CANFETCHBACKWARDS ou DBPROP_CANSCROLLBACKWARDS a la valeur VARIANT_TRUE. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).|  
|DBPROP_CANHOLDROWS|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : par défaut, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne DB_E_ROWSNOTRELEASED si le consommateur essaie d’obtenir plusieurs lignes pour un ensemble de lignes lors de modifications en attente existe sur ceux actuellement dans l’ensemble de lignes. Ce comportement peut être modifié.<br /><br /> L'affectation de la valeur VARIANT_TRUE à DBPROP_CANHOLDROWS et DBPROP_IRowsetChange implique un ensemble de lignes contenant un signet. Si les deux propriétés ont la valeur VARIANT_TRUE, le **IRowsetLocate** interface est disponible sur l’ensemble de lignes et DBPROP_BOOKMARKS et DBPROP_LITERALBOOKMARKS sont les deux VARIANT_TRUE.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Natives Client OLE DB fournisseur ensembles de lignes qui contiennent les signets sont pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les curseurs.|  
|DBPROP_CHANGEINSERTEDROWS|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : cette propriété peut être définie uniquement à VARIANT_TRUE si l'ensemble de lignes utilise un curseur de jeu de clés.|  
|DBPROP_COLUMNRESTRICT|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif définit la propriété à VARIANT_TRUE lorsqu’une colonne dans un ensemble de lignes ne peut pas être modifiée par le consommateur. D'autres colonnes de l'ensemble de lignes peuvent être mises à jour et les lignes elles-mêmes peuvent être supprimées.<br /><br /> Lorsque la propriété a la valeur VARIANT_TRUE, le consommateur examine le *dwFlags* membre de la structure DBCOLUMNINFO pour déterminer si la valeur d’une colonne individuelle peut être écrite ou non. Pour les colonnes modifiables, *dwFlags* expose DBCOLUMNFLAGS_WRITE.|  
|DBPROP_COMMANDTIMEOUT|R/W : lecture/écriture<br /><br /> Par défaut : 0<br /><br /> Description : par défaut, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif n’expire pas sur le **ICommand::Execute** (méthode).|  
|DBPROP_COMMITPRESERVE|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : le comportement d'un ensemble de lignes après une opération de validation est déterminé par cette propriété.<br /><br /> VARIANT_TRUE : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur gère un ensemble de lignes valide.<br /><br /> VARIANT_FALSE : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif invalide les ensembles de lignes après une opération de validation. Les fonctionnalités de l'objet d'ensemble de lignes sont quasiment perdues. Il prend uniquement en charge **IUnknown** opérations et la version de handles de ligne et d’accesseur en attente.|  
|DBPROP_DEFERRED|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Lorsque la valeur VARIANT_TRUE le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client essaie d’utiliser un curseur côté serveur pour l’ensemble de lignes. **Texte**, **ntext**, et **image** colonnes ne sont pas retournées à partir du serveur jusqu'à ce qu’ils sont accessibles par l’application.|  
|DBPROP_DELAYSTORAGEOBJECTS|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge le mode de mise à jour immédiate sur les objets de stockage.<br /><br /> Les modifications apportées aux données dans un objet de flux séquentiel sont immédiatement envoyées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les modifications sont validées selon le mode de transaction de l'ensemble de lignes.|  
|DBPROP_HIDDENCOLUMNS|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> **Description :** nombre de colonnes masquées<br /><br /> Si DBPROP_UNIQUEROWS a la valeur VARIANT_TRUE, la propriété DBPROP_HIDDENCOLUMNS retourne le nombre de colonnes « cachées » supplémentaires ajoutées par le fournisseur pour identifier les lignes de manière unique dans l'ensemble de lignes. Ces colonnes sont retournées par **IColumnsInfo::GetColumnInfo** et **IColumnsRowset::GetColumnsRowset**. Toutefois, ils ne sont pas inclus dans le nombre de lignes retournées par la *pcColumns* argument retourné par **IColumnsInfo::GetColumnInfo**.<br /><br /> Pour déterminer le nombre total de colonnes représentées dans le *prgInfo* structure retournée par **IColumnsInfo::GetColumnInfo**, y compris les colonnes masquées, le consommateur ajoute la valeur de DBPROP_HIDDENCOLUMNS au nombre de colonnes retourné par **IColumnsInfo::GetColumnInfo** dans *pcColumns*. Si DBPROP_UNIQUEROWS a la valeur VARIANT_FALSE, DBPROP_HIDDENCOLUMNS a la valeur zéro.|  
|DBPROP_IAccessor DBPROP_IColumnsInfo DBPROP_IConvertType DBPROP_IRowset DBPROP_IRowsetInfo|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge ces interfaces sur tous les ensembles de lignes.|  
|DBPROP_IColumnsRowset|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client le **IColumnsRowset** interface.|  
|DBPROP_IConnectionPointContainer|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : IConnectionPointContainer. Si la valeur est VARIANT_TRUE, l'ensemble de lignes prend en charge l'interface spécifiée. Si la valeur est VARIANT_FALSE, l'ensemble de lignes ne prend pas en charge l'interface spécifiée. Les fournisseurs qui prennent en charge une interface doivent prendre en charge la propriété associée à cette interface avec une valeur VARIANT_TRUE. Ces propriétés sont essentiellement utilisées pour adresser des requêtes aux interfaces via ICommandProperties::SetProperties.|  
|DBPROP_IMultipleResults|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client le **IMultipleResults** interface.|  
|DBPROP_IRowsetChange DBPROP_IRowsetUpdate|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client le **IRowsetChange** et **IRowsetUpdate** interfaces.<br /><br /> Un ensemble de lignes créé en utilisant DBPROP_IRowsetChange avec la valeur VARIANT_TRUE dévoile les comportements du mode de mise à jour immédiate.<br /><br /> Lorsque DBPROP_IRowsetUpdate a la valeur VARIANT_TRUE, DBPROP_IRowsetChange a également la valeur VARIANT_TRUE. L'ensemble de lignes expose le comportement du mode de mise à jour différée.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de fournisseur OLE DB Native Client utilise un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseur pour prendre en charge les ensembles de lignes exposant **IRowsetChange** ou **IRowsetUpdate**. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).|  
|DBPROP_IRowsetIdentity|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client le **IRowsetIdentity** interface. Si un ensemble de lignes prend en charge cette interface, deux handles de ligne représentant la même ligne sous-jacente reflètent toujours les mêmes données et le même état. Les consommateurs peuvent appeler le **IRowsetIdentity :: IsSameRow** méthode pour comparer deux handles de ligne pour voir s’ils font référence à la même instance de ligne.|  
|DBPROP_IRowsetLocate DBPROP_IRowsetScroll|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur peut exposer le **IRowsetLocate** et **IRowsetScroll** interfaces.<br /><br /> Lorsque DBPROP_IRowsetLocate a la valeur VARIANT_TRUE, DBPROP_CANFETCHBACKWARDS et DBPROP_CANSCROLLBACKWARDS ont également la valeur VARIANT_TRUE.<br /><br /> Lorsque DBPROP_IRowsetScroll a la valeur VARIANT_TRUE, DBPROP_IRowsetLocate a également la valeur VARIANT_TRUE ; en outre, les deux interfaces sont disponibles dans l'ensemble de lignes.<br /><br /> Les signets sont requis pour les deux interfaces. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client définit DBPROP_BOOKMARKS et DBPROP_LITERALBOOKMARKS à VARIANT_TRUE lorsque le consommateur demande l’interface.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de fournisseur OLE DB Native Client utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour prendre en charge les curseurs **IRowsetLocate** et **IRowsetScroll**. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).<br /><br /> Définition de ces propriétés en conflit avec d’autres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définition de curseur des propriétés du fournisseur OLE DB Native Client provoque une erreur. Par exemple, si DBPROP_IRowsetScroll a la valeur VARIANT_TRUE alors que DBPROP_OTHERINSERT a également la valeur VARIANT_TRUE, une erreur est générée lorsque le consommateur essaie d'ouvrir un ensemble de lignes.|  
|DBPROP_IRowsetResynch|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **IRowsetResynch** interface à la demande. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur peut exposer l’interface sur n’importe quel ensemble de lignes.|  
|DBPROP_ISupportErrorInfo|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ISupportErrorInfo** interface sur les ensembles de lignes.|  
|DBPROP_ILockBytes|Cette interface n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la propriété génère une erreur.|  
|DBPROP_ISequentialStream|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ISequentialStream** interface pour prendre en charge de temps, les données de longueur variable stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBPROP_IStorage|Cette interface n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la propriété génère une erreur.|  
|DBPROP_IStream|Cette interface n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la propriété génère une erreur.|  
|DBPROP_IMMOBILEROWS|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : la propriété a uniquement la valeur VARIANT_TRUE pour les curseurs de jeu de clés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Elle a la valeur VARIANT_FALSE pour tous les autres curseurs.<br /><br /> VARIANT_TRUE : l'ensemble de lignes ne réorganise pas les lignes insérées ou mises à jour. Pour **IRowsetChange::InsertRow**, lignes apparaissent à la fin de l’ensemble de lignes. Pour **IRowsetChange::SetData**, si l’ensemble de lignes n’est pas ordonné, la position des lignes mises à jour n’est pas modifiée. Si l’ensemble de lignes est ordonné et **IRowsetChange::SetData** change une colonne qui est utilisée pour l’ensemble de lignes, la ligne de commande n’est pas déplacé. Si l'ensemble de lignes est basé sur un jeu de colonnes clés (en général, un ensemble de lignes pour lequel DBPROP_OTHERUPDATEDELETE a la valeur VARIANT_TRUE mais où DBPROP_OTHERINSERT a la valeur VARIANT_FALSE), la modification de la valeur d'une colonne clé est généralement équivalente à la suppression de la ligne actuelle et à l'insertion d'une nouvelle ligne. Par conséquent, la ligne peut se déplacer, voire disparaître, dans l'ensemble de lignes, si DBPROP_OWNINSERT a la valeur VARIANT_FALSE, alors que la propriété DBPROP_IMMOBILEROWS a la valeur VARIANT_TRUE.<br /><br /> VARIANT_FALSE : si l'ensemble de lignes est ordonné, les lignes insérées apparaissent dans l'ordre approprié de l'ensemble de lignes. Si l'ensemble de lignes n'est pas ordonné, la ligne insérée apparaît à la fin. Si **IRowsetChange::SetData** modifie une colonne qui est utilisé pour le déplacement de l’ensemble de lignes, la ligne de commande. Si l'ensemble de lignes n'est pas ordonné, la position de la ligne ne change pas.|  
|DBPROP_LITERALIDENTITY|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : cette propriété a toujours la valeur VARIANT_TRUE.|  
|DBPROP_LOCKMODE|R/W : lecture/écriture<br /><br /> Valeur par défaut : DBPROPVAL_LM_NONE<br /><br /> Description : niveau du verrouillage effectué par l'ensemble de lignes (DBPROPVAL_LM_NONE, DBPROPVAL_LM_SINGLEROW).<br /><br /> Remarque : Lorsque vous utilisez l’isolement d’instantané dans une transaction, si un ensemble de lignes est ouvert à l’aide d’un curseur keyset ou serveur dynamique et le mode de verrouillage a la valeur DBPROPVAL_LM_SINGLEROW, une erreur se produit lors de l’extraction d’une ligne si une autre personne a mis à jour cette ligne depuis le début de la transaction. Pour les autres types de curseurs et modes de verrouillage, si une autre personne a mis à jour la ligne depuis le début de la transaction, aucune erreur ne se produit tant que l'utilisateur n'essaie pas de mettre à jour cette ligne. Dans les deux cas, ces erreurs sont générées par le serveur.|  
|DBPROP_MAXOPENROWS|R/w : lecture seule<br /><br /> Par défaut : 0<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne limite pas le nombre de lignes qui peuvent être actives dans les ensembles de lignes.|  
|DBPROP_MAXPENDINGROWS|R/w : lecture seule<br /><br /> Par défaut : 0<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne limite pas le nombre de lignes du jeu de lignes avec des modifications en attente.|  
|DBPROP_MAXROWS|R/W : lecture/écriture<br /><br /> Par défaut : 0<br /><br /> Description : par défaut, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne limite pas le nombre de lignes dans un ensemble de lignes. Lorsque le consommateur définit DBPROP_MAXROWS, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif utilise l’instruction SET ROWCOUNT pour limiter le nombre de lignes dans l’ensemble de lignes.<br /><br /> SET ROWCOUNT peut avoir des conséquences inattendues dans l'exécution de l'instruction [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [SET ROWCOUNT](../../t-sql/statements/set-rowcount-transact-sql.md).|  
|DBPROP_MAYWRITECOLUMN|Cette propriété de l’ensemble de lignes n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la valeur de propriété génère une erreur.|  
|DBPROP_MEMORYUSAGE|Cette propriété de l’ensemble de lignes n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la valeur de propriété génère une erreur.|  
|DBPROP_NOTIFICATIONGRANULARITY|Cette propriété de l’ensemble de lignes n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la valeur de propriété génère une erreur.|  
|DBPROP_NOTIFICATIONPHASES|R/w : lecture seule<br /><br /> Valeur par défaut : DBPROPVAL_NP_OKTODO &#124; DBPROPVAL_NP_ABOUTTODO &#124;  DBPROPVAL_NP_SYNCHAFTER &#124; DBPROPVAL_NP_FAILEDTODO &#124;  DBPROPVAL_NP_DIDEVENT<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge toutes les phases de notification.|  
|DBPROP_NOTIFYCOLUMNSET DBPROP_NOTIFYROWDELETE DBPROP_NOTIFYROWFIRSTCHANGE DBPROP_NOTIFYROWINSERT DBPROP_NOTIFYROWRESYNCH DBPROP_NOTIFYROWSETRELEASE DBPROP_NOTIFYROWSETFETCH-POSITIONCHANGE DBPROP_NOTIFYROWUNDOCHANGE DBPROP_NOTIFYROWUNDODELETE DBPROP_NOTIFYROWUNDOINSERT DBPROP_NOTIFYROWUPDATE|R/w : lecture seule<br /><br /> Valeur par défaut : DBPROPVAL_NP_OKTODO &#124;  DBPROPVAL_NP_ABOUTTODO<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] phases de notification du fournisseur OLE DB Native Client sont annulables avant toute tentative d’exécution de la modification de l’ensemble de lignes indiqué. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne prend pas en charge l’annulation de phase issue de la tentative.|  
|DBPROP_ORDEREDBOOKMARKS|Cette propriété de l’ensemble de lignes n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la valeur de propriété génère une erreur.|  
|DBPROP_OTHERINSERT DBPROP_OTHERUPDATEDELETE DBPROP_OWNINSERT DBPROP_OWNUPDATEDELETE|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Paramètre modifie la visibilité propriétés entraîne la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client à utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseurs pour prendre en charge l’ensemble de lignes. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).|  
|DBPROP_QUICKRESTART|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Lorsque la valeur VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client essaie d’utiliser un curseur côté serveur pour l’ensemble de lignes.|  
|DBPROP_REENTRANTEVENTS|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensembles de lignes du fournisseur OLE DB Native Client sont réentrants et peuvent retourner DB_E_NOTREENTRANT si un consommateur essaie d’accéder à une méthode réentrante d’ensemble de lignes à partir d’un rappel de notification.|  
|DBPROP_REMOVEDELETED|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif modifie la valeur de la propriété en fonction de la visibilité des modifications apportées à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données exposées par l’ensemble de lignes.<br /><br /> VARIANT_TRUE : les lignes supprimées par le consommateur ou d'autres utilisateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont supprimées de l'ensemble de lignes lorsque ce dernier est actualisé. DBPROP_OTHERINSERT a la valeur VARIANT_TRUE.<br /><br /> VARIANT_FALSE : les lignes supprimées par le consommateur ou d'autres utilisateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas supprimées de l'ensemble de lignes lorsque ce dernier est actualisé. La valeur d'état de ligne pour les lignes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprimées dans l'ensemble de lignes est DBROWSTATUS_E_DELETED. DBPROP_OTHERINSERT a la valeur VARIANT_TRUE.<br /><br /> Cette propriété a seulement une valeur pour les ensembles de lignes pris en charge par les curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).<br /><br /> Lorsque la propriété DBPROP_REMOVEDELETED est implémentée sur un ensemble de lignes du curseur keyset, les lignes supprimées sont enlevées au moment de l’extraction et il est possible pour les méthodes d’extraction de lignes, telles que **GetNextRows** et **GetRowsAt,** pour retourner S_OK et moins de lignes que celle demandée. Notez que ce comportement ne correspond pas à la condition DB_S_ENDOFROWSET et que le nombre de lignes retournées ne peut jamais être nul s'il reste des lignes.|  
|DBPROP_REPORTMULTIPLECHANGES|Cette propriété de l’ensemble de lignes n’est pas implémentée par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Toute tentative de lecture ou d'écriture de la valeur de propriété génère une erreur.|  
|DBPROP_RETURNPENDINGINSERTS|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Lorsqu’une méthode qui extrait des lignes est appelée, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne retourne pas les lignes en attente d’insertion.|  
|DBPROP_ROWRESTRICT|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensembles de lignes du fournisseur OLE DB Native Client ne prennent pas en charge les droits d’accès en fonction de la ligne. Si le **IRowsetChange** interface est exposée sur un ensemble de lignes, la **SetData** méthode peut être appelée par le consommateur.|  
|DBPROP_ROWSET_ASYNCH|R/W : lecture/écriture<br /><br /> Par défaut : 0<br /><br /> Description : permet le traitement asynchrone de l'ensemble de lignes. Cette propriété figure dans le groupe de propriétés d'ensemble de lignes et dans le jeu de propriétés DBPROPSET_ROWSET. Le type est VT_14.<br /><br /> La seule valeur dans le masque de bits pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est **DBPROPVAL_ASYNCH_INITIALIZE**.|  
|DBPROP_ROWTHREADMODEL|R/w : lecture seule<br /><br /> Valeur par défaut : DBPROPVAL_RT_FREETHREAD<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge l’accès à ses objets à partir de plusieurs threads d’exécution d’un consommateur unique.|  
|DBPROP_SERVERCURSOR|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : une fois la propriété définie, un curseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est utilisé pour prendre en charge l'ensemble de lignes. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).|  
|DBPROP_SERVERDATAONINSERT|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : données du serveur lors de l'insertion.<br /><br /> VARIANT_TRUE : au moment où une insertion est transmise au serveur, le fournisseur récupère les données du serveur afin de mettre à jour le cache de lignes local.<br /><br /> VARIANT_FALSE : le fournisseur ne récupère pas les valeurs du serveur pour les lignes récemment insérées.|  
|DBPROP_STRONGIDENTITY|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : identité de ligne forte. Si les insertions sont autorisées sur un ensemble de lignes (soit **IRowsetChange** ou **IRowsetUpdate** a la valeur true) et si DBPROP_UPDATABILITY est défini pour prendre en charge InsertRows, la valeur de DBPROP_STRONGIDENTITY dépend de la propriété DBPROP_CHANGEINSERTEDROWS (sera VARIANT_FALSE si la valeur de la propriété DBPROP_CHANGEINSERTEDROWS est VARIANT_FALSE).|  
|DBPROP_TRANSACTEDOBJECT|R/w : lecture seule<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge uniquement les objets transactionnels. Pour plus d’informations, consultez [Transactions](../../relational-databases/native-client-ole-db-transactions/transactions.md).|  
|DBPROP_UNIQUEROWS|R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : lignes uniques.<br /><br /> VARIANT_TRUE : chaque ligne est identifiée uniquement par ses valeurs de colonnes. Le jeu de colonnes qui identifient la ligne dbcolumnflags_keycolumn est défini dans la structure DBCOLUMNINFO retournée à partir de la **GetColumnInfo** (méthode).<br /><br /> VARIANT_FALSE : les lignes peuvent être identifiées ou non de manière unique par leurs valeurs de colonnes. Les colonnes clés peuvent être signalées ou non à l'aide de DBCOLUMNFLAGS_KEYCOLUMN.|  
|DBPROP_UPDATABILITY|R/W : lecture/écriture<br /><br /> Par défaut : 0<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge toutes les valeurs DBPROP_UPDATABILITY. La définition de DBPROP_UPDATABILITY ne crée pas d'ensemble de lignes modifiable. Pour rendre un ensemble de lignes modifiable, définissez DBPROP_IRowsetChange ou DBPROP_IRowsetUpdate.|  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif définit l’ensemble de la propriété spécifique au fournisseur DBPROPSET_SQLSERVERROWSET comme indiqué dans cette table.  
  
|ID de propriété| Description|  
|-----------------|-----------------|  
|SSPROP_COLUMN_ID|Colonne : ColumnID<br /><br /> R/w : lecture seule<br /><br /> Type : VT_U12 &#124; VT_ARRAY<br /><br /> Valeur par défaut : VT_EMPTY<br /><br /> Description : tableau de valeurs entières représentant la position ordinale (de base 1) d'une colonne de résultats d'une clause COMPUTE dans l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT actuelle. Il s’agit de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] équivalent pour le fournisseur OLE DB Native Client de l’attribut ODBC SQL_CA_SS_COLUMN_ID.|  
|SSPROP_DEFERPREPARE|Colonne : non<br /><br /> R/W : lecture/écriture<br /><br /> Type : VT_BOOL<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : VARIANT_TRUE : dans l’exécution préparée, la préparation de la commande est différée jusqu'à ce que **ICommand::Execute** est appelée ou une opération de métapropriété est effectuée. Si la propriété a la valeur<br /><br /> VARIANT_FALSE : L’instruction est préparée lorsque **ICommandPrepare::Prepare** est exécutée.|  
|SSPROP_IRowsetFastLoad|Colonne : non<br /><br /> R/W : lecture/écriture<br /><br /> Type : VT_BOOL<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Définissez cette propriété à VARIANT_TRUE pour ouvrir un ensemble de lignes de chargement rapide via **IOpenRowset::OpenRowset**. Vous ne pouvez pas définir cette propriété dans **ICommandProperties::SetProperties**.|  
|SSPROP_ISSAsynchStatus|Colonne : non.<br /><br /> R/W : lecture/écriture<br /><br /> Type : VT_BOOL<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : Définissez cette propriété à VARIANT_TRUE pour activer les opérations asynchrones à l’aide de la [ISSAsynchStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md) interface.|  
|SSPROP_MAXBLOBLENGTH|Colonne : non<br /><br /> R/W : lecture/écriture<br /><br /> Type : VT_I4<br /><br /> Valeur par défaut : le fournisseur ne restreint pas la taille du texte retourné par le serveur et la valeur de propriété est définie à sa valeur maximale. Par exemple 2 147 483 647.<br /><br /> Description : Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client exécute une instruction SET TEXTSIZE pour restreindre la longueur des données d’objet binaire volumineux (BLOB) retournées dans une instruction SELECT.|  
|SSPROP_NOCOUNT_STATUS|Colonne : NoCount<br /><br /> R/w : lecture seule<br /><br /> Type : VT_BOOL<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : valeur booléenne représentant l'état de SET NOCOUNT ON/OFF dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :<br /><br /> VARIANT_TRUE : avec SET NOCOUNT ON<br /><br /> VARIANT_FALSE : avec SET NOCOUNT OFF|  
|SSPROP_QP_NOTIFICATION_MSGTEXT|Colonne : non<br /><br /> R/W : lecture/écriture<br /><br /> Type : VT_BSTR (entre 1 et 2 000 caractères sont autorisés)<br /><br /> Valeur par défaut : chaîne vide<br /><br /> Description : texte du message de notification de requête. Il est défini par l'utilisateur et n'a aucun format spécifique.|  
|SSPROP_QP_NOTIFICATION_OPTIONS|Colonne : non<br /><br /> R/W : lecture/écriture<br /><br /> Type : VT_BSTR<br /><br /> Valeur par défaut : chaîne vide<br /><br /> Description : options de notifications de requêtes. Elles sont spécifiées dans une chaîne avec `name=value`. L'utilisateur est chargé de créer le service et de lire les notifications de la file d'attente. La syntaxe de la chaîne des options de notifications de requêtes est :<br /><br /> `service=<service-name>[;(local database=<database>&#124;broker instance=<broker instance>)]`<br /><br /> Exemple :<br /><br /> `service=mySSBService;local database=mydb`|  
|SSPROP_QP_NOTIFICATION_TIMEOUT|Colonne : non<br /><br /> R/W : lecture/écriture<br /><br /> Type : VT_UI4<br /><br /> Valeur par défaut : 432 000 secondes (5 jours)<br /><br /> Valeur minimale : 1 seconde<br /><br /> Valeur maximale : 2^31-1 secondes<br /><br /> Description : nombre de secondes pendant lesquelles la notification de requête doit rester active.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  