---
title: Erweiterung für SQL Server-Import
titleSuffix: Azure Data Studio
description: Installieren und Verwenden der SQL Server-Import-Erweiterung (Vorschau) für Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: acca24570cf1c5052d92378b0dd5aa44d978aab6
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54131420"
---
# <a name="sql-server-import-extension-preview"></a>SQL Server-Import-Erweiterung (Vorschau)

Die Erweiterung für SQL Server-Import (Vorschau) konvertiert TXT- und CSV-Dateien in einer SQL-Tabelle. Dieser Assistent führt eine Microsoft Research-Frameworks, bekannt als [Program Synthesis using Beispiele (Text)](https://microsoft.github.io/prose/) , die Datei mit minimalen Benutzereingaben auf intelligente Weise zu analysieren. Es ist ein leistungsfähiges Framework für die Datenanalyse, und es ist die gleiche Technologie, die unterstützt Flash Fill in Microsoft Excel

Weitere Informationen zu den SSMS-Version dieser Funktion finden Sie [in diesem Artikel](https://docs.microsoft.com/sql/relational-databases/import-export/import-flat-file-wizard).


## <a name="install-the-sql-server-import-extension"></a>Installieren Sie die SQL Server-Import-Erweiterung

1. Um Erweiterungs-Manager öffnen und den Zugriff auf die verfügbaren Erweiterungen, wählen Sie das Symbol für Erweiterungen oder **Erweiterungen** in die **Ansicht** Menü.
2. Wählen Sie eine verfügbare Erweiterung, um seine Details anzuzeigen.

   ![Importieren von Erweiterungs-manager](media/sql-server-import-extension/import-wizard-install.png)

1. Wählen Sie die gewünschte Erweiterung und **installieren** es.
2. Wählen Sie **Reload** zum Aktivieren der Erweiterung (nur beim ersten eine Erweiterung der Installation erforderlich).

## <a name="start-import-wizard"></a>Tabellenimport-Assistenten starten

1. Um SQL Server-Import zu starten, stellen Sie zunächst eine Verbindung mit einem Server, auf die Registerkarte "Server".
2. Nachdem Sie eine Verbindung herstellen, einen Drilldown für die Zieldatenbank, die Sie eine Datei in eine SQL-Tabelle importieren möchten.
3. Mit der rechten Maustaste auf die Datenbank, und klicken Sie auf **Tabellenimport-Assistenten**.
    ![Öffnen der tabellenimport-Assistenten](media/sql-server-import-extension/open-import-wizard.png)

## <a name="importing-a-file"></a>Importieren einer Datei
1. Wenn Sie mit der rechten Maustaste auf um den Assistenten zu starten, sind Server und Datenbank bereits automatisch ausgefüllten. Wenn es andere aktiven Verbindungen, können Sie in der Dropdownliste auswählen. 
    
    Wählen Sie eine Datei, indem Sie auf **durchsuchen.** Sollte den Namen der Tabelle auf den Dateinamen basierend automatisch ausgefüllt, aber Sie können auch ändern, es selbst.

    Standardmäßig das Schema wird Dbo, aber Sie können ihn ändern. Klicken Sie auf **Weiter** , um den Vorgang fortzusetzen.
    ![Eingabedatei](media/sql-server-import-extension/import-wizard-input-file.png)
1. Der Assistent generiert eine Vorschau auf die ersten 50 Zeilen basiert. Es sind keine zusätzlichen Aktionen auf dieser Seite als überprüfen, dass die Daten korrekt aussieht. Klicken Sie auf **Weiter** , um den Vorgang fortzusetzen.
    ![Öffnen der tabellenimport-Assistenten](media/sql-server-import-extension/import-wizard-preview-data.png)
2. Auf dieser Seite können Sie Änderungen vornehmen, Spaltenname, Datentyp, ob es ein primärer Schlüssel ist oder NULL-zu ermöglichen Werte. Sie können beliebig viele Änderungen wie gewünscht festlegen. Klicken Sie auf **Importdaten** um den Vorgang fortzusetzen.
    ![Öffnen der tabellenimport-Assistenten](media/sql-server-import-extension/import-wizard-modify-columns.png)
3. Diese Seite bietet einen Überblick über die Aktionen, die ausgewählt werden. Sie können auch sehen, ob die Tabelle erfolgreich eingefügt. 

    Können Sie entweder auf **Fertig "," Previous** Wenn Sie Änderungen vornehmen müssen oder **neue Importdatei** um schnell eine andere Datei zu importieren.
    ![Öffnen der tabellenimport-Assistenten](media/sql-server-import-extension/import-wizard-summary.png)
1. Überprüfen Sie, ob die Tabelle erfolgreich importiert, durch Ihre Zieldatenbank zu aktualisieren oder durch Ausführen einer SELECT-Abfrage auf den Namen der Tabelle.

## <a name="next-steps"></a>Nächste Schritte
- Weitere Informationen zum Importassistenten finden unter den [Blogbeitrag](https://cloudblogs.microsoft.com/sqlserver/2018/08/30/the-august-release-of-sql-operations-studio-is-now-available/).
- Weitere Informationen zu PROSE finden unter den [Dokumentation.](https://microsoft.github.io/prose/)
