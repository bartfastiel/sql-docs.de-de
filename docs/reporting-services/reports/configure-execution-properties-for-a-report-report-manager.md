---
title: "Konfigurieren von Ausf&#252;hrungseigenschaften f&#252;r einen Bericht (Berichts-Manager) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Berichtsausführungseigenschaften [Reporting Services]"
  - "Berichte [Reporting Services], Eigenschaften"
  - "Berichte [Reporting Services], Ausführungsoptionen"
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
caps.latest.revision: 41
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 41
---
# Konfigurieren von Ausf&#252;hrungseigenschaften f&#252;r einen Bericht (Berichts-Manager)
  Sie können Berichtsverarbeitungsoptionen festlegen, um anzugeben, wann Daten für einen Bericht abgerufen werden sollen. Es ist hilfreich, die Datenverarbeitung für einen Bericht zu planen, wenn die externe Datenquelle zu bestimmten Zeiten aktualisiert wird (beispielsweise bei einem Data Warehouse, das täglich oder wöchentlich aktualisiert wird) und Sie vermeiden wollen, dass bei jeder Berichtsanforderung dieselben Daten abgerufen werden. Das Planen der Datenverarbeitung ist außerdem hilfreich, wenn Sie die Verarbeitungslast für den externen Datenbankserver steuern möchten oder wenn Sie einheitliche Ergebnisse für verschiedene Benutzer bereitstellen möchten, die mit identischen Datensätzen arbeiten sollen. Bei flüchtigen Daten kann ein bedarfsgesteuerter Bericht von einer Minute zur nächsten unterschiedliche Ergebnisse liefern. Dagegen können Sie mit einer Berichtsmomentaufnahme gültige Vergleiche mit anderen Berichten oder Analysetools ausführen, die Daten desselben Zeitpunkts enthalten.  
  
 Eine Berichtsmomentaufnahme ist ein Bericht, der Layoutanweisungen und Abfrageergebnisse enthält, die zu einem bestimmten Zeitpunkt abgerufen wurden. Während für bedarfsgesteuerte Berichte aktuelle Abfrageergebnisse abgerufen werden, wenn Sie den Bericht auswählen, werden Berichtsmomentaufnahmen anhand eines Zeitplans verarbeitet und anschließend auf einem Berichtsserver gespeichert. Wenn Sie eine Berichtsmomentaufnahme zum Anzeigen auswählen, ruft der Berichtsserver den gespeicherten Bericht aus der Berichtsserver-Datenbank ab und zeigt die Daten und das Layout an, die zum Zeitpunkt der Momentaufnahmeerstellung für den Bericht aktuell waren.  
  
 Berichtsmomentaufnahmen werden in keinem speziellen Renderingformat gespeichert. Stattdessen werden Berichtsmomentaufnahmen erst dann in einem endgültigen Anzeigeformat (wie HTML) gerendert, wenn sie von einem Benutzer oder einer Anwendung angefordert werden. Durch das verzögerte Rendering wird eine Momentaufnahme portabel. Der Bericht kann jeweils im richtigen Format für das anfordernde Gerät oder den anfordernden Webbrowser gerendert werden.  
  
### So konfigurieren Sie Berichtsverarbeitungsoptionen  
  
1.  Starten Sie den [Berichts-Manager im einheitlichen SSRS-Modus](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  Navigieren Sie zu dem Bericht, für den Sie Berichtsverarbeitungsoptionen festlegen möchten, und öffnen Sie den Bericht.  
  
 Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
1.  Klicken Sie im Dropdownmenü auf **Verwalten**, und wählen Sie dann die Registerkarte **Verarbeitungsoptionen** aus.  
  
2.  Klicken Sie auf **Diesen Bericht aus einer Berichtsausführungs-Momentaufnahme rendern**, und wählen Sie dann eine der folgenden Optionen:  
  
    -   Falls Sie eine Momentaufnahme erstellen möchten, wählen Sie **Berichtsausführungs-Momentaufnahmen entsprechend diesem Zeitplan erstellen** aus, und definieren Sie anschließend einen berichtsspezifischen Zeitplan, oder wählen Sie aus der Liste **Freigegebener Zeitplan** einen Zeitplan aus.  
  
    -   Wenn Sie sofort eine Momentaufnahme erstellen möchten, wählen Sie **Erstellen Sie eine Momentaufnahme des Berichts, wenn Sie auf dieser Seite auf die Schaltfläche "Anwenden" klicken**aus.  
  
3.  Klicken Sie auf **Anwenden**.  
  
## Siehe auch  
 [Festlegen von Berichtsverarbeitungseigenschaften](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Öffnen und Schließen eines Berichts &#40;Berichts-Manager&#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)   
 [Inhalt &#40;Seite, Berichts-Manager&#41;](../Topic/Contents%20Page%20\(Report%20Manager\).md)   
 [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Verarbeitungsoptionen (Eigenschaftenseite) &#40;Berichts-Manager&#41;](../Topic/Processing%20Options%20Properties%20Page%20\(Report%20Manager\).md)  
  
  