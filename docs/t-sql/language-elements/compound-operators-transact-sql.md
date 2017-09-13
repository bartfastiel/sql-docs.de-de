---
title: Verbundoperatoren (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators
- compound operators, described
ms.assetid: 5072fe91-02d3-42a7-831f-756eff714a17
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2e5fde8cd4265359722f33400d834b0a301718ef
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="compound-operators-transact-sql"></a>Verbundoperatoren (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Verbundoperatoren führen einen Vorgang aus und legen einen ursprünglichen Wert auf das Ergebnis des Vorgangs fest. Angenommen, eine Variable @x gleich 35 ist, klicken Sie dann @x += 2 nimmt den ursprünglichen Wert des @x, Hinzufügen von 2 und legt @x auf diesen neuen Wert (37).  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] stellt die folgenden Verbundoperatoren bereit:  
  
|Operator|Link zu weiteren Informationen|Aktion|  
|--------------|------------------------------|------------|  
|+=|[+= &#40; Hinzufügen von EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/add-equals-transact-sql.md)|Addiert etwas zum ursprünglichen Wert und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|-=|[= &#40; Subtrahieren Sie gleich &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/subtract-equals-transact-sql.md)|Subtrahiert etwas vom ursprünglichen Wert und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|*=|[&#42; = &#40; Multiplizieren Sie gleich &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/multiply-equals-transact-sql.md)|Multipliziert mit einem Betrag und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|/=|[&#40; Teilen gleich &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)|Dividiert durch einen Betrag und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|%=|[Modulo ist gleich &#40; Transact-SQL &#41;](../../t-sql/language-elements/modulo-equals-transact-sql.md)|Dividiert durch einen Betrag und legt den ursprünglichen Wert auf den Modulo fest.|  
|&=|[& = &#40; Bitweises AND EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)|Führt eine bitweise AND-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|^=|[^ = &#40; Bitweises exklusives OR EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)|Führt eine bitweise exklusive OR-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
|&#124;=|[&#124; = &#40; Bitweises OR EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)|Führt eine bitweise OR-Operation aus und legt den ursprünglichen Wert auf das Ergebnis fest.|  
  
## <a name="syntax"></a>Syntax  
  
```  
  
expression operator expression  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ist ein beliebiger gültiger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines beliebigen Datentyps der Kategorie "numeric" eingibt.  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt einen Wert vom Datentyp des Arguments zurück, das in der Rangfolge höher steht. Weitere Informationen finden Sie unter [Rangfolge der Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen finden Sie in den Themen zu jedem Operator.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen sind Verbundoperationen dargestellt.  
  
```  
DECLARE @x1 int = 27;  
SET @x1 += 2 ;  
SELECT @x1 AS Added_2;  
  
DECLARE @x2 int = 27;  
SET @x2 -= 2 ;  
SELECT @x2 AS Subtracted_2;  
  
DECLARE @x3 int = 27;  
SET @x3 *= 2 ;  
SELECT @x3 AS Multiplied_by_2;  
  
DECLARE @x4 int = 27;  
SET @x4 /= 2 ;  
SELECT @x4 AS Divided_by_2;  
  
DECLARE @x5 int = 27;  
SET @x5 %= 2 ;  
SELECT @x5 AS Modulo_of_27_divided_by_2;  
  
DECLARE @x6 int = 9;  
SET @x6 &= 13 ;  
SELECT @x6 AS Bitwise_AND;  
  
DECLARE @x7 int = 27;  
SET @x7 ^= 2 ;  
SELECT @x7 AS Bitwise_Exclusive_OR;  
  
DECLARE @x8 int = 27;  
SET @x8 |= 2 ;  
SELECT @x8 AS Bitwise_OR;  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Operatoren &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Bitweise Operatoren &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  