---
title: UNICODE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- UNICODE
- UNICODE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- first character of input expression [SQL Server]
- UNICODE function
- Unicode [SQL Server], UNICODE function
ms.assetid: 5e3c40b2-8401-4741-9f2a-bae70eaa4da6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 29a9476f5835df326aa34d8ccfc4cc6d22ea7e3f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68670617"
---
# <a name="unicode-transact-sql"></a>UNICODE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie la valeur entière, telle qu'elle est définie par la norme Unicode, du premier caractère de l'expression entrée.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
UNICODE ( 'ncharacter_expression' )  
```  
  
## <a name="arguments"></a>Arguments  
**'** *ncharacter_expression* **'**  
Expression **nchar** ou **nvarchar**.  
  
## <a name="return-types"></a>Types de retour  
**int**  
  
## <a name="remarks"></a>Notes  
Dans les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], la fonction UNICODE retourne un codepoint UCS-2 dans la plage de 000000 à 00FFFF qui est capable de représenter les 65 535 caractères dans le plan multilingue de base (BMP) Unicode. À partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], lors de l'utilisation de classements prenant en charge des [Caractères supplémentaires (SC)](../../relational-databases/collations/collation-and-unicode-support.md#Supplementary_Characters), UNICODE retourne un codepoint UTF-16 compris entre 000000 et 10FFFF. Pour plus d’informations sur le support Unicode dans le [!INCLUDE[ssde_md](../../includes/ssde_md.md)], consultez [Classement et support Unicode](../../relational-databases/collations/collation-and-unicode-support.md#Unicode_Defn). 
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-unicode-and-the-nchar-function"></a>R. Utilisation d'UNICODE et de la fonction NCHAR  
 Cet exemple fait appel aux fonctions `UNICODE` et `NCHAR` pour imprimer la valeur UNICODE du premier caractère de la chaîne `Åkergatan` de 24 caractères et pour imprimer correctement le premier caractère, soit `Å`.  
  
```sql  
DECLARE @nstring nchar(12);  
SET @nstring = N'Åkergatan 24';  
SELECT UNICODE(@nstring), NCHAR(UNICODE(@nstring));  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------- -   
197         Å  
```  
  
### <a name="b-using-substring-unicode-and-convert"></a>B. Utilisation de SUBSTRING, UNICODE et CONVERT  
 Cet exemple fait appel aux fonctions `SUBSTRING`, `UNICODE` et `CONVERT` pour imprimer le nombre de caractères, le caractère Unicode et la valeur UNICODE de chacun des caractères de la chaîne `Åkergatan 24`.  
  
```sql  
-- The @position variable holds the position of the character currently  
-- being processed. The @nstring variable is the Unicode character   
-- string to process.  
DECLARE @position int, @nstring nchar(12);  
-- Initialize the current position variable to the first character in   
-- the string.  
SET @position = 1;  
-- Initialize the character string variable to the string to process.   
-- Notice that there is an N before the start of the string, which   
-- indicates that the data following the N is Unicode data.  
SET @nstring = N'Åkergatan 24';  
-- Print the character number of the position of the string you are at,   
-- the actual Unicode character you are processing, and the UNICODE   
-- value for this particular character.  
PRINT 'Character #' + ' ' + 'Unicode Character' + ' ' + 'UNICODE Value';  
WHILE @position <= LEN(@nstring)  
-- While these are still characters in the character string,  
   BEGIN;  
   SELECT @position,   
      CONVERT(char(17), SUBSTRING(@nstring, @position, 1)),  
      UNICODE(SUBSTRING(@nstring, @position, 1));  
   SELECT @position = @position + 1;  
   END;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Character # Unicode Character UNICODE Value  
  
----------- ----------------- -----------   
1           Å                 197           
  
----------- ----------------- -----------   
2           k                 107           
  
----------- ----------------- -----------   
3           e                 101           
  
----------- ----------------- -----------   
4           r                 114           
  
----------- ----------------- -----------   
5           g                 103           
  
----------- ----------------- -----------   
6           a                 97            
  
----------- ----------------- -----------   
7           t                 116           
  
----------- ----------------- -----------   
8           a                 97            
  
----------- ----------------- -----------   
9           n                 110           
  
----------- ----------------- -----------   
10                            32            
  
----------- ----------------- -----------   
11          2                 50            
  
----------- ----------------- -----------   
12          4                 52  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ASCII &#40;Transact-SQL&#41;](../../t-sql/functions/ascii-transact-sql.md)  
 [CHAR &#40;Transact-SQL&#41;](../../t-sql/functions/char-transact-sql.md)  
 [NCHAR &#40;Transact-SQL&#41;](../../t-sql/functions/nchar-transact-sql.md)   
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  

