---
title: "Der Datenverbindungspfad in der Arbeitsmappe verweist auf eine Datei auf dem lokalen Laufwerk oder entspricht einem ung&#252;ltigen URI. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Der Datenverbindungspfad in der Arbeitsmappe verweist auf eine Datei auf dem lokalen Laufwerk oder entspricht einem ung&#252;ltigen URI. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten
  Für Excel-Arbeitsmappen, die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Daten enthalten, gibt Excel Services diesen Fehler zurück, wenn keine Verbindung mit eingebetteten Datenquellen hergestellt werden kann.  
  
## Details  
  
|||  
|-|-|  
|Gilt für|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Excel Services werden dafür konfiguriert, nur Datenverbindungen von ODC-Dateien zuzulassen, die sich in einer vertrauenswürdigen Datenverbindungsbibliothek befinden.|  
|Meldungstext|Der Datenverbindungspfad in der Arbeitsmappe verweist auf eine Datei auf dem lokalen Laufwerk oder entspricht einem ungültigen URI. Die folgenden Verbindungen wurden nicht aktualisiert: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Daten|  
  
## Erklärung  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappen enthalten eingebettete Datenverbindungen. Um die Interaktion mit Arbeitsmappen über Slicer und Filter zu unterstützen, müssen Excel Services so konfiguriert sein, dass der externe Datenzugriff über eingebettete Verbindungsinformationen möglich ist. Externer Datenzugriff ist zum Abrufen von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Daten erforderlich, die auf [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Server in der Farm geladen wurden.  
  
## Benutzeraktion  
 Ändern Sie die Konfigurationseinstellungen, um eingebettete Datenquellenverbindungen zuzulassen.  
  
1.  Klicken Sie in der Zentraladministration unter Anwendungsverwaltung auf **Dienstanwendungen verwalten**.  
  
2.  Klicken Sie auf **Excel Services-Anwendung**.  
  
3.  Klicken Sie auf **Vertrauenswürdiger Dateispeicherort**.  
  
4.  Klicken Sie auf **http://** oder den Speicherort, den Sie konfigurieren möchten.  
  
5.  Klicken Sie unter Externe Daten in **Externe Daten zulassen**auf Vertrauenswürdige Datenverbindungsbibliotheken und eingebettete Verbindungen.  
  
6.  Klicken Sie auf **OK**.  
  
 Alternativ können Sie einen neuen vertrauenswürdigen Speicherort für Websites erstellen, die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappen enthalten, und dann die Konfigurationseinstellungen nur für diese Website ändern. Weitere Informationen finden Sie unter [Erstellen eines vertrauenswürdigen Speicherorts für PowerPivot-Websites in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  