---
title: "SQL Server, Cursor-Manager nach Typ-Objekt | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cursor-Manager nach Typ-Objekt"
  - "SQLServer:Cursor-Manager nach Typ"
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# SQL Server, Cursor-Manager nach Typ-Objekt
  Das **SQLServer:Cursor-Manager nach Typ** -Objekt stellt Leistungsindikatoren zum Überwachen von Cursorn bereit, die nach dem Typ gruppiert sind.  
  
 Diese Tabelle beschreibt die Leistungsindikatoren des **SQLServer:Cursor-Manager nach Typ** -Objekts von SQL Server.  
  
|Leistungsindikatoren des SQLServer:Cursor-Manager nach Typ-Objekts|Beschreibung|  
|-------------------------------------|-----------------|  
|**Aktive Cursor**|Anzahl der aktiven Cursor.|  
|**Cachetrefferquote**|Das Verhältnis zwischen Cachetreffern und -suchvorgängen.|  
|**Basis für Cachetrefferquote**|Nur zur internen Verwendung.| 
|**Anzahl der zwischengespeicherten Cursor**|Anzahl der Cursor eines bestimmten Typs im Cache.|  
|**Verwendungszähler für zwischengespeicherte Cursor/Sekunde**|Häufigkeit, mit der jeder Typ eines zwischengespeicherten Cursors verwendet wurde.|  
|**Cursorspeicherauslastung**|Größe des Speicherplatzes, der durch Cursor belegt wird (KB).|  
|**Cursoranforderungen/Sekunde**|Anzahl der SQL-Cursoranforderungen, die vom Server empfangen wurden.|  
|**Cursor-Arbeitstabellenverwendung**|Anzahl der Arbeitstabellen, die von Cursorn verwendet werden.|  
|**Anzahl der aktiven Cursorpläne.**|Anzahl der Cursorpläne.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Cursor-Manager-Instanz|Beschreibung|  
|-----------------------------|-----------------|  
|**_Total**|Informationen für alle Cursor.|  
|**API Cursor**|Nur die API-Cursor-Informationen.|  
|**TSQL Global Cursor**|Nur die globalen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Cursorinformationen.|  
|**TSQL Local Cursor**|Nur die lokalen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Cursorinformationen.|  
  
## Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  