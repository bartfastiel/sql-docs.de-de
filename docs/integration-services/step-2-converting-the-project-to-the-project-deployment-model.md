---
title: "Schritt 2: Converting the Project to the Project Deployment Model (Konvertieren des Projekts in das Projektbereitstellungsmodell) | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 80964293-f1f5-4da7-b1fb-00ab8c30c1c5
caps.latest.revision: 4
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Schritt 2: Converting the Project to the Project Deployment Model (Konvertieren des Projekts in das Projektbereitstellungsmodell)
In dieser Aufgabe verwenden Sie den Konvertierungs-Assistenten von Integration Services-Projekt, um das Projekt in das Projektbereitstellungsmodell zu konvertieren.  
  
### Konvertieren des Projekts in das Projektbereitstellungsmodell  
  
1.  Klicken Sie im Menü „Projekt“ auf „Paketbereitstellungsmodell konvertieren“.  
  
2.  Überprüfen Sie die Schritte der Konvertierungs-Assistent von Integration Services-Einführungsseite und klicken Sie auf Weiter.  
  
3.  Klicken Sie auf der Seite zur Paketauswahl in die Paketliste, deaktivieren Sie alle Kontrollkästchen außer Lektion 6.dtsx, und klicken Sie dann auf Weiter.  
  
4.  Klicken Sie auf der Projekteigenschaftenseite auf Weiter.  
  
5.  Klicken Sie auf der Seite Task 'Paket ausführen' aktualisieren auf Weiter.  
  
6.  Stellen Sie auf auf der Konfigurationsauswahlseite sicher, dass das Paket Lektion 6.dtsx in der Konfigurationsliste ausgewählt ist, und klicken Sie auf Weiter.  
  
7.  Stellen Sie auf der Seite zum Erstellen von Parametern sicher, dass das Paket Lektion 6.dtsx ausgewählt ist, und der Bereich in der Konfigurationseigenschaftsliste auf Paket festgelegt ist, und klicken Sie dann auf Weiter.  
  
8.  Stellen Sie auf der Seite zur Konfiguration der Parameter sicher, dass die Werte für den Namen und den Wert demselben Namen und Wert entsprechen, den Sie in der Lektion 5 für den Variablen- und Konfigurationswert angegeben haben, und klicken Sie dann auf Weiter.  
  
9. Beachten Sie auf der Überprüfungsseite im Zusammenfassungsbereich, dass der Assistent die Informationen aus der Konfigurationsdatei verwendet hat, um die zu konvertierenden Eigenschaften festzulegen.  
  
10. Klicken Sie auf Konvertieren.  
  
    Beim Abschluss der Konvertierung einer Nachricht wird eine Warnung angezeigt, das die Änderungen nicht gespeichert werden, bis das Projekt in Visual Studio gespeichert wird. Klicken Sie im Warnungsdialogfeld auf OK.  
  
11. Klicken Sie im Konvertierungs-Assistenten des Integration Services-Projekts auf Schließen.  
  
12. Klicken Sie in SQL Server Data Tools auf das Menü "Datei", klicken Sie auf "Speichern", um das konvertierte Paket zu speichern.  
  
13. Klicken Sie auf der Registerkarte "Parameter", und stellen Sie sicher, dass das Paket jetzt einen Parameter für VarFolderName enthält und der Wert denselben Pfad für den Ordner der neuen Beispieldaten aus der Lektion 5-Konfigurationsdatei angegeben ist.  
  
## Nächste Aufgabe in der Lektion  
[Schritt 3: Testen des Pakets aus Lektion 6](../integration-services/step-3-testing-the-lesson-6-package.md)  
  
  
  