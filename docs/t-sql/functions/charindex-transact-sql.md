---
title: CHARINDEX (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CHARINDEX
- CHARINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], pattern searching
- CHARINDEX function
- pattern searching [SQL Server]
- starting point of expression in character string
ms.assetid: 78c10341-8373-4b30-b404-3db20e1a3ac4
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bf82d7899558349bd28e73f19f648d2f66323bdd
ms.sourcegitcommit: b58d514879f182fac74d9819918188f1688889f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "50971011"
---
# <a name="charindex-transact-sql"></a>CHARINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

> [!div class="nextstepaction"]
> [Unterstützen Sie uns bei der Verbesserung der Dokumentation für SQL Server.](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

Mit dieser Funktion können Sie in einem Zeichenausdruck nach einem anderen Zeichenausdruck suchen. Bei erfolgreicher Suche wird die Startposition des gesuchten Ausdrucks zurückgegeben.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
CHARINDEX ( expressionToFind , expressionToSearch [ , start_location ] )   
```  
  
## <a name="arguments"></a>Argumente  
*expressionToFind*  
Ein Zeichenausdruck ([Expressions (Ausdrücke)](../../t-sql/language-elements/expressions-transact-sql.md)), der die zu suchende Sequenz enthält. Die maximale Zeichenlänge von *expressionToFind* beträgt 8000 Zeichen.
  
*expressionToSearch*  
Der zu suchende Zeichenausdruck.
  
*start_location*  
Ein **integer**- oder **bigint**-Ausdruck, bei dem die Suche beginnt. Wenn *start_location* nicht angegeben ist, einen negativen Wert oder den Wert 0 (null) besitzt, wird mit der Suche am Anfang von *expressionToSearch* begonnen.
  
## <a name="return-types"></a>Rückgabetypen
**bigint**, wenn *expressionToSearch* vom Datentyp **nvarchar(max)**, **varbinary(max)** oder **varchar(max)** ist; andernfalls **int**.
  
## <a name="remarks"></a>Remarks  
Wenn entweder der Ausdruck *expressionToFind* oder der Ausdruck *expressionToSearch* einen Unicode-Datentyp aufweist (**nchar** oder **nvarchar**), und der andere Ausdruck nicht, konvertiert die CHARINDEX-Funktion diesen anderen Ausdruck in einen Unicode-Datentyp. CHARINDEX kann nicht mit den Datentypen **image**, **ntext** oder **text** verwendet werden.
  
Wenn entweder der Ausdruck *expressionToFind* oder der Ausdruck *expressionToSearch* einen NULL-Wert aufweist, gibt auch CHARINDEX NULL zurück.
  
Wenn *expressionToFind* innerhalb von *expressionToSearch* von CHARINDEX nicht gefunden werden kann, gibt CHARINDEX 0 (null) zurück.
  
CHARINDEX führt Vergleiche basierend auf der Sortierung der Eingabe aus. Verwenden Sie zum Ausführen eines Vergleichs in einer angegebenen Sortierung COLLATE, um eine ausdrückliche Sortierung auf die Eingabe anzuwenden.
  
Die zurückgegebene Startposition ist 1-basiert, nicht 0-basiert.
  
0x0000 (**char(0)**) ist ein nicht definiertes Zeichen in Windows-Sortierungen und kann nicht in CHARINDEX enthalten sein.
  
## <a name="supplementary-characters-surrogate-pairs"></a>Ergänzende Zeichen (Ersatzpaare)  
Bei Verwendung von SC-Sortierungen werden Ersatzzeichenpaare sowohl von *start_location* als auch vom Rückgabewert als ein anstelle von zwei Zeichen gezählt. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-starting-position-of-an-expression"></a>A. Zurückgeben der Startposition eines Ausdrucks  
In diesem Beispiel wird in der Variablen des gesuchten Zeichenfolgenwerts `@document` nach `bicycle` gesucht.
  
```sql
DECLARE @document varchar(64);  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bicycle', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
48            
```  
  
### <a name="b-searching-from-a-specific-position"></a>B. Suchen ab einer bestimmten Position  
In diesem Beispiel wird der optionale *start_location*-Parameter verwendet, um die Suche nach `vital` beim fünften Zeichen der Variable des gesuchten Zeichenfolgenwerts `@document` zu beginnen.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('vital', @document, 5);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
16            
  
(1 row(s) affected)  
```  
  
### <a name="c-searching-for-a-nonexistent-expression"></a>C. Suchen nach einem nicht vorhandenen Ausdruck  
In diesem Beispiel wird das Resultset dargestellt, wenn *expressionToFind* von CHARINDEX nicht in *expressionToSearch* gefunden werden kann.
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bike', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
  
(1 row(s) affected)
```
  
### <a name="d-performing-a-case-sensitive-search"></a>D. Ausführen einer Suche unter Beachtung der Groß-/Kleinschreibung  
In diesem Beispiel wird eine Suche nach der Zeichenfolge `'TEST'` in der gesuchten Zeichenfolge `'This is a Test``'` dargestellt, wobei die Groß-/Kleinschreibung berücksichtigt wird.
  
```sql
USE tempdb;  
GO  
--perform a case sensitive search  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
```  
  
In diesem Beispiel wird eine Suche nach der Zeichenfolge `'Test'` in `'This is a Test'` dargestellt, wobei die Groß-/Kleinschreibung berücksichtigt wird.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'Test',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
11
```  
  
### <a name="e-performing-a-case-insensitive-search"></a>E. Ausführen einer Suche ohne Beachtung der Groß-/Kleinschreibung  
In diesem Beispiel wird eine Suche nach der Zeichenfolge `'TEST'` in `'This is a Test'` dargestellt, wobei die Groß-/Kleinschreibung nicht berücksichtigt wird.
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CI_AS);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
11
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="f-searching-from-the-start-of-a-string-expression"></a>F. Suche ab dem Beginn eines Zeichenfolgenausdrucks  
Dieses Beispiel gibt den ersten Speicherort der Zeichenfolge `is` in der Zeichenfolge `This is a string` ab Position 1 (also ab dem ersten Zeichen) von `This is a string` zurück.
  
```sql
SELECT CHARINDEX('is', 'This is a string');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
3
```  
  
### <a name="g-searching-from-a-position-other-than-the-first-position"></a>G. Suchen ab einer anderen Position als der ersten  
Dieses Beispiel gibt den ersten Speicherort der Zeichenfolge `is` in der Zeichenfolge `This is a string` ab Position 4 (also ab dem vierten Zeichen) zurück.
  
```sql
SELECT CHARINDEX('is', 'This is a string', 4);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
 6
 ```  
  
### <a name="h-results-when-the-string-is-not-found"></a>H. Ergebnisse, wenn die Zeichenfolge nicht gefunden wird  
Dieses Beispiel zeigt den Rückgabewert, wenn die Zeichenfolge *string_pattern* von CHARINDEX nicht in der gesuchten Zeichenfolge gefunden wird.
  
```sql
SELECT TOP(1) CHARINDEX('at', 'This is a string') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
0
```  
  
## <a name="see-also"></a>Siehe auch
 [LEN &#40;Transact-SQL&#41;](../../t-sql/functions/len-transact-sql.md)  
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)  
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen (Transact-SQL))](../../t-sql/functions/string-functions-transact-sql.md)  
 [+ &#40;Verketten von Zeichenfolgen&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  


