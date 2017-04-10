---
title: "RunningValue-Funktion (Berichts-Generator und SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# RunningValue-Funktion (Berichts-Generator und SSRS)
  Gibt ein laufendes Aggregat aller numerischen Werte ungleich NULL aus dem angegebenen Ausdruck für den Kontext des angegebenen Bereichs ausgewertet zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Syntax  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### Parameter  
 *expression*  
 Der Ausdruck, für den die Aggregation auszuführen ist, z.B. `[Quantity]`.  
  
 *Funktion*  
 (**Enum**) Der Name der Aggregatfunktion, die auf den Ausdruck angewendet werden soll. Beispiel: **Sum**. Diese Funktion kann nicht **RunningValue**, **RowNumber**oder **Aggregate**sein.  
  
 *Bereich*  
 (**String**) Eine Zeichenfolgenkonstante als Name eines Datasets, eines Datenbereichs oder einer Gruppe oder NULL (**Nothing** in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), der den Kontext angibt, in dem die Aggregation ausgewertet wird. Durch**Nothing** wird der äußerste Kontext angegeben, normalerweise das Berichtsdataset.  
  
## Rückgabetyp  
 Wird durch die im *function* -Parameter angegebene Aggregatfunktion bestimmt.  
  
## Hinweise  
 Der Wert für **RunningValue** wird für jede neue Instanz des Bereichs auf 0 zurückgesetzt. Wenn eine Gruppe angegeben wird, wird der laufende Wert zurückgesetzt, wenn sich der Gruppenausdruck ändert. Wenn ein Datenbereich angegeben wird, wird der laufende Wert für jede neue Instanz des Datenbereichs zurückgesetzt. Wenn ein Dataset angegeben wird, wird der laufende Wert für das gesamte Dataset nicht zurückgesetzt.  
  
 **RunningValue** darf nicht in einem Filter- oder Sortierausdruck verwendet werden.  
  
 Der Datensatz, für den der ausgeführte Wert berechnet wird, muss den gleichen Datentyp aufweisen. Um Daten mit mehreren numerischen Datentypen in den gleichen Datentyp zu konvertieren, verwenden Sie Konvertierungsfunktionen wie **CInt**, **CDbl** oder **CDec**. Weitere Informationen finden Sie unter [Funktionen für die Typkonvertierung](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 *Scope* darf kein Ausdruck sein.  
  
 Das*Expression* -Objekt kann Aufrufe von geschachtelten Aggregatfunktionen enthalten. Dabei gelten folgende Ausnahmen und Bedingungen:  
  
-   Der Bereich für geschachtelte Aggregate muss dem Bereich des äußeren Aggregats entsprechen oder darin enthalten sein. In allen eindeutigen Bereichen des Ausdrucks muss ein Bereich eine untergeordnete Beziehung zu allen anderen Bereichen haben.  
  
-   Der Bereich für geschachtelte Aggregate darf nicht der Name eines Datasets sein.  
  
-   Das*Expression* -Objekt darf die Funktionen **First**, **Last**, **Previous**oder **RunningValue** nicht enthalten.  
  
-   Das*Expression* -Objekt darf keine geschachtelten Aggregate enthalten, die ein *recursive*-Objekt angeben.  
  
 Verwenden Sie **RowNumber**zur Berechnung des laufenden Werts für die Zeilenanzahl. Weitere Informationen finden Sie unter [RowNumber-Funktion &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/rownumber-function-report-builder-and-ssrs.md).  
  
 Weitere Informationen finden Sie unter [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md) und [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md).  
  
 Weitere Informationen zu rekursiven Aggregaten finden Sie unter [Erstellen von rekursiven Hierarchiegruppen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## Beispiele  
 Das folgende Codebeispiel generiert eine laufende Summe für das Feld mit dem Namen `Cost` im äußersten Bereich, den das Dataset darstellt.  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 Das folgende Codebeispiel generiert eine laufende Summe für das Feld mit dem Namen `Score` im Dataset mit dem Namen `DataSet1`.  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 Das folgende Codebeispiel generiert eine laufende Summe für das Feld mit dem Namen `Traffic Charges` im äußersten Bereich.  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## Siehe auch  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  