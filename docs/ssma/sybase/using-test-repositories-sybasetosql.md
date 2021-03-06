---
title: Using Test Repositories (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Repositories
ms.assetid: c359c25c-db2a-4a20-afa9-62d87a62df72
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 939342a85ed657faa645c593018cbf39042031c2
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52505228"
---
# <a name="using-test-repositories-sybasetosql"></a>Verwenden von Testrepositorys (SybaseToSQL)
Der SSMA-testen-Repository speichert SSMA Tester Testfälle und die Testergebnisse für die spätere Verwendung. Die Repository-Daten in SQL Server-Tabellen gespeichert sind **TestCaseRepository** und **RunTestCaseResultRepository** im Schema **Ssma_sybase_utilities** von **Ssmatesterdb_syb** Datenbank.  
  
Die folgenden Schaltflächen sind auf das Repository der Testfälle Dialogfeld verfügbar:  
  
-   Klicken Sie auf die **aktualisieren** Schaltfläche, um die Liste von Testfällen oder Testergebnisse zu aktualisieren.  
  
-   Klicken Sie auf die **schließen** Schaltfläche, um das Repository von Test Cases-Dialogfeld zu schließen.  
  
## <a name="test-cases-repository"></a>Testfälle-Repository  
Sie können das Repository von Testfällen anzeigen, indem Sie auf **Testfälle...**  aus der **Tester** Menü. SSMA zeigt dann die **Repository Testfälle** Dialogfenster mit einer Liste von gespeicherten Testfälle auf die **Testfälle** Seite.  
  
Das Raster zeigt die folgende Informationen zu jedem Testfall muss:  
  
-   Name: Der Name des Testfalls.  
  
-   Erstellt: Das Erstellungsdatum des Testfalls.  
  
-   Geändert: Das Datum der letzten Änderung des Testfalls.  
  
-   Beschreibung: Die Testfall-Beschreibungen.  
  
Die folgenden Schaltflächen sind auf der Seite "Testfälle" verfügbar:  
  
-   Klicken Sie auf die **hinzufügen** Schaltfläche, um den Testfall-Assistenten ausführen, und erstellen einen neuen Test.  
  
-   Klicken Sie auf die **entfernen** Schaltfläche, um den ausgewählten Test aus dem Repository zu löschen. Wenn ein Testfall gelöscht wird, werden alle zugehörigen Testergebnisse ebenfalls gelöscht.  
  
-   Klicken Sie auf die **bearbeiten** Schaltfläche, um den Testfall-Assistenten ausführen und ändern den ausgewählten Test.  
  
-   Klicken Sie auf die **ausführen** die Schaltfläche, um die [Ausführen von Testfällen &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) Dialogfeld, und führen Sie den ausgewählten Test.  
  
## <a name="test-results-repository"></a>Ergebnisrepository  
Sehen Sie auf das Ergebnisrepository der **Testergebnisse** auf der Seite die **Repository Testfälle** Fenster. Öffnen Sie sie durch Klicken auf **Testergebnisse...**  aus der **Tester** Menü.  
  
Sie können zwei Filter auf **Testergebnisse** Seite:  
  
-   Der Name des Testfalls-Filter: Ermöglicht die Auswahl der Testergebnisse anhand des Namens des Testfalls. Dieser Filter die **alle Testfall** Wert ermöglicht das Anzeigen von Testergebnissen für alle Testfälle.  
  
-   Der Testfall Ausführungsdatum-Filter: Filter-Testergebnisse nach dem Datum speichern. Dieser Filter die **alle Zeitraum** Wert ermöglicht das Anzeigen von Testergebnissen für jedes Datum speichern.  
  
Die folgende Informationen zu Testergebnissen wird im Raster angezeigt.  
  
-   Name: Name des Testfalls.  
  
-   Gestartet: Datum der Testfall wird ausgeführt.  
  
-   Ergebnis: Eine kurze Zusammenfassung der Ausführung des Tests (diese Zelle die QuickInfo zeigt eine vollständige Zusammenfassung der Ausführung des Tests).  
  
Die folgenden Schaltflächen sind auf der Seite "Testergebnis" verfügbar:  
  
-   Klicken Sie auf die **Ansicht** die Schaltfläche, um [Viewing Test Case Reports &#40;SybaseToSQL&#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md) des aktuellen Ergebnis des Testfalls.  
  
-   Klicken Sie auf die **löschen** Schaltfläche, um das ausgewählte Testergebnis löschen  
  
## <a name="see-also"></a>Siehe auch  
[Ausführen von Testfällen &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Testen von migrierten Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
