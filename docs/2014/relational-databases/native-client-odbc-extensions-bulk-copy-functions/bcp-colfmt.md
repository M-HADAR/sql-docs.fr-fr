---
title: bcp_colfmt | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colfmt function
ms.assetid: 5c3b6299-80c7-4e84-8e69-4ff33009548e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c583ffad2267a82c39d4ab6c7cd71a1852c7cb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63065457"
---
# <a name="bcp_colfmt"></a>bcp_colfmt
  Spécifie le format source ou cible des données d'un fichier utilisateur. En cas d'utilisation comme format source, **bcp_colfmt** spécifie le format d'un fichier de données existant utilisé comme source de données dans une copie en bloc sur une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . En cas d'utilisation comme format cible, le fichier de données est créé à l'aide des formats de colonne spécifiés avec **bcp_colfmt**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_colfmt (  
HDBC   
hdbc  
,  
INT  
idxUserDataCol  
,  
BYTE   
eUserDataType  
,  
INT   
cbIndicator  
,  
DBINT   
cbUserData  
,  
LPCBYTE   
pUserDataTerm  
,  
INT   
cbUserDataTerm  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *idxUserDataCol*  
 Numéro de colonne ordinal dans le fichier des données utilisateur pour lequel le format est spécifié. La première colonne est 1.  
  
 *eUserDataType*  
 Type de données de la colonne dans le fichier utilisateur. Si le type de données est différent de celui de la colonne correspondante dans la table de base de données (*idxServerColumn*), la copie en bloc convertit si possible les données.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]a introduit la prise en charge des jetons de type de données SQLXML et SQLUDT dans le paramètre *eUserDataType* .  
  
 Le paramètre *eUserDataType* est énuméré par les jetons de type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans sqlncli.h, et non par les énumérateurs de type de données C ODBC. Par exemple, vous pouvez spécifier une chaîne de caractères, ODBC type SQL_C_CHAR, à l'aide du SQLCHARACTER de type propre à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour spécifier la représentation des données par défaut pour le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , attribuez la valeur 0 à ce paramètre.  
  
 Pour une copie en bloc à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un fichier, lorsque *eUserDataType* est de type SQLDECIMAL ou SQLNUMERIC :  
  
-   Si la colonne source n’est pas **décimale** ou **numérique**, la précision et l’échelle par défaut sont utilisées.  
  
-   Si la colonne source est **décimale** ou **numérique**, sa précision et son échelle propres sont utilisées.  
  
 *cbIndicator*  
 Longueur, en octets, d'une longueur/indicateur null au sein des données de la colonne. Les valeurs de longueur d'indicateur valides sont 0 (quand aucun indicateur n'est utilisé), 1, 2, 4 ou 8.  
  
 Pour spécifier l'utilisation d'un indicateur de copie en bloc par défaut, définissez ce paramètre sur SQL_VARLEN_DATA.  
  
 Les indicateurs apparaissent directement en mémoire avant les autres données et, dans le fichier de données, juste avant les données auxquelles ils s'appliquent.  
  
 Si plusieurs méthodes de spécification de la longueur de colonne d'un fichier de données sont utilisées (par exemple, un indicateur et une longueur de colonne maximale, ou un indicateur et une séquence de terminaison), la copie en bloc choisit celle qui implique la quantité de données à copier la moins élevée.  
  
 Les fichiers de données générés par la copie en bloc lorsqu'aucune intervention de l'utilisateur n'ajuste le format des données contiennent des indicateurs si la longueur des données de la colonne est variable ou si la colonne peut accepter la valeur NULL.  
  
 *cbUserData*  
 Longueur maximale, en octets, des données de cette colonne dans le fichier utilisateur, sans compter la longueur d'un indicateur de longueur ou d'un terminateur.  
  
 L'attribution de SQL_NULL_DATA à *cbUserData* indique que toutes les valeurs de la colonne du fichier de données sont ou doivent être NULL.  
  
 L'attribution de SQL_VARLEN_DATA à *cbUserData* indique que le système doit déterminer la longueur des données dans chaque colonne. Pour certaines colonnes, cela peut signifier qu'un indicateur de longueur/null est généré pour précéder les données dans une copie à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou que l'indicateur est attendu dans les données copiées vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character et binary, *cbUserData* peut avoir la valeur SQL_VARLEN_DATA, SQL_NULL_DATA, 0 ou une valeur positive quelconque. Si *cbUserData* a la valeur SQL_VARLEN_DATA, le système utilise l'indicateur de longueur, s'il est présent, ou une séquence de terminaison pour déterminer la longueur des données. Si un indicateur de longueur et une séquence de terminaison sont fournis, la copie en bloc utilise celui qui implique le volume de données à copier le plus faible. Si *cbUserData* a la valeur SQL_VARLEN_DATA, le type de données est un type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character ou binary, et si aucun indicateur de longueur ou séquence de terminaison n'est spécifié, le système retourne un message d'erreur.  
  
 Si *cbUserData* a la valeur 0 ou une valeur positive, le système utilise *cbUserData* comme longueur de données maximale. Toutefois, si un indicateur de longueur ou une séquence de terminaison est fournie en plus d'une valeur *cbUserData*positive, le système détermine la longueur de données en utilisant la méthode qui entraîne la plus petite quantité de données à copier.  
  
 La valeur *cbUserData* représente le nombre d'octets de données. Si des données caractères sont représentées par des caractères Unicode étendus, une valeur de paramètre *cbUserData* positive représente le nombre de caractères multiplié par la taille, en octets, de chaque caractère.  
  
 *pUserDataTerm*  
 Séquence de terminaison à utiliser pour cette colonne. Ce paramètre est utile surtout pour les types de données de caractères puisque tous les autres types sont de longueur fixe ou, dans le cas des données binaires, nécessitent un indicateur de longueur pour enregistrer avec précision le nombre d'octets présents.  
  
 Pour éviter de terminer des données extraites ou pour indiquer que les données dans un fichier utilisateur ne sont pas terminées, attribuez la valeur NULL à ce paramètre.  
  
 Si plusieurs méthodes sont employées pour définir la longueur des colonnes du fichier utilisateur (par exemple, un terminateur et un indicateur de longueur, ou un terminateur et une longueur de colonne maximale), la copie en bloc choisit celle qui implique le volume de données à copier le moins élevé.  
  
 L'interface de programmation d'applications (API) de la copie en bloc procède à la conversion des caractères Unicode vers MBCS en fonction des besoins. Prenez soin de définir comme il se doit la chaîne d'octets de terminaison et la longueur de cette même chaîne.  
  
 *cbUserDataTerm*  
 Longueur, en octets, de la séquence de marque de fin à utiliser pour la colonne. Si aucune marque de fin n'est présente ou désirée dans les données, attribuez 0 à cette valeur.  
  
 *idxServerCol*  
 Position ordinale de la colonne dans la table de base de données. Le premier numéro de colonne est 1. La position ordinale d'une colonne est indiquée par [SQLColumns](../native-client-odbc-api/sqlcolumns.md).  
  
 Si cette valeur est 0, la copie en bloc ignore la colonne dans le fichier de données.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 La fonction **bcp_colfmt** permet de spécifier le format du fichier utilisateur pour les copies en bloc. Pour la copie en bloc, un format se compose des éléments suivants :  
  
-   Mappage des colonnes du fichier utilisateur avec les colonnes de la base de données  
  
-   Type de données de chaque colonne du fichier utilisateur  
  
-   Longueur de l'indicateur facultatif pour chaque colonne  
  
-   Longueur maximale des données par colonne du fichier utilisateur  
  
-   Séquence d'octets de fin facultative pour chaque colonne  
  
-   Longueur de la séquence d'octets de fin facultative  
  
 Chaque appel à **bcp_colfmt** spécifie le format pour une colonne du fichier utilisateur. Par exemple, pour modifier les paramètres par défaut de trois colonnes d'un fichier de données utilisateur de cinq colonnes, appelez d'abord [bcp_columns](bcp-columns.md)**(5)**, puis **bcp_colfmt** cinq fois (trois de ces appels définissant votre format personnalisé). Pour les deux appels restants, définissez *eUserDataType* avec la valeur 0 et définissez respectivement *cbIndicator*, *cbUserData*et *cbUserDataTerm* avec les valeurs 0, SQL_VARLEN_DATA et 0. Cette procédure copie les cinq colonnes, trois avec votre format personnalisé et deux avec le format par défaut.  
  
 Pour *cbIndicator*, la valeur 8 pour indiquer un type valeur élevé est désormais valide. Si le préfixe est spécifié pour un champ dont la colonne correspondante est un nouveau type max, il ne peut avoir que la valeur 8. Pour plus d’informations, consultez [bcp_bind](bcp-bind.md).  
  
 La fonction **bcp_columns** doit être appelée avant tout appel de **bcp_colfmt**.  
  
 Vous devez appeler **bcp_colfmt** une fois pour chaque colonne du fichier utilisateur.  
  
 L’appel de **bcp_colfmt** plusieurs fois pour une colonne de fichier utilisateur génère une erreur.  
  
 Vous n'avez pas besoin de copier toutes les données d'un fichier utilisateur dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour ignorer une colonne, spécifiez le format des données de la colonne, en affectant la valeur 0 au paramètre *idxServerCol* . Pour ignorer une colonne, vous devez spécifier son type.  
  
 La fonction [bcp_writefmt](bcp-writefmt.md) peut être utilisée pour garantir la persistance du format spécifié.  
  
## <a name="bcp_colfmt-support-for-enhanced-date-and-time-features"></a>Prise en charge de bcp_colfmt pour les fonctionnalités Date et Heure améliorées  
 Pour plus d’informations sur les types utilisés avec le paramètre *eUserDataType* pour les types date/time, consultez [modifications de copie en bloc pour les types de date et d’heure améliorés &#40;OLE DB et ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
