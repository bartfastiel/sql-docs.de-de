---
title: Achse (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2802422f7d50c0a504a0c42eec940d81e89e66b8
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739629"
---
# <a name="axis-mdx"></a>Axis (MDX)


  Gibt die Menge der Tupel auf der angegebenen Achse zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>Argumente  
 *Axis_Number*  
 Ein gültiger numerischer Ausdruck, der eine Achsennummer angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Achse** Funktion verwendet die nullbasierte Position einer Achse, um die Menge der Tupel auf dieser Achse zurückzugeben. Beispielsweise gibt `Axis(0)` die COLUMNS-Achse zurück, `Axis(1)` die ROWS-Achse usw. Die **Achse** Funktion kann nicht für die Filterachse verwendet werden. Diese Funktion kann verwendet werden, damit berechnete Elemente den Kontext der aktuell ausgeführten Abfrage erkennen. Wenn Sie z. B. ein berechnetes Element benötigen, das die Summe nur der Elemente bereitstellt, die auf der ROWS-Achse ausgewählt werden. Sie kann auch verwendet werden, um eine Achse in Abhängigkeit von der Definition einer anderen Achse zu definieren. Z. B. um den Inhalt der ROWS-Achse entsprechend dem Wert des ersten Eintrags auf der COLUMNS-Achse anzuordnen.  
  
> [!NOTE]  
>  Eine Achse kann nur auf eine vorhergehende Achse verweisen. Beispielsweise muss `Axis(0)` nach der Auswertung der COLUMNS-Achse auftreten, z. B auf einer ROW- oder PAGE-Achse.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Beispielabfrage veranschaulicht die Verwendung der Axis-Funktion:  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SETTOSTR(AXIS(1))`  
  
 `SELECT MEASURES.AXISDEMO ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Im folgenden Beispiel wird die Verwendung der Axis-Funktion in einem berechneten Element veranschaulicht:  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SUM(AXIS(1), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.AXISDEMO} ON 0,`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
