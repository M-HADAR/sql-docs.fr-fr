---
title: Native Client, mettre à jour l’application SQL 2005
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, updating applications
ms.assetid: 1e1e570c-7f14-4e16-beab-c328e3fbdaa8
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2eddd2284ec77a1a4979389f964baeafb6932dc5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75243813"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Mise à jour d'une application depuis SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique décrit les modifications essentielles apportées à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client depuis [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Lorsque vous effectuez une mise à niveau de MDAC (Microsoft Data Access Components) vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vous pouvez constater également des différences de comportement. Pour plus d’informations, consultez [mise à jour d’une application vers SQL Server Native Client à partir de MDAC](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 livré avec [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 livré avec [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 livré avec [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 livré avec [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  
  
|Modification du comportement dans SQL Server Native Client depuis [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]|Description|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB effectue un remplissage uniquement à l'échelle définie.|Pour les conversions où les données converties sont envoyées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] au serveur, native client [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)](à compter de) remplit les zéros à droite dans les données uniquement jusqu’à la longueur maximale des valeurs **DateTime** . SQL Server Native Client 9.0 effectuaient un remplissage à neuf chiffres.|  
|Validez DBTYPE_DBTIMESTAMP pour ICommandWithParameter :: SetParameterInfo.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client (à compter [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]de) implémente l’OLE DB spécification pour *bScale* dans ICommandWithParameter :: SetParameterInfo à définir sur la précision en fractions de seconde pour DBTYPE_DBTIMESTAMP.|  
|La procédure stockée **sp_columns** retourne désormais la valeur **« no »** au lieu de **« no »** pour la colonne IS_NULLABLE.|À compter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de Native Client 10,0[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)](), **sp_columns** procédure stockée retourne désormais la valeur **« non »** au lieu de **« non »** pour une colonne IS_NULLABLE.|  
|SQLSetDescRec, SQLBindParameter et SQLBindCol effectuent maintenant la vérification de cohérence.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0, la définition de SQL_DESC_DATA_PTR n’a pas provoqué de vérification de cohérence pour un type de descripteur dans SQLSetDescRec, SQLBindParameter ou SQLBindCol.|  
|SQLCopyDesc effectue maintenant la vérification de la cohérence du descripteur.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0, SQLCopyDesc n’a pas effectué de vérification de cohérence lorsque le champ SQL_DESC_DATA_PTR était défini sur un enregistrement particulier.|  
|SQLGetDescRec n’effectue plus de vérification de cohérence de descripteur.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0, SQLGetDescRec effectue une vérification de cohérence du descripteur lors de la définition du champ SQL_DESC_DATA_PTR. Cela n'était pas requis par la spécification ODBC et dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) et les versions ultérieures, cette vérification de cohérence n'est plus effectuée.|  
|Erreur différente retournée lorsque la date est hors limites.|Pour le type **DateTime** , un numéro d’erreur différent est retourné par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (à compter [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]de) pour une date hors limites que celle qui a été retournée dans les versions antérieures.<br /><br /> Plus précisément [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , native client 9,0 a renvoyé 22007 pour toutes les valeurs hors limites de l’année dans les conversions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de chaînes en **DateTime**, et native[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]client à partir de la version 10,0 () retourne 22008 lorsque la date se trouve dans la plage prise en charge par **datetime2** , mais en dehors de la plage prise en charge par **DateTime** ou **smalldatetime**.|  
|la valeur **DateTime** tronque les fractions de seconde et non arrondies si l’arrondi modifie le jour.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, le comportement client pour les valeurs **datetime** envoyées au serveur consistait à les arrondir au 1/300e de seconde. Depuis [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, ce scénario provoque une troncation des fractions de seconde si l'arrondi modifie le jour.|  
|Trunction possibles de secondes pour la valeur **DateTime** .|Une application générée avec [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client (ou ultérieure) qui se connecte à un serveur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 tronquera des secondes et des fractions de seconde pour la partie heure des données envoyées au serveur si vous créez une liaison avec une colonne datetime avec un identificateur de type de DBTYPE_DBTIMESTAMP (OLE DB) ou SQL_TIMESTAMP (ODBC) et une échelle de 0.<br /><br /> Par exemple :<br /><br /> Données d'entrée : 1994-08-21 21:21:36.000<br /><br /> Données insérées : 1994-08-21 21:21:00.000|  
|La conversion de données OLE DB de DBTYPE_DBTIME vers DBTYPE_DATE ne peut plus provoquer de changement de jour.|Avant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, si la partie heure d'un DBTYPE_DATE était à moins d'une demi-seconde de minuit, le code de conversion OLE DB provoquait le changement de jour. Depuis [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, le jour ne change pas (les fractions de seconde sont tronquées et non arrondies).|  
|IBCPSession :: BCColFmt conversion des modifications.|À compter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de Native Client 10,0, lorsque vous utilisez IBCPSession :: BCOColFmt pour convertir SQLDATETIME ou SqlDateTime en un type chaîne, une valeur fractionnaire est exportée. Par exemple, lors de la conversion du type SQLDATETIME vers le type SQLNVARCHARMAX, les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client retournaient<br /><br /> 1989-02-01 00:00:00. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 et versions ultérieures retournent 1989-02-01 00:00:00.0000000.|  
|La taille des données envoyées doit correspondre à la longueur spécifiée dans SQL_LEN_DATA_AT_EXEC.|Lors de l'utilisation de SQL_LEN_DATA_AT_EXEC, la taille des données doit correspondre à la longueur que vous avez spécifiée avec SQL_LEN_DATA_AT_EXEC. Vous pouvez utiliser SQL_DATA_AT_EXEC, mais l'utilisation de SQL_LEN_DATA_AT_EXEC présente certains avantages en matière de performances.|  
|Les applications personnalisées qui utilisent l'API BCP peuvent maintenant afficher un avertissement.|L'API BCP génère un message d'avertissement si la longueur des données est supérieure à la longueur spécifiée pour un champ pour tous les types. Auparavant, cet avertissement était affiché uniquement pour les types caractère, et non pour tous les types.|  
|L’insertion d’une chaîne vide dans un **sql_variant** lié en tant que type date/heure génère une erreur.|Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0, l’insertion d’une chaîne vide dans un **sql_variant** lié en tant que type date/heure ne générait pas d’erreur. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 (et versions ultérieures) génère correctement une erreur dans cette situation.|  
|Validation des paramètres _TIMESTAMP SQL_C_TYPE et DBTYPE_DBTIMESTAMP plus stricte.|Avant [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client, les valeurs **DateTime** étaient arrondies pour correspondre à l’échelle des colonnes **DateTime** et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **smalldatetime** par. 
  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client (et versions ultérieures) applique maintenant les règles de validation plus strictes définies dans la spécification principale ODBC pour les fractions de seconde. Si une valeur de paramètre ne peut pas être convertie au type SQL à l'aide de l'échelle spécifiée ou déduite de la liaison de client sans troncation des chiffres de fin, une erreur est retournée.|  
|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut retourner des résultats différents lorsque le déclencheur s’exécute.|Des modifications apportées dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] ont pu amener une application à avoir des résultats différents retournés par une instruction, ce qui a entraîné l’exécution d’un déclencheur quand **NOCOUNT OFF** était actif. Dans ce cas, votre application peut générer une erreur. Pour résoudre cette erreur, définissez **NOCOUNT on** dans le déclencheur ou appelez SQLMoreResults pour passer au résultat suivant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
