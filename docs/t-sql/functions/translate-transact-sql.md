---
title: TRANSLATE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eadf8d4512e3dd5e119dd92e9e2039e0af9dc0ce
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "52617436"
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Gibt die Zeichenfolge zurück, die als erstes Argument bereitgestellt wurde, nachdem einige durch das zweite Argument angegebene Zeichen in einen Zielzeichensatz übersetzt wurden, der im dritten Argument angegeben wird.

## <a name="syntax"></a>Syntax   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>Argumente   

 *inputString*   
 Der [Zeichenfolgenausdruck](../../t-sql/language-elements/expressions-transact-sql.md), der gesucht werden soll. *inputString* kann ein beliebiger Zeichendatentyp sein (nvarchar, varchar, nchar, nchar, char).

 *characters*   
 Ist ein aus einer Zeichenfolge bestehender [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md), der zu ersetzende Zeichen enthält. Für *characters* sind beliebige Zeichendatentypen möglich.

*translations*   
 Ist ein aus einer Zeichenfolge bestehender [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md), der die ersetzten Zeichen enthält. *translations* muss denselben Datentyp und dieselbe Länge wie *characters* haben.

## <a name="return-types"></a>Rückgabetypen   
Gibt einen Zeichenausdruck des gleichen Datentyps wie `inputString` zurück, bei dem die Zeichen des zweiten Arguments durch die entsprechenden Zeichen des dritten Arguments ersetzt werden.

## <a name="remarks"></a>Hinweise   

`TRANSLATE` gibt einen Fehler zurück, wenn sich die Länge von *characters* und *translations* unterscheidet. `TRANSLATE` gibt NULL zurück, wenn eines der Argumente NULL ist.  

Das Verhalten der `TRANSLATE`-Funktion entspricht dem Verwenden mehrerer [REPLACE](../../t-sql/functions/replace-transact-sql.md)-Funktionen.

Bei `TRANSLATE` werden SC-Sortierungen immer beachtet.

## <a name="examples"></a>Beispiele   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Ersetzen von eckigen und geschweiften Klammern durch reguläre Klammern    
Die folgende Abfrage ersetzt eckige und geschweifte Klammern in der Eingabezeichenfolge durch Klammern:
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

#### <a name="equivalent-calls-to-replace"></a>Entsprechende Aufrufe an REPLACE

In der folgenden SELECT-Anweisung gibt es eine Gruppe von vier geschachtelten Aufrufen der REPLACE-Funktion. Diese Gruppe entspricht dem einen Aufruf der Funktion TRANSLATE in der vorangehenden SELECT-Anweisung:

```sql
SELECT
REPLACE
(
      REPLACE
      (
            REPLACE
            (
                  REPLACE
                  (
                        '2*[3+4]/{7-2}',
                        '[',
                        '('
                  ),
                  ']',
                  ')'
            ),
            '{',
            '('
      ),
      '}',
      ')'
);
```

###  <a name="b-convert-geojson-points-into-wkt"></a>B. Konvertieren von GeoJSON-Punkten in WKT    
GeoJSON ist ein Format für das Codieren von vielen verschiedenen geografischen Datenstrukturen. Mit der `TRANSLATE`-Funktion können Entwickler GeoJSON-Punkte einfach in das WKT-Format (und umgekehrt) konvertieren. Die folgende Abfrage ersetzt eckige und geschweifte Klammern in der Eingabe durch reguläre Klammern:   
```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|Punkt  |Koordinaten |  
---------|--------- |
(137,4; 72,3) |[137,4; 72,3] |


## <a name="see-also"></a>Weitere Informationen finden Sie unter
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [Zeichenfolgenfunktionen (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   

