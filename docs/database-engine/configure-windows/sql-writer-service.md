---
title: "SQL Writer-Dienst | Microsoft Docs"
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
  - "VDI [SQL Server]"
  - "Wiederherstellen [SQL Server], SQL Writer-Dienst"
  - "Sicherungen [SQL Server], während der Ausführung von SQL Server"
  - "Volumenschattenkopie-Dienst"
  - "Volumesicherungen während dem Ausführen [SQL Server]"
  - "VDI (Virtual Backup Device Interface) [SQL Server]"
  - "SQL Writer-Dienst"
  - "Dienste [SQL Server], SQL Writer"
  - "MSDE Writer"
  - "VSS"
ms.assetid: 0f299867-f499-4c2a-ad6f-b2ef1869381d
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# SQL Writer-Dienst
  Der SQL Writer-Dienst bietet zusätzliche Funktionalität zum Sichern und Wiederherstellen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über dass VSS-Framework (Volume Shadow Copy Service, Volumeschattenkopie-Dienst).  
  
 Der SQL Writer Service wird automatisch installiert. Er muss ausgeführt werden, wenn die Anwendung des Volumenschattenkopie-Diensts (VSS, Volume Shadow Copy Service) eine Sicherung oder Wiederherstellung anfordert. Verwenden Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services-Applet, um den Dienst zu konfigurieren. Der SQL Writer-Dienst kann auf allen Betriebssystemen installiert werden.  
  
## Zweck  
 Beim Ausführen errichtet [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Sperre und verfügt somit über den alleinigen Zugriff auf die Datendateien. Wenn der SQL Writer Service nicht ausgeführt wird, haben unter Windows ausgeführte Sicherungsprogramme keinen Zugriff auf die Datendateien, und die Sicherung muss mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung erfolgen.  
  
 Verwenden Sie den SQL Writer Service, um Windows-Sicherungsprogrammen das Kopieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datendateien zu ermöglichen, während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
## Volumenschattenkopie-Dienst  
 Die in VSS bereitgestellte Gruppe von COM APIs implementiert ein Framework, das die Sicherung von Volumes ermöglicht, während die auf dem System ausgeführten Anwendungen weiter Daten auf die betreffenden Datenträger schreiben. Der VSS stellt eine konsistente Oberfläche bereit, mit der die Benutzeranwendungen, die Daten auf dem Datenträger aktualisieren (Verfasser), und die Benutzeranwendungen zum Sichern der Anwendungen (Anforderer) koordiniert werden können.  
  
 Der VSS kopiert und zeichnet dauerhafte Bilder zur Sicherung der laufenden Systeme, insbesondere der Server, auf, ohne dass dadurch Leistung und Stabilität der bereitgestellten Dienste übermäßig beeinträchtigt werden. Weitere Informationen zum VSS finden Sie in der Windows-Dokumentation.  
  
## VDI (Virtual Backup Device Interface)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt ein API namens VDI (Virtual Backup Device Interface) bereit, mit dem unabhängige Softwarehersteller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in ihre Produkte integrieren können, um so Unterstützung für Sicherungs- und Wiederherstellungsvorgänge bereitzustellen. Diese APIs wurden mit dem Ziel der maximalen Zuverlässigkeit und Leistung entworfen und unterstützen das gesamte Spektrum der in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellten Sicherungs- und Wiederherstellungsfunktionen, einschließlich aller Funktionen von Hotbackups und Momentaufnahmesicherungen.  
  
## Berechtigungen  
 Der SQL Writer-Dienst muss unter dem Konto **Lokales System** ausgeführt werden. Der SQL Writer-Dienst verwendet die Anmeldung für **NT-Dienst\SQLWriter**, um eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen. Mithilfe der Anmeldung für **NT-Dienst\SQLWriter** kann der SQL Writer-Prozess mit einer niedrigeren Berechtigungsstufe unter einem Konto ausgeführt werden, das **nicht als Anmeldekonto** geführt wird. Auf diese Weise wird das Sicherheitsrisiko verringert. Wenn der SQL Writer-Dienst deaktiviert ist, werden Hilfsprogramme, die auf VSS-Momentaufnahmen basieren, z. B. System Center Data Protection Manager sowie einige andere Drittanbieterprodukte, funktionsunfähig. Im schlimmsten Fall besteht die Gefahr, dass Sicherungen von inkonsistenten Datenbanken erstellt werden. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], das System, auf dem die Software ausgeführt wird, und das Hostsystem (im Falle eines virtuellen Computers) keine anderen Komponenten als die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Sicherung erfordern, kann der SQL Writer-Dienst gefahrlos deaktiviert und die Anmeldung entfernt werden.  Beachten Sie, dass der SQL Writer-Dienst durch eine Sicherung auf Volume- oder Systemebene initiiert werden kann, unabhängig davon, ob die Sicherung direkt auf einer Momentaufnahme basiert oder nicht. Einige Systemsicherungsprodukte verwenden VSS, um Blockierungen durch geöffnete oder gesperrte Dateien zu verhindern. Der SQL Writer-Dienst erfordert erhöhte Berechtigungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], da im Verlauf der Dienstaktivitäten sämtliche E/A-Vorgänge für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kurzzeitig eingefroren werden.  
  
## Funktionen  
 SQL Writer unterstützt:  
  
-   Vollständige Sicherung und Wiederherstellung von Datenbanken, einschließlich der Volltextkataloge  
  
-   Differenzielle Sicherung und Wiederherstellung  
  
-   Wiederherstellung mit MOVE-Klausel  
  
-   Datenbankumbenennung  
  
-   Kopiesicherung  
  
-   Automatische Wiederherstellung einer Datenbankmomentaufnahme  
  
 SQL Writer unterstützt nicht:  
  
-   Protokollsicherungen  
  
-   Datei- und Dateigruppensicherung  
  
-   Seitenwiederherstellung  
  
  