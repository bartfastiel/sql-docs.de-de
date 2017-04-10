---
title: "&#196;ndern von Measures | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# &#196;ndern von Measures
Sie können die **FormatString**-Eigenschaft verwenden, um Formatierungseinstellungen zu definieren, die die Darstellung von Measures steuern. In dieser Aufgabe geben Sie Formatierungseigenschaften für die Währungs- und Prozentsatzmeasures im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube an.  
  
### So ändern Sie die Measures des Cubes  
  
1.  Wechseln Sie zur Registerkarte **Cubestruktur** des Cube-Designers für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube, erweitern Sie die **Internet Sales**-Measuregruppe im Bereich **Measures**, klicken Sie mit der rechten Maustaste auf **Order Quantity**, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Eigenschaftenfenster auf das Pushpin-Symbol **Automatisch im Hintergrund**, um das Eigenschaftenfenster offen zu halten.  
  
    Das Ändern von Eigenschaften für eine Reihe von Elementen ist einfacher, wenn das Eigenschaftenfenster geöffnet bleibt.  
  
3.  Klicken Sie im Eigenschaftenfenster auf die Liste **FormatString**, und geben Sie anschließend **#,#** ein.  
  
4.  Klicken Sie auf der Symbolleiste der Registerkarte **Cubestruktur** auf der linken Seite auf das Symbol **Measuresraster anzeigen**.  
  
    In der Rasteransicht können Sie mehrere Measures gleichzeitig auswählen.  
  
5.  Wählen Sie eine der folgenden Measures aus. Um mehrere Measures auszuwählen, halten Sie beim Klicken die STRG-TASTE gedrückt:  
  
    -   **Unit Price**  
  
    -   **Extended Amount**  
  
    -   **Discount Amount**  
  
    -   **Product Standard Cost**  
  
    -   **Total Product Cost**  
  
    -   **Sales Amount**  
  
    -   **Tax Amt**  
  
    -   **Freight**  
  
6.  Wählen Sie im Eigenschaftenfenster in der **FormatString**-Liste **Currency** aus.  
  
7.  Wählen Sie im Dropdown-Listenfeld oben im Eigenschaftenfenster (rechts unterhalb der Titelleiste) das Measure **Unit Price Discount Pct** und anschließend in der Liste **FormatString** die Option **Percent** aus.  
  
8.  Ändern Sie im Eigenschaftenfenster die **Name**-Eigenschaft für das **Unit Price Discount Pct**-Measure zu **Unit Price Discount Percentage**.  
  
9. Klicken Sie im Bereich **Measures** auf **Tax Amt**, und ändern Sie den Namen dieses Measures in **Tax Amount**.  
  
10. Klicken Sie im Eigenschaftenfenster auf das Symbol **Automatisch im Hintergrund**, um das Eigenschaftenfenster auszublenden, und anschließend auf der Symbolleiste der Registerkarte **Cubestruktur** auf **Measuresstruktur anzeigen**.  
  
11. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## Nächste Aufgabe in der Lektion  
[Ändern der Customer-Dimension](../analysis-services/modifying-the-customer-dimension.md)  
  
## Siehe auch  
[Definieren von Datenbankdimensionen](../analysis-services/multidimensional-models/define-database-dimensions.md)  
[Konfigurieren von Measureeigenschaften](../analysis-services/multidimensional-models/configure-measure-properties.md)  
  
  
  