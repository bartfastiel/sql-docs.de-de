---
title: "Zugreifen auf FileTables mit Transact-SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FileTables [SQL Server], Zugreifen auf Dateien mit T-SQL"
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Zugreifen auf FileTables mit Transact-SQL
  Beschreibt, wie die Befehle der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Datenbearbeitungssprache (Data Manipulation Language, DML) mit FileTables funktionieren.  
  
##  <a name="BasicsInsert"></a> INSERT-Vorgänge in FileTables  
 Die folgenden Überlegungen gelten für **INSERT** -Vorgänge in FileTables:  
  
-   Alle Dateiattributspalten besitzen NOT NULL-Einschränkungen. Wenn Werte nicht explizit festgelegt werden, werden entsprechende Standardwerte angegeben.  
  
-   Systemdefinierte Einschränkungen werden erzwungen, wenn die INSERT-Anweisung **name**, **path_locator**, **parent_path_locator** oder Dateiattribute festlegt.  
  
-   Die Anwendung kann **path_locator** für eine Datei oder ein Verzeichnis abrufen, indem in der Funktion [GetPathLocator &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getpathlocator-transact-sql.md) der Dateisystempfad angegeben wird.  
  
##  <a name="BasicsUpdate"></a> UPDATE-Vorgänge in FileTables  
 Die folgenden Überlegungen gelten für **UPDATE** -Vorgänge in FileTables:  
  
-   Aktualisierungen an benutzerdefinierten Daten sind zulässig.  
  
-   Systemdefinierte Einschränkungen werden erzwungen, wenn die INSERT-Anweisung **name**, **path_locator**, **parent_path_locator** oder Dateiattribute festlegt.  
  
-   Aktualisierungen können an den FILESTREAM-Daten in der Spalte **file_stream** ohne Auswirkungen auf die anderen Spalten, einschließlich Timestamps, vorgenommen werden.  
  
##  <a name="BasicsDelete"></a> DELETE-Vorgänge in FileTables  
 Die folgenden Überlegungen gelten für **DELETE** -Vorgänge in FileTables:  
  
-   Durch Löschen einer Zeile wird auch die entsprechende Datei oder das entsprechende Verzeichnis aus dem Dateisystem entfernt.  
  
-   Das Löschen einer Zeile schlägt fehl, wenn die Zeile einem Verzeichnis entspricht, das andere Dateien oder Verzeichnisse enthält.  
  
##  <a name="BasicsConstraints"></a> Einschränkungen, die für DML-Vorgänge in FileTables erzwungen werden  
 Systemdefinierte Einschränkungen stellen sicher, dass DML-Aktionen nicht die Integrität der Dateinamespacehierarchie beeinträchtigen. Zu den Einschränkungen, die erzwungen werden, gehören Folgende:  
  
-   Wenn Sie **name** der Datei oder des Verzeichnisses festgelegt oder geändert haben:  
  
    -   Die Windows-Benennungskonventionen für Dateien und Verzeichnisse werden erzwungen.  
  
    -   Die Eindeutigkeit des Namens im übergeordneten Verzeichnis wird erzwungen.  
  
-   Wenn Sie den Speicherort einer Datei oder eines Verzeichnisses durch Festlegen oder Ändern von **path_locator** oder **parent_path_locator** festgelegt oder geändert haben:  
  
    -   Eindeutigkeit wird erzwungen.  
  
    -   Die Konsistenz der hierarchischen Struktur von Verzeichnissen und Dateien wird erzwungen, einschließlich der Konsistenz der Werte **path_locator** und **parent_path_locator**.  
  
-   Der Wert für **is_directory** kann nicht auf TRUE festgelegt werden, wenn die **file_stream**-Spalte nicht NULL ist. Daten in der **file_stream**-Spalte geben an, dass die Zeile eine Datei und nicht ein Verzeichnis darstellt.  
  
-   Spalten mit Dateiattributen können nicht NULL sein. NOT NULL-Einschränkungen werden mit Standardwerten erzwungen.  
  
-   Der Wert **last_access_time** kann nicht vor **last_write_time** und **creation_time** liegen.  
  
## Siehe auch  
 [Laden von Dateien in FileTables](../../relational-databases/blob/load-files-into-filetables.md)   
 [Arbeiten mit Verzeichnissen und Pfaden in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)   
 [Zugreifen auf FileTables mit Datei-E/A-APIs](../../relational-databases/blob/access-filetables-with-file-input-output-apis.md)   
 [FileTable-DDL, Funktionen, gespeicherte Prozeduren und Sichten](../../relational-databases/blob/filetable-ddl-functions-stored-procedures-and-views.md)  
  
  