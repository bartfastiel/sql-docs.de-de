---
title: "&#196;ndern des Texts eines Legendenelements (Berichts-Generator und SSRS) | Microsoft Docs"
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
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# &#196;ndern des Texts eines Legendenelements (Berichts-Generator und SSRS)
  Wenn Sie ein Feld im Wertebereich des Diagramms ablegen, wird automatisch ein Legendenelement mit dem Namen dieses Felds erstellt. Alle Legendenelemente im Diagramm sind mit jeweils einer Reihe verknüpft, mit Ausnahme von Formdiagrammen, bei denen die Legende stattdessen mit einzelnen Datenpunkten verknüpft ist.  
  
 In Formdiagrammen können Sie den Text eines Legendenelements so ändern, dass weitere Informationen zu den einzelnen Datenpunkten angezeigt werden. Wenn beispielsweise die Werte der Datenpunkte in der Legende als Prozentsätze angezeigt werden sollen, können Sie ein Schlüsselwort wie **#PERCENT** angeben. Sie können .NET Framework-Formatcodes in Verbindung mit Schlüsselwörtern anfügen, um numerische Formate und Datumsformate anzuwenden. Weitere Informationen zu Schlüsselwörtern finden Sie unter [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
 ![Sharp-Diagramm](../../reporting-services/report-design/media/sharpchart.png "Sharp-Diagramm")  
  
 In Nicht-Formdiagrammen können Sie den Text eines Legendenelements ändern. Wenn eine Reihe beispielsweise den Namen "Reihe1" aufweist, können Sie diesen in einen aussagekräftigeren Namen wie "Umsatz für 2008" ändern.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### So ändern Sie den Text, der in der Legende eines Formdiagramms angezeigt wird  
  
1.  Klicken Sie mit der rechten Maustaste auf eine Reihe, oder klicken Sie mit der rechten Maustaste auf ein Feld im Bereich **Werte**, und wählen Sie die Option **Reiheneigenschaften** aus.  
  
2.  Klicken Sie auf **Legende** , und geben Sie im Feld **Benutzerdefinierter Legendentext** ein Schlüsselwort ein.  
  
 In der folgenden Tabelle sind Beispiele für diagrammspezifische Schlüsselwörter aufgelistet, die für die Eigenschaft **Benutzerdefinierter Legendentext** verwendet werden sollen. Weitere Informationen zu Schlüsselwörtern finden Sie unter [Formatieren von Datenpunkten in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
|Schlüsselwort|Description|Beispiel für den in der Legende angezeigten Text|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|Zeigt den Prozentsatz des Gesamtwerts mit einer Dezimalstelle an.|85.0%|  
|`#VALY`|Zeigt den tatsächlichen numerischen Wert des Datenfelds an.|17000|  
|`#VALY{C2}`|Zeigt den tatsächlichen numerischen Wert des Datenfelds als Währung mit zwei Dezimalstellen an.|$17000.00|  
|`#AXISLABEL (#PERCENT{P0})`|Zeigt die Textdarstellung des Kategoriefelds an, gefolgt von dem Prozentsatz, der in den einzelnen Kategorien im Diagramm angezeigt wird.|Michael Blythe (85 %)|  
  
> [!NOTE]  
>  Das Schlüsselwort #AXISLABEL kann nur dann zur Laufzeit ausgewertet werden, wenn im Bereich **Reihengruppen** kein Feld angegeben ist.  
  
### So ändern Sie den Text, der in der Legende eines Nicht-Formdiagramms angezeigt wird  
  
1.  Klicken Sie mit der rechten Maustaste auf eine Reihe, oder klicken Sie mit der rechten Maustaste auf ein Feld im Bereich **Werte**, und wählen Sie die Option **Reiheneigenschaften** aus.  
  
2.  Klicken Sie auf **Legende** , und geben Sie im Feld **Benutzerdefinierter Legendentext** eine Legendenbezeichnung ein. Die Reihe wird mit dem Text aktualisiert.  
  
## Siehe auch  
 [Formatieren der Legende in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-the-legend-on-a-chart-report-builder-and-ssrs.md)   
 [Formatieren von Reihenfarben in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Ausblenden von Legendenelementen im Diagramm &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/hide-legend-items-on-the-chart-report-builder-and-ssrs.md)  
  
  