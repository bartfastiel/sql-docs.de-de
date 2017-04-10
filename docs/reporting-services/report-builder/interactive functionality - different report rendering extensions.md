---
title: "Interaktive Funktionalit&#228;t f&#252;r verschiedene Berichtsrenderingerweiterungen (Berichts-Generator und SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "01/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0bd1c4c-e8b5-467f-b5a1-541f19c7e3e2
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Interaktive Funktionalit&#228;t f&#252;r verschiedene Berichtsrenderingerweiterungen (Berichts-Generator und SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet Funktionen für die Interaktion mit einem paginierten Bericht zur Laufzeit. Nicht alle Berichtsrenderingformate unterstützen die interaktiven Funktionen in vollem Umfang. In der folgenden Tabelle ist die Funktionsweise der einzelnen interaktiven Funktionen in bestimmten Formaten beschrieben.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Interaktive Funktionen in verschiedenen Ausgabeformaten  
 Paginierte Berichte, die im XML-, CSV- oder IMAGE-Format gerendert werden, unterstützen keine interaktiven Funktionen.  
  
 Im [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Webportal, in SharePoint-Webparts oder in einem Browser angezeigte Berichte werden in HTML gerendert. HTML und Windows Forms sind die einzigen Berichtsausgabeformate, die alle interaktiven Funktionen vollständig unterstützen. Alternative HTML-Formate (wie MHTML) unterstützen viele interaktive Funktionen. Falls Ausnahmen für MHTML bestehen, wird in der folgenden Tabelle darauf hingewiesen.  
  
### Dokumentstrukturen  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Die interaktive Dokumentstruktur stellt einen Navigationsbereich mit hierarchischen Links bereit, mit denen zu verschiedenen Abschnitten des Berichts navigiert werden kann.|  
|PDF|PDF rendert eine Dokumentstruktur in Form des Lesezeichen-Bereichs. Alle Elemente in der Dokumentstruktur werden in dem Bereich von oben nach unten aufgelistet. Dies schließt eine Hierarchie aus Links ein. Wenn ein Seitenbereich angegeben wird, sind nur die Lesezeichen, die gerendert werden, in der Hierarchie vorhanden.|  
|Excel|Excel rendert in der Arbeitsmappe eine Dokumentstruktur als erstes Arbeitsblatt. Dies schließt eine Hierarchie aus Links ein. Beim Klicken auf den Link in der Dokumentstruktur wird die entsprechende Zielzelle im jeweiligen Arbeitsblatt geöffnet.|  
|Wort|Word rendert die Dokumentstruktur als Inhaltsverzeichnisbezeichnungen.|  
|Andere (z. B., TIFF, XML und CSV)|Nicht verfügbar in MHTML, XML, CSV oder IMAGE.|  
  
### Drillthroughlinks zu anderen Berichten  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Benutzer klicken auf Datenwerte im Bericht, um verwandte Daten in einem anderen Bericht anzuzeigen.|  
|PDF|Drillthroughlinks sind in PDF nicht verfügbar. Für PDF-Berichte, die Links zu anderen Seiten enthalten, sollten Sie Links verwenden.|  
|Excel|Drillthroughlinks werden in Excel gerendert.<br /><br /> Der Link wird zu einem Link auf den Bericht, auf den der Drillthroughlink verweist. Beim Klicken auf den Link wird ein Bericht in einem Browserfenster geöffnet.|  
|Wort|Drillthroughlinks werden in Word gerendert.<br /><br /> Der Link wird zu einem Link auf den Bericht, auf den der Drillthroughlink verweist. Beim Klicken auf den Link wird ein Bericht in einem Browserfenster geöffnet.|  
|Andere|Nicht verfügbar in XML, CSV oder IMAGE.|  
  
### Elemente zum Ein-/Ausschalten in einem Bericht  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Benutzer klicken auf Symbole zum Erweitern und Reduzieren, um Abschnitte eines Berichts anzuzeigen.|  
|PDF|Der Berichtsserver exportiert den aktuellen Ansichtsstatus des Berichts in eine PDF-Datei. Interaktives Umschalten wird nicht unterstützt.|  
|Excel|Drilldownlinks und Elemente, die umgeschaltet werden können, werden in Excel als reduzierbare Konturen gerendert. Sie können Abschnitte des Berichts in Excel erweitern und reduzieren. Weitere Informationen zu Einschränkungen mit Excel finden Sie unter [Exportieren nach Microsoft Excel &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).|  
|Wort|Der Berichtsserver exportiert den aktuellen Ansichtsstatus des Berichts in eine PDF-Datei. Interaktives Umschalten wird nicht unterstützt.|  
|Andere|Nicht verfügbar in MHTML, XML oder CSV. Beim Exportieren in ein Bildformat exportiert der Berichtsserver den aktuellen Ansichtsstatus des Berichts in eine PDF-Datei. Interaktives Umschalten wird nicht unterstützt.|  
  
### Interaktives Sortieren  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|In tabellarischen Berichten klicken Benutzer auf Sortierpfeile in Spalten, um die Sortierung der Daten zu ändern.|  
|PDF|Nicht verfügbar in PDF.|  
|Excel|Nicht verfügbar in Excel.|  
|Wort|Nicht verfügbar in Word.|  
|Andere|Nicht verfügbar in MHTML, XML, CSV oder IMAGE.|  
  
### Links zu externen Webinhalten oder Bildern  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Benutzer klicken auf Links, um externe Webseiten in einem neuen Browserfenster zu öffnen.|  
|PDF|Links werden von der PDF-Renderingerweiterung gerendert. Wenn ein Benutzer auf einen Link klickt, werden die verknüpften Seiten im Browser geöffnet.|  
|Excel|Links werden in Excel gerendert.|  
|Wort|Links werden in Word gerendert.|  
|Andere|Links sind in MHTML, XML, CSV oder IMAGE nicht verfügbar.<br /><br /> In MHTML und IMAGE werden externe Bilder als statisches Bild gerendert.|  
  
### Lesezeichen oder Anker  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Benutzer klicken auf Links, um zu einem anderen Abschnitt desselben Berichts zu navigieren.|  
|PDF|Nicht verfügbar in PDF.|  
|Excel|Lesezeichen werden in Excel gerendert.<br /><br /> Das Lesezeichen wird zu einem Link, der auf den Namen des Berichtselements verweist.|  
|Wort|Lesezeichen werden in Word gerendert.<br /><br /> Das Lesezeichen wird zu einem Link, der auf das Lesezeichen des Berichtselements verweist. Es werden nur 40 Zeichen eines Lesezeichens oder Anchornamens beim Exportieren des Berichts konvertiert. Dies kann zu doppelten Lesezeichen oder Anchornamen führen. Leerzeichen werden in Unterstriche (_) konvertiert.|  
|Andere|Nicht verfügbar in XML, CSV oder IMAGE.|  
  
### Angeforderte Parameter, die zur Laufzeit abgerufen wurden  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Oben im Bericht wird ein Parametereingabebereich angezeigt. Dieser Bereich ist Teil des HTML-Viewers, mit dem Berichte in einem Browser angezeigt werden.|  
|PDF|Der Berichtsserver exportiert den Bericht nach PDF mithilfe der zurzeit gültigen Parameterwerte für den Bericht.|  
|Excel|Der Berichtsserver exportiert den Bericht nach Excel mithilfe der zurzeit gültigen Parameterwerte für den Bericht.|  
|Wort|Der Berichtsserver exportiert den Bericht nach Word mithilfe der zurzeit gültigen Parameterwerte für den Bericht.|  
|Andere|Der Berichtsserver exportiert den Bericht in andere Formate mithilfe der zurzeit gültigen Parameterwerte für den Bericht.|  
  
### Filter, die zur Laufzeit angewendet wurden  
  
|Exportoption|Supportinformationen|  
|-------------------|-------------------------|  
|Vorschau/Berichts-Viewer, HTML|Die gefilterten Daten werden dem Benutzer zur Laufzeit angezeigt.|  
|PDF|Der Berichtsserver exportiert den Bericht nach PDF mithilfe der gefilterten Daten im aktuellen Bericht.|  
|Excel|Der Berichtsserver exportiert den Bericht nach Excel mithilfe der gefilterten Daten im aktuellen Bericht.|  
|Wort|Der Berichtsserver exportiert den Bericht nach Word mithilfe der gefilterten Daten im aktuellen Bericht.|  
|Andere|Der Berichtsserver exportiert den Bericht in andere Formate mithilfe der gefilterten Daten im aktuellen Bericht.|  
  
## Siehe auch  
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [Interaktive Sortierung, Dokumentstrukturen und Links &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)   
 [Matrizen &#40;Berichts-Generator und SSRS&#41;](../Topic/Matrices%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  