---
title: () (Klammern) (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e2ff4ecbfec3d3d52181a4860aac5a9f5073f275
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762042"
---
# <a name="-parentheses-ssis-expression"></a>() (Klammern) (SSIS-Ausdruck)
  Identifiziert die Auswertungsreihenfolge von Ausdrücken. Ausdrücke in Klammern haben die höchste Auswertungsrangfolge. Geschachtelte Ausdrücke, die in Klammern eingeschlossen sind, werden von innen nach außen ausgewertet.  
  
 Durch Klammern werden außerdem komplexe Ausdrücke verständlicher.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein gültiger Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Datentyp von *expression*. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 Dieses Beispiel zeigt, wie die Rangfolge von Operatoren durch die Verwendung von Klammern geändert wird. Der erste Ausdruck wird zu 100 ausgewertet, der zweite zu 31.  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
